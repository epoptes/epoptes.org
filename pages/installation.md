---
title: "Installation"
permalink: /installation/
---

# Installation

Epoptes consists of a server package called `epoptes` and a client package called `epoptes-client`. Install the server part on the PC where you'll be monitoring the clients from. If you want to use the GUI from a thin-client, install it on the LTSP server.

## Server package installation

Execute the following command as root (use `sudo -i` first on Ubuntu or `su -` on Debian):

```shell
apt-get install --install-recommends epoptes
```

After the installation you need to add some users to the "epoptes" group (or use another group as mentioned in the Configuration section below). These users will be allowed to launch the GUI and control clients:

```shell
gpasswd -a username epoptes
```

Users that are currently logged on need to logoff/logon for the group change to take effect (or use `newgrp`).

## Client package installation for standalone clients

Before installing the epoptes-client package, it's necessary to tell the clients how to contact the epoptes server PC. There are three different ways to do  that:

1. By default, epoptes-client tries to connect to the epoptes server with the DNS name "server". So if you have a DNS server (most people don't run their own DNS server though), put a corresponding entry there.
2. If you don't have a DNS server **and** your epoptes server has a static IP (many people don't use static IPs though), you can put a line like 1.2.3.4 server to /etc/hosts in all clients, replacing 1.2.3.4 with the server's static IP.
3. If your epoptes server doesn't have a static IP, then it might be possible to use its avahi (multicast DNS) hostname that is automatically provided in most recent distributions. For example, if your server hostname is "myserver", try this command in one of your clients: ping myserver.local. If this command works, then your multicast DNS is working properly, and you tell your clients where to find the epoptes server by putting SERVER=myserver.local in /etc/default/epoptes-client in all of them.

If needed, [this launchpad question](https://answers.launchpad.net/epoptes/+question/284584) provides more details on the aforementioned methods.
After you've configured where the clients will find the epoptes server, execute these commands as root in them (use `sudo -i` first on Ubuntu or `su -` on Debian):

```shell
apt-get install --install-recommends epoptes-client
epoptes-client -c             # Fetches the OpenSSL certificate from the server
```

Note that packages are not allowed to start programs inside a user's session, so you need to reboot the clients for the epoptes-client installation to take effect.

## Client package installation for LTSP chroots

For LTSP chroots, execute the following commands:

```shell
sudo ltsp-chroot
apt-get install --install-recommends epoptes-client
epoptes-client -c             # Fetches the OpenSSL certificate from the server
exit
```

If you're using NBD (all Ubuntu versions and Debian >=8), you also need to update the NBD image for the changes to take effect:

```shell
sudo ltsp-update-image
```
