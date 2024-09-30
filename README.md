# DIP virtual machine walkthrough

## 01_apache-james:

finding machine in my network

![](01_apache-james/2024-09-17_08-26.png)

finding apache james port opened

![](01_apache-james/2024-09-17_08-27.png)

telneting and using user naming bug to access /etc/bash_completion.d

![](01_apache-james/2024-09-17_08-34.png)

25 port also opened

![](01_apache-james/2024-09-17_08-37.png)

telneting to smtp and sending email

![](01_apache-james/2024-09-17_08-43.png)

starting listening and waiting for connection from attacked machine

![](01_apache-james/2024-09-17_08-44.png)

## 02_nfs:

nfs related ports opened

![](02_nfs/2024-09-24_07-12.png)

can also confirm witn rpcinfo

![](02_nfs/2024-09-24_07-17.png)

searching for related exploit

![](02_nfs/2024-09-24_07-19.png)

![](02_nfs/2024-09-24_07-21.png)

![](02_nfs/2024-09-24_07-22.png)

mounting the directory

![](02_nfs/2024-09-24_07-25.png)

![](02_nfs/2024-09-24_07-26.png)

we'll try this info for ssh connection

![](02_nfs/2024-09-24_07-27.png)

creating payload for priviledge escalation

![](02_nfs/2024-09-24_07-29.png)

![](02_nfs/2024-09-24_07-29_1.png)

trying secret found to ssh the machine

![](02_nfs/2024-09-24_07-34.png)

compiling payload

![](02_nfs/2024-09-24_08-26.png)

adding access rights

![](02_nfs/2024-09-24_08-26_1.png)

and... we are ROOT!

![](02_nfs/2024-09-24_08-34.png)

## 03_sudoers:

ssh opened

![](03_sudoers/2024-09-27_12-55.png)

searching for relevant bruteforce tool

![](03_sudoers/2024-09-27_12-57.png)

![](03_sudoers/2024-09-27_13-02.png)

secret found

![](03_sudoers/2024-09-27_13-19.png)

logging in via ssh

![](03_sudoers/2024-09-27_13-20.png)

no sudo superpowers

![](03_sudoers/2024-09-27_13-22.png)

but there are some programs listed in /etc/sudoers

![](03_sudoers/2024-09-27_13-23.png)

![](03_sudoers/2024-09-27_13-23_1.png)

let's change it a bit

![](03_sudoers/2024-09-27_13-28.png)

we are ROOT!

![](03_sudoers/2024-09-27_13-29.png)

we can also run bash from vi

![](03_sudoers/2024-09-27_13-30.png)

![](03_sudoers/2024-09-27_13-30_1.png)

or run commands via python

![](03_sudoers/2024-09-27_13-33.png)

we can also read secret directly with Vi

![](03_sudoers/2024-09-27_13-35.png)

or with python oneliner

![](03_sudoers/2024-09-27_13-36.png)

or calling sh

![](03_sudoers/2024-09-27_13-37.png)

one more way - nmap script

![](03_sudoers/2024-09-27_13-43.png)

we are ROOT again!

![](03_sudoers/2024-09-27_13-44.png)

## 04_phpMyAdmin:

apache is running

![](04_phpMyAdmin/2024-09-27_17-11.png)

checking also with nikto

![](04_phpMyAdmin/2024-09-27_17-14.png)

phpmyadmin detected and accessible

![](04_phpMyAdmin/2024-09-27_17-15.png)

searching for relevent exploit

![](04_phpMyAdmin/2024-09-27_17-16.png)

configuring options for brutforce

![](04_phpMyAdmin/2024-09-27_17-34.png)

secret found

![](04_phpMyAdmin/2024-09-27_17-43.png)

login successful

![](04_phpMyAdmin/2024-09-27_18-06.png)

writing webshell via sql query

![](04_phpMyAdmin/2024-09-27_18-11_1.png)

![](04_phpMyAdmin/2024-09-27_18-12.png)

accessing webshell

![](04_phpMyAdmin/2024-09-27_18-13.png)

folders witn 777 permissions found

![](04_phpMyAdmin/2024-09-27_18-15.png)

system info gathered

![](04_phpMyAdmin/2024-09-27_18-15_1.png)

searching for relevant exploits, I need to escalate privileges

![](04_phpMyAdmin/2024-09-28_06-43.png)

![](04_phpMyAdmin/2024-09-28_06-45.png)

looking for sploit path

![](04_phpMyAdmin/2024-09-28_06-45_1.png)

sploit shared via

```sh
python3 -m http.server
```

![](04_phpMyAdmin/2024-09-28_06-48.png)

![](04_phpMyAdmin/2024-09-28_06-49.png)

reverse shell

![](04_phpMyAdmin/2024-09-28_06-51.png)

we are ROOT after running compiled sploit!

![](04_phpMyAdmin/2024-09-28_07-11.png)
