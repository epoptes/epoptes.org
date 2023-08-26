---
parent: Documentation
---

# Running from LTSP fat clients

In recent Epoptes versions (>= 23.08), it's possible to run `epoptes` from any
LTSP fat client, and seamlessly control all epoptes-clients in the same subnet.
This is automatically accomplished using the following logic:

- If epoptes-daemon isn't running locally, and this is an LTSP client, then
  `ltsp remoteapps` is used to connect to the remote epoptes-daemon running on
  the LTSP server, via SSH.
- Client thumbnails, command execution etc all happen through the SSH channel.
- But certain features that need additional performance, such as screen
  broadcasting and monitoring, LAN benchmark etc, are performed directly and
  not via the LTSP server. These features will then only work if the "teacher
  PC" is in the same IP subnet as the "student PCs".

For older Epoptes versions or for some specific use cases, there are two other
ways to run `epoptes` in an LTSP fat client, described below.

## Remotely

It's possible to launch the Epoptes GUI remotely on the LTSP server using the
`ltsp remoteapps epoptes` LTSP command. To do that, put the following in
ltsp.conf, run `ltsp initrd`, and reboot the clients:

```shell
[clients]
POST_INIT_EPOPTES="sed 's|^Exec=/usr/bin/epoptes|Exec=ltsp remoteapps epoptes|' -i /usr/share/applications/epoptes.desktop"
```

After that, they should be able to run Epoptes as usual, from the system menu,
although all VNC traffic will go through the SSH tunnel and it will be quite
slow.

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
