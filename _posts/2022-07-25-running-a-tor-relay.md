---
title: 'Running a Tor relay'
date: 2022-07-21
draft: false
categories:
 - Tech
tags:
 - Linux
 - config
 - privacy
---

## TL;DR

```bash
apt install tor  
nano /etc/tor/torrc
```

```bash
Nickname    myNiceRelay
ContactInfo your@e-mail
ORPort      443  
ExitRelay   0  
SocksPort   0
```

```bash
systemctl restart tor
```

## A What?

I've been wanting to do this for a while - and I've got loads of zombie PCs around the place in varying states of undress. I thought I'd have a go at contributing to the Tor network by setting up a relay node.

Not an [exit node](https://community.torproject.org/relay/types-of-relays/), I need to know more about the legal issues of this - I'm not sure how into it BT are. I'm going to run a middle (or guard) node. This is effectively donating some of my internet bandwidth to Tor, but also helping to secure the network. Last year it a mysterious threat actor, [KAX17](https://blog.malwarebytes.com/reports/2021/12/was-threat-actor-kax17-de-anonymizing-the-tor-network/) ran about 900 malicious servers (about 10% of all relays) in a probable attempt to de-anonymise the network.

The Tor project is really well documented and this <a href="https://community.torproject.org/relay/" target="_blank">guide</a> is excellent.

### Ingredients

- An old HP Desktop i5 - 5th? Gen. 4Gb RAM
- Ubuntu Server
- 120Gb SSD

### Method

#### Setup a base install of ubuntu server

With hindsight I'd have used FreeBSD because I want to get some experience of it. I didn't because I can troubleshoot linux better. So I'm going to attempt to migrate to FreeBSD at some point. All I included in the package options was an OpenSSH server.

#### Install Tor

This means adding the Tor repository to apt and using that to install it. Tor project has this [guide](https://support.torproject.org/apt/tor-deb-repo/)

#### Configuration File

This file drives the whole show its in:  
`/etc/tor/torrc`  
really all you need to change are Nickname and ContactInfo (and not your work email address)

#### Restart the deamon

`systemctl restart tor`

#### Check the logs

`tail /var/log/syslog`
