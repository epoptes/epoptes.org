---
parent: Documentation
---

# Google Summer of Code

This is a blueprint for a possible GSoC or Outreachy project on
[Epoptes](https://epoptes.org), which is a computer lab management and
monitoring tool.

## Project goals

The following three tasks are more than enough for a GSoC/Outreachy project:

- Reimplement the network benchmark tool with python libraries, e.g. twisted.
- Replace xterm with tabbed VTE widgets for the "Open terminal" action.
- Allow running the GUI remotely with an [OpenSSL client
  certificate](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html).

For a future second project, these tasks can also be considered:

- Reimplement epoptes-client in python instead of shell.
- Use a VNC library instead of relying on external programs like x11vnc and
  xvnc4viewer.
- Investigate screen sharing on Wayland.

### Network benchmark tool

The current implementation of the network benchmark tool is externally calling
iperf v2, which is deprecated and rather unstable. Its backend should be
rewritten using native python libraries, for example
[socket](https://docs.python.org/3/library/socket.html) for the clients and
either socket or [twisted](https://twistedmatrix.com/trac/) for the server.

### Replace xterm with VTE

When selecting many clients and choosing to open a terminal locally, multiple
xterm windows appear, cluttering the user workspace. The xterm dependency must
be removed for Wayland compatibility. We should instead use vte and
gtk.Notebook to provide a tabbed window, where each tab contains a remote
terminal. This can also be reused by epoptes-client/receive-terminals.
Additionally, it will make Epoptes more firewall-friendly, by allowing it to
use a single server port for this function.

The most difficult part will be to replace the socat stdio descriptors handling
(`socat tcp-listen:5499,keepalive=1 stdio,raw,echo=0`) with Python/VTE
equivalents.

### Remote GUI

The Epoptes daemon usually listens for connections on
/run/epoptes/epoptes.socket, which can be accessed only by members of the
epoptes group. Additionally listening on an OpenSSL socket should make it
possible for clients to connect securely and authenticate using an [OpenSSL
client
certificate](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html).
The client certificate could reside in the client /etc/epoptes/gui.pem, or, for
LTSP where the disk is public, in ~/.config/epoptes/gui.pem. Then the gui.py
would check for that file, and if present, it would use it to connect to the
server. This architecture means that the file would be manually transferred to
each client image or LTSP user.

### Epoptes client in Python

Epoptes client was written in shell for minimal RAM requirements (e.g. 1 MB),
as at the time schools used LTSP thin clients with as low as 64 MB RAM. The use
of socat for encryption increased the RAM usage. Now that LTSP no longer
supports thin clients, reimplementing epoptes-client in Python would remove the
socat dependency and allow LTSP to push epoptes-client even to netbooted live
CDs.

### VNC library

Epoptes supports broadcasting the teacher screen and assisting the students by
taking control of their screens remotely. To do that, it's using external
programs like x11vnc, xvnc4viewer, tightvnc, tigervnc, ssvnc. Most of these
programs have maintenance issues and some of them have already been removed
from distributions. On the other hand, there are some VNC libraries available
in most distributions. They should be evaluated, and if some of them plans to
eventually support Wayland, Epoptes should be rewritten to use that library
instead of the external VNC programs.

### Screen sharing on Wayland

Some developers are trying to [implement screen sharing on
Wayland](https://www.phoronix.com/scan.php?page=news_item&px=WebRTC-Wayland-Screen-Share)
using modern technologies like WebRC/PipeWire. The current status should be
evaluated, and if it appears to be mature, code could be added in Epoptes to
support that.

## Application/evaluation tasks

Students that apply for a GSoC/Outreachy project should implement the following
task for their initial evaluation:

> 👉 Implement a network benchmark tool in Python using the [socket
> library](https://docs.python.org/3/library/socket.html), that measures the
> upload/download speed between only two computers in the local network.
