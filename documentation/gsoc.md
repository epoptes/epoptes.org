---
parent: Documentation
---

# Google Summer of Code

This is a blueprint for a possible GSoC or Outreachy project on
[Epoptes](https://epoptes.org), which is a computer lab management and
monitoring tool.

## Project goals

The following tasks are more than enough for a GSoC/Outreachy project:

- Make Epoptes [available on more Linux
  distributions](#available-on-more-distributions).
- Support [screen sharing on Wayland](#screen-sharing-on-wayland).
- [Drop the session service](#drop-the-session-service) and keep only the
  system epoptes-client service.
- Use [systemd socket activation](#systemd-socket-activation) and
  [autorestart](#systemd-autorestart).

For a future second project, these tasks can also be considered:

- [Improve firewall compatibility](#improve-firewall-compatibility).
- Add a [client details view](#client-details-view) option in the GUI.
- [Replace xterm with tabbed VTE widgets](#replace-xterm-with-vte) for the
  "Open terminal" action.
- [Reimplement epoptes-client in python](#epoptes-client-in-python) instead of
  shell.
- Implement the [network benchmark tool](#network-benchmark-tool) in python.
- [Use a VNC library](#vnc-library) instead of relying on external programs
  like vncviewer.

### Available on more distributions

Epoptes has upstream support for [Debian
packaging](https://github.com/epoptes/epoptes/tree/main/debian), and up to date
.deb packages are always available in the [Epoptes
PPA](https://epoptes.org/documentation/ppa/). But no other distributions are
supported upstream.

The [openSUSE Build Service](https://openbuildservice.org/) should replace or
at least complement the Epoptes PPA as it can build packages for a wide range
of distributions, such as Arch, CentOS, Debian, Fedora, Mageia, Raspbian, RHEL,
SUSE, Ubuntu etc. The hardest part, of course, will be to develop upstream
packaging support for many of these distributions.

### Screen sharing on Wayland

The Linux desktop environments are migrating from X11 to Wayland, but most of
the existing screen sharing tools don't work on Wayland yet. Reverse screen
sharing (like `x11vnc -connect teacher-pc`) isn't implemented, and permissions
for screen casting are controlled by [XDG desktop
portals](https://flatpak.github.io/xdg-desktop-portal/#gdbus-org.freedesktop.portal.ScreenCast).

- Native tools should be explored and utilized to automate teacher screen
  broadcasting without the students' confirmation.
- Forward screen sharing should be supported when reverse sharing isn't
  possible.
- In Wayland compositors that don't support screen casting, notifications of
  failure should be displayed in the system tray.
- Thumbshots are probably the hardest to implement and might need to be
  postponed until appropriate XDG desktop portals are developed.

### Drop the session service

Currently, there are two kinds of epoptes-client services, "system" and "session":

- The "system" service is used to manage PCs. It is launched by the epoptes-client systemd service and it runs as root.
- The "session" services are used to manage users. They are launched by /etc/xdg/autostart/epoptes-client.desktop when users login graphically and run from the user account.

This means that if for example 10 users connect via x2go/xfreerdp or locally to a school server, then 11 epoptes-client processes will be launched. This can be optimized to a single service by completely dropping the session services. In order for the system service to be able to launch processes inside the user sessions, [socket](http://0pointer.de/blog/projects/socket-activated-containers.html) or [dbus activation](https://dbus.freedesktop.org/doc/system-activation.txt) and possibly some scripts similar to [get-display](https://github.com/epoptes/epoptes/blob/main/epoptes-client/get-display) could be utilized.

### Systemd socket activation

The epoptesd service, written in python/twisted, listens on port 789 for incoming client connections. This reserves 50 MB of RAM, but in certain cases it not used at all, for example in the very common case when the same template image is cloned to all school PCs. By using systemd socket activation, no RAM will be used until the first connection arrives. [Ubuntu 22.10+ used a similar technique for openssh-server](https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189).

### Systemd autorestart

So far, epoptes-client uses a complicated algorithm to restart itself. The session epoptes-client service is launched by /etc/xdg/autostart. To prevent students from killing it, it traps the TERM signal and accepts the QUIT signal instead. Since this code is shared with the system epoptes-client service, which is started by systemd, it requires sophisticated entries for custom signal handling and process termination.

After the [session service is dropped](#drop-the-session-service), signal handling can be overhauled and process restarting can be removed and delegated to systemd.

### Improve firewall compatibility

As documented in [this open
issue](https://github.com/epoptes/epoptes/issues/11), epoptes currently isn't
firewall-friendly. At the very least, it should define a wide port range for
incoming traffic, such as 5490-5990, that could be whitelisted in firewalls to
have epoptes working without reduced functionality.

To achieve this, several parts that rely on random ports will need to be
rewritten. Ideally, reverse sockets should also be opened when necessary, so
that the clients will be able to reach the epoptes server or the epoptes GUI
even when they are behind NAT.

### Client details view

The epoptes GUI offers an "icon" view of the clients, where either the type of the client is displayed (standalone, thin or fat LTSP client), or a thumbshot of the screen of the logged in user. It would be very helpful to be able to toggle it into a "client health live monitoring" listview of a selection of the following columns:

- Client hostname, MAC, IP, connected usernames
- % utilization of CPU, GPU, RAM, disk and network resources
- Alert icon, based on the client systemd journal and logs

The "client information" dialog could be augmented with these additional statistics, and a .csv export would be handy for inventory management.

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

### Epoptes client in Python

Epoptes client was written in shell for minimal RAM requirements (e.g. 1 MB),
as at the time schools used LTSP thin clients with as low as 64 MB RAM. The use
of socat for encryption increased the RAM usage. Now that LTSP no longer
supports thin clients, reimplementing epoptes-client in Python would remove the
socat dependency and allow LTSP to push epoptes-client even to netbooted live
CDs.

### Network benchmark tool

The current implementation of the network benchmark tool is externally calling
iperf v2, which is deprecated and rather unstable. Its backend should be
rewritten using native python libraries, for example
[socket](https://docs.python.org/3/library/socket.html) for the clients and
either socket or [twisted](https://twistedmatrix.com/trac/) for the server.

### VNC library

Epoptes supports broadcasting the teacher screen and assisting the students by
taking control of their screens remotely. To do that, it's using external
programs like x11vnc, xvnc4viewer, tightvnc, tigervnc, ssvnc. Most of these
programs have maintenance issues and some of them have already been removed
from distributions. On the other hand, there are some VNC libraries available
in most distributions. They should be evaluated, and if some of them plans to
eventually support Wayland, Epoptes should be rewritten to use that library
instead of the external VNC programs.

## Application/evaluation tasks

Many of the goals in this blueprint require research work in addition to the
actual implementation. To demonstrate both abilities, students that apply for a
GSoC/Outreachy project should participate in the following task for their
initial evaluation:

> 👉 Implement a draft version of a shell script that automates teacher screen
> broadcasting on Wayland.
