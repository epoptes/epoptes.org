---
parent: Documentation
---

# Google Summer of Code
This is a blueprint for a possible GSoC or Outreachy project on [Epoptes](https://epoptes.org), which is a computer lab management and monitoring tool.

## Project goals

- Reimplement the network benchmark tool with python libraries, e.g. twisted.
- Allow running the GUI remotely with an [OpenSSL client certificate](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html).
- Use a VNC library instead of relying on external programs like x11vnc and xvnc4viewer.
- Investigate screen sharing on Wayland.
- Reimplement epoptes-client in python instead of shell.

### Network benchmark tool

The current implementation of Epoptes network benchmark tool is externally calling iperf v2, which is rather unstable. Its backend should be rewritten using native python libraries, for example twisted.

### Remote GUI

The Epoptes daemon usually listens for connections on /run/epoptes/epoptes.socket, which can be accessed only by members of the epoptes group.
Additionally listening on an OpenSSL socket should make it possible for clients to connect securely and authenticate using an [OpenSSL client certificate](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html).
The client certificate could reside in the client /etc/epoptes/gui.pem, or, for LTSP where the disk is public, in ~/.config/epoptes/gui.pem. Then the gui.py would check for that file, and if present, it would use it to connect to the server.
This architecture means that the file would be manually transferred to each client image or LTSP user.

### VNC library

Epoptes supports broadcasting the teacher screen and assisting the students by taking control of their screens remotely. To do that, it's using external programs like x11vnc, xvnc4viewer, tightvnc, tigervnc, ssvnc. Most of these programs have maintenance issues and some of them have already been removed from distributions.
On the other hand, there are some VNC libraries available in most distributions. They should be evaluated, and if some of them plans to eventually support Wayland, Epoptes should be rewritten to use that library instead of the external VNC programs.

### Screen sharing on Wayland

Some developers are trying to [implement screen sharing on Wayland](https://www.phoronix.com/scan.php?page=news_item&px=WebRTC-Wayland-Screen-Share) using modern technologies like WebRC/PipeWire. The current status should be evaluated, and if it appears to be mature, code could be added in Epoptes to support that.

### Epoptes client in Python

Epoptes client was written in shell for minimal RAM requirements (e.g. 1 MB), as at the time schools used LTSP thin clients with as low as 64 MB RAM. The use of socat for encryption increased the RAM usage. Now that LTSP no longer supports thin clients, reimplementing epoptes-client in Python would remove the socat dependency and allow LTSP to push epoptes-client even to netbooted live CDs.

## Application/evaluation tasks

Students that apply for a GSoC/Outreachy project should implement the following tasks for their initial evaluation:

- Implement a network benchmark tool in python, that measures the upload/download speed between only two computers in the local network.
- Try out and document the software and steps involved for sharing the screen (or a window, whichever is easier) between two users under Wayland, in any distribution.
