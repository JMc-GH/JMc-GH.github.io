---
title: "OneDrive, Unraid and the 3-2-1 Rule"
date: 2022-08-10
categories: 
    - Tech
tags:
    - Linux
    - OneDrive
    - Unraid
    - bash
    - Virtualisation
draft: false
---
With the prospect of a university course on the horizon I thought I better have another look at cloud storage, as I'm likely to be generating stuff that I can't afford to lose as a result of a hardware failure. I have fault-tolerance provided by Unraid for all my data, but this server is a single point of failure - if it pops all the data is gone. This would have to be a fairly catastrophic event - as each individual drive is redundant, but I feel I should pay at least some attention to the [3-2-1 rule](https://www.acronis.com/en-us/blog/posts/backup-rule/).

I store about 8Tb of data on the 12Tb capacity Unraid server. A fair bit of this I store for convenience, rainbow tables, leaked data, media files so the fault-tolerance provided by Unraid is fine for all of this. In all of this there is about 400GB that really needs to be protected in the event of this server catching fire - university work, projects I've worked on, ambulance service stuff, family photos, etc. I already have a 1 year subscription to [OneDrive](https://en.wikipedia.org/wiki/OneDrive) that came free with a cheapo laptop I bought, I don't use it because Microsoft doesn't support Linux clients.

I looked around for implementations of Linux clients for OneDrive and there are one or two on GitHub and I could base a software project on one of these perhaps. The other option that I'm thinking of is to have a Windows VM acting as a 'staging point' for data to be synced with OneDrive. So steps to set this up would be:

**Stand up a Windows VM** - I'm going to use the Proxmox machine for this, which at the moment is a vintage HP desktop. I'll be giving it 2Tb on a dedicated rotating drive, so it will be super slow in terms of disk access - but I don't mind how long it takes to do the sync. This seemed like a good use of a laptop drive that I had lying around. It will be configured with my OneDrive account details and will share its local OneDrive directory (where the OneDrive service monitors for changes).

**Backup cron job** - I'm hoping this will be as easy as rsyncing between the shares to be backed up on Unraid and the OneDrive share on the windows staging machine. At which point OneDrive will detect the changes and upload them to Microsoft-land. 

That's the plan.

### Windows VM

I've installed an old 2tb laptop drive in the Proxmox machine for this VM to use, and allocated it 1583GiB (approximates to 1.7Tb), 1 core and 2048MiB RAM (the Windows 10 minimum system requirement). Right away the slowness of the mechanical drive is apparent, it takes 5 minutes to create the VM. Next is to set up a user (that will be used for remote access to the share).

I've set up a Windows share on the directory OneDrive is using. I thought about alternative ways of getting files into this directory to be synced, rather than a samba share. I like using SSH, but this limits me to using `scp` for syncing files across systems. I need to use `rsync` because it copies only changes - so allows incremental updates. If I mount the windows share on a Linux machine then I can `rsync` into it. There are implementation of rsyncd for windows but it seems to involve installing a Linux emulator. It seems like a point of failure.

I'm ticking off the '2' of the 3-2-1 rule here as it's a copy of the data on a different machine to the original.

### Syncronisation Job

I'm running this on the Proxmox server too, this is because I consider this to be a 'live' server, but has no unique data on it. Its a web server with content from GitHub, and the staging server for OneDrive. 

Shares from Unraid to be backed up are mounted on the Proxmox server using a username with read-only permissions. The share from the Windows VM hosting OneDrive is also mounted locally. Then its just a case of running this command for each share to be backed up:
`rsync -rv /mnt/unraid-share/ /mnt/windows-share/OneDrive/nas-backup/`

I've since modified this command to include:

- `--size-only` - I had a problem that because the OneDrive app on windows seems to mess with the file modified timestamps, `rsync` was moving everything, every time. So now it only copies files if their file size changes. This might be risky as there is a chance that an older version could overwrite a newer one, but I can't (at the moment) think of when that might arise.
- `--contimeout=60` - This stops the job hanging if there is a network problem - it just aborts and hopefully will work on the next run.

Next is to run this command and try it with the first share, approx 80GB. Then run it again to make sure the incremental aspect is working. Providing that works OK I'll set it up as a cron job.

The shell script ends up like this:

```bash
 function myecho() {
         echo "date +%y/%m/%d_%H:%M:%S:: $@"
 }
 logfile="sync-log.txt"
 echo '-----------------------------------------------------------------------' >> $logfile
 myecho 'STARTED' >> $logfile
 echo '-----------------------------------------------------------------------' >> $logfile
 rsync -rv --size-only /mnt/source-share/ /mnt/onedrive-sync/ >> $logfile
 echo '-----------------------------------------------------------------------' >> $logfile
 myecho 'FINISHED' >> $logfile
 echo '-----------------------------------------------------------------------' >> $logfile
```

and the cron job looks like this:

```cron
0 * * * * /root/sync-onedrive/sync-onedrive.sh
```

### Limitations & Future Plans

This system isn't true replication as it doesn't handle deletes: even if a file is deleted in the source data, this won't be reflected in OneDrive. Deletions have to be done manually in both data sets.

When my OneDrive subscription runs out I'll look at other providers, and maybe reevaluate this. 

I need to add some better logging / error alerts for when the rsync job fails.

OneDrive 1Tb    £60/year
pCloud Premieum Plus 2Tb    £100/year or £350/life 
