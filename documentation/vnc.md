---
parent: Documentation
---

# VNC

This page tries to explain the reasoning for the selected vnc viewer and server dependencies. Those are needed in two cases, when a person using the epoptes UI wants to broadcast his screen, or when he wants to monitor the screen of an epoptes-client user.

## VNC server selection

To monitor a user's screen, vncviewer -listen is started on the server to listen for reverse connections, and x11vnc -connect is ran on the clients to connect to the server. Reverse connections were chosen for simplicity; only one port needs to be open on the server, the clients can even be behind NAT or behind firewalls, and all connections can be terminated by killing a single process.
This design choice resulted in ruling out vino-server as the vnc server, because it doesn't have a -connect option. And we wanted to keep the RAM usage low, so x11vnc was the only real option, at least until a C client that uses some vnc library is developed.
To broadcast the screen of the person using the epoptes UI, a vnc server is started in shared read-only mode, and epoptes-cilent launches a vnc viewer that connects to that vnc server. Unfortunately the embedded vino-server doesn't have any command line parameters that would allow doing that, but fortunately we'd already selected x11vnc, which easily meets the requirements.

## VNC client selection

Part of epoptes-client requirements was that it should be able to run on LTSP thin clients with only 64MB RAM, so RAM usage played a key role in the app selection. The following clients were taken into consideration. Vinagre was ruled out due to its big list of dependencies (we wouldn't want gconf in LTSP chroots by default) and great RAM usage, and gvncviewer for its RAM usage. Also, from all of them, only xvnc4viewer had a command line option to completely disable the F8 menu. Teachers usually don't want the students to be able to stop the screen broadcasting.

```shell
USER  PID %CPU %MEM    VSZ   RSS TTY   STAT START TIME COMMAND
user 5832  0.9  0.2  10412  7432 pts/1 S    18:43 0:01 ssvncviewer localhost
user 5915 11.0  0.5 118244 15884 pts/1 Sl   18:44 0:11 gvncviewer localhost
user 5940  0.7  0.2   9576  6764 pts/1 S    18:44 0:00 xvnc4viewer localhost
user 6001  7.8  0.7 145456 21820 pts/1 Sl   18:44 0:05 vinagre localhost
```

The developers have considered using some VNC library in the future, perhaps the one remmina uses, but the client will need to be written in C to keep the RAM usage low.
