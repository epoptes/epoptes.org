---
parent: Documentation
---

# Running from a fat client

This page assumes that you already have a working LTSP installation, with the epoptes package installed in the LTSP server and epoptes-client in the image, as described in the [LTSP installation page](https://ltsp.org/docs/installation/).

Now suppose that your LTSP server is headless, and that it serves 3 computer labs. How would Epoptes operators in each lab run it in that case? Two solutions called "Remotely" and "Locally" are presented below. The following table compares them:

| Question | Remotely | Locally |
|--|--|--|
| Where does the Epoptes GUI run? | In the LTSP server |  In an "epoptes PC" per lab |
| Which epoptes-clients are seen? | All | Only the ones in the current lab |
| Is screen broadcasting fast? | No, it goes via the server |  Yes, it uses direct connections |
| Is it secure? | Yes | Somewhat |

So "locally" is better in all cases, except for security, as then the Epoptes private key gets exposed to the local network, allowing man-in-the-middle attacks but not network sniffing.

## Remotely

Remotely means to connect to the LTSP server and launch the Epoptes GUI there, similarly to `ltsp-remoteapps epoptes` in the older LTSP5. Since the new LTSP doesn't support remote apps, the following steps are needed. First, put the following in ltsp.conf, run `ltsp initrd`, and reboot the clients:

```shell
[clients]
POST_INIT_EPOPTES="sed 's|^Exec=/usr/bin/epoptes|Exec=ssh -X server dbus-launch epoptes|' -i /usr/share/applications/epoptes.desktop"
```

Then, tell all the users in the epoptes group to login to an LTSP client, and to run the following commands once:

```shell
# Generate an SSH key if it doesn't already exist:
test -f ~/.ssh/id_rsa || ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa -N ''
# Enable "passwordless SSH" by trusting the key:
install -m 0600 ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
# Connect to the LTSP server once, in order to trust the server as well:
ssh -X server x-terminal-emulator
```

After that, they should be able to run Epoptes as usual, from the system menu.

## Locally

In this solution, one LTSP client per computer lab is named "the epoptes PC". They are given specific hostnames, for example `a00` for `lab-a`, they run the epoptes service and GUI, and the other LTSP clients of that computer lab are instructed to connect there, instead of the LTSP server. To do all these, the following settings are needed in ltsp.conf. Merge the [server] section shown below with the existing one, don't create a new one:

```shell
[server]
# Keep the epoptes private key in ltsp images
OMIT_IMAGE_EXCLUDES="etc/epoptes/server.key"

[lab-a]
# Instruct lab-a clients to connect to a00.local
# The .local suffix is automatically added to hostnames by "avahi"
POST_INIT_EPOPTES="sed 's/.*SERVER=.*/SERVER=a00.local/' -i /etc/default/epoptes-client"

[mac:address:of:lab-a-epoptes-pc]
HOSTNAME=a00
# In epoptes PCs, do start the epoptes service
KEEP_SYSTEM_SERVICES="epoptes"
IGNORE_EPOPTES=1

[mac:address:of:lab-a-client01]
HOSTNAME=a01
# Use INCLUDE directives to map clients to computer labs
INCLUDE=lab-a
```

Then, run the following commands on the server as root:

```shell
# Regenerate the image (in this case, chrootlesss)
ltsp image /
# Update /srv/tftp/ltsp/ltsp.img with the ltsp.conf changes
ltsp initrd
```
