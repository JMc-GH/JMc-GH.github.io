---
title: "Hacking air-gapped networks"
date: 2022-09-04T22:55:03+01:00
categories:
  - World
tags:
  - Security
  - Networks
  - Systems
---
Hacking networks that are not connected to other networks (including the internet) are thought to be super-secure. They are used for malware analysis, exploit research and keeping sensitive systems from outside interferance. 

The way these networks can be compromised is interesting, and examples of excersices in latering thinking. It seems that two types of attack are possible against air-gapped networks.

The most researched is data exfiltration, this tends to be done by turning a target on the air-gapped network into a transmitter. Computers come with transmitters, a speaker, wi-fi card. Obviously these are removed disabled to prevent just this kind of thing. Research conducted at Ben-Gurion University (who seem to be really into this kind of thing) have found ways around this.

Air gapped networks are used for malware analysis, exploit research and running the control systems for your uranium enriching centrifuges. Hacking them by definition requires something that can travel through air, so radio, light and sound emissions that can be picked up by the crooks (using their mobile phone gyroscope as a microphone, for example). 

[Mordechai Guri](https://cris.bgu.ac.il/en/persons/mordechai-guri) has been exploring these air-gap 'vulnerabilities' using LAN cables as radio transmitters, Ethernet LED indicators as Morse signalers or using the varying speed of a system fan as a sound transmitter. He also has some other interesting stuff like what he's found on [DDOS attacks on emergency services during the 911 attacks](https://ieeexplore.ieee.org/abstract/document/8949688).

Denials of service are possible, like by [RnB-ing a hard drive to death](https://www.wired.com/story/janet-jackson-rhythm-nation-crash-hard-drives/) by playing it a Janet Jackson track.

Probably the the most famous example of a defeated airgap is [Stuxnet](https://dale-peterson.com/2016/06/20/s4-classic-video-langners-stuxnet-deep-dive/)

Humans can also travel through air so I think that [USB Baiting](https://aware.eccouncil.org/usb-baiting.html) is a kind of air-gap hack?
