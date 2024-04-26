---
title: "Data Store Setup"
date: 2022-08-01
categories:
    - Tech
tags:
    - carbon-arc
    - RDMS
    - MySQL
    - PostgreSQL
draft: true
---
This is to store source data for the automated scans, so subdomains. It will also store the results of the scans - possibly using triggers to automate alerts.  

I initially went for [PostgreSQL](https://www.postgresql.org/) running on a Ubuntu VM under Hyper-V. I've given it the same resource as a mid-range [DigitalOcean droplet](https://www.digitalocean.com/pricing/droplets), so that **2 CPUs**, **4Gb RAM** and **80Gb SSD**. I want to try and start planning for cloud deployment of this at this stage - while I could give it 23 processors - thats not going to be scalable.  I think this will help me focus on the efficieny of the code and database design too. I went for Postgres for no particular reason other than it seems to be widely used and well supported. It also comes on the Ubuntu server ISO :-). 

There turned out to be problems with remote access to the Postgres server. Sorting this out would mean spending more time than I've budgeted for. I switched to [MySQL](https://www.mysql.com/products/community/) running the same configuration and managed to get a remote accessable blank datbase running quickly. As I didn't really have a solid case for any particular RDBMS, changing this now doesn't matter. 

Rather than design the whole database now, which is what I should probably do. I just want to get the data import (from diodb) bit done first - so I get to grips with the technology. Then move on to the scanning module and see how it spits out results before designing the tables for it.

## Next Steps

- automate subdmain discovery

## TL;DR

**Install** 

`sudo apt update && sudo apt upgrade`

`sudo apt mysql-server`

`sudo systemctl restart mysqld`

**Allow Remote Access**    

`sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`

`bind-address           = 0.0.0.0`
`# skip-networking`

**Add remote user**  

`GRANT ALL ON database_name.* TO user_name@'ip_address' IDENTIFIED BY 'user_password';`
  
  






