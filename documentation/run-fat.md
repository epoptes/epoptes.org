---
parent: Documentation
---

# Running from a fat client

This page assumes that you already have a working LTSP fat clients installation, with the epoptes package installed on the LTSP server and epoptes-client in the chroot, as described in the installation page.

Applications on fat clients are ran locally, but the Epoptes user interface needs to be launched on the LTSP server, where the Epoptes daemon is running. Fortunately, LTSP provides a technology called remote apps that helps in doing so. To enable it, open your lts.conf file, usually located in /var/lib/tftpboot/ltsp/i386/lts.conf (if it doesn't exist, create it), and put the following lines under the [Default] section:

```shell
[Default]
    REMOTE_APPS=True
    RCFILE_01="sed 's,^Exec=/usr/bin/epoptes,Exec=ltsp-remoteapps dbus-launch epoptes,' -i /usr/share/applications/epoptes.desktop"
```

Reboot a fat client and login as a user which is a member of the epoptes group. Then open a terminal and run this command:

```shell
ltsp-remoteapps dbus-launch epoptes
```

Epoptes should open, and on its window title bar it should be mentioning that it's running on the server instead of the local PC.

If you have a recent LTSP version, the RCFILE_01 directive above should allow you to run Epoptes remotely without opening a terminal, by using the DE menus. If not, you can run that sed command inside your chroot, so that the epoptes.desktop file is changed to include ltsp-remoteapps in front of the Exec line.
