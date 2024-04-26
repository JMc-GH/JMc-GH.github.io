---
title: Configuring Debian to Automatically Apply Security Updates
date: 2022-08-11
categories:
    - Tech
tags:
    - Linux
    - Debian
    - Proxmox
    - config
---

I'm doing this on a 'live' virtualisation server running Proxmox. There is a first step here to change the Proxmox repo, as I'm cheap and I haven't paid for the enterprise edition, I don't have access to the enterprise repositories. This causes at error when you `apt update`. So I added a file called `pve-non-enterprise.list` which includes the line:  
`deb [arch=amd64] http://download.proxmox.com/debian/pve bullseye pve-no-subscription`  
I renamed the old file in the same directory, which causes a warning - which I'm happy with.

### Unattended Upgrades
This is a package, installed with apt
`apt install unattended-upgrades`  
   
Then enable and start it a service:  
`systemctl enable unattended-upgrades`  
`systemctl start unattended-upgrades`  
  
Edit `/etc/apt/apt.conf.d/50unattended-upgrades` to make sure it includes these lines:  
```
        "origin=Debian,codename=${distro_codename},label=Debian";
        "origin=Debian,codename=${distro_codename},label=Debian-Security";
        "origin=Debian,codename=${distro_codename}-security,label=Debian-Securi>
```  
  
More info here [linode](https://www.linode.com/docs/guides/how-to-configure-automated-security-updates-debian/)

