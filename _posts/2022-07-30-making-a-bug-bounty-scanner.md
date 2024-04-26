---
title: "Making a Bug Bounty Scanner"
date: 2022-07-30
categories:
    - Tech
tags:
    - carbon-arc
    - bug-bounty
draft: true
---

I'm going to a make an application to can for bugs on the internet.

It will:
- Read a list of domains, and for each domain.
- Enumerate subdomains and flag any new ones since last scan
- Perform a targeted scan on new subdomains, initially using an automated tool like nuclei.
- Store results of scans in an RDBMS
- Produce alerts if any of the scan find a vulnerability


This will run as a web-based app on my home internet connection for development, later to be deployed on a VPS somewhere, or possibly containerised and clustered with [k8s](http://kubernetes.io).

The reason I'm doing this:
- Learn how to develop and deploy a full stack web application.
- Make some money from bug-bounty (optional).
- I get to refer to it as a cool project name just like the CIA do.

I'll be blogging about this project under the tag **carbon-arc**. This is from the type of lamp used in [Searchlights](https://en.wikipedia.org/wiki/Searchlight)

