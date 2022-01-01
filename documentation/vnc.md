---
parent: Documentation
---

# VNC viewer packages

When installing epoptes or epoptes-client, one of the following VNC viewer packages will automatically get installed:

- [realvnc-vnc-viewer](#realvnc-vnc-viewer)
- [ssvnc](#ssvnc)
- [xtightvncviewer](#xtightvncviewer)
- [xvnc4viewer](#xvnc4viewer)
- [tigervnc-viewer](#tigervnc-viewer)

It's possible to select which one you prefer by installing it before installing epoptes. Otherwise they're preferred in the order mentioned above, depending on what's available in your repositories.

If multiple VNC viewers are installed, epoptes will use the value of the VNCVIEWER environment variable, if it's set in /etc/default/epoptes[-client]. If unset, it will run /usr/bin/vncviewer, which may be a symlink to /etc/alternatives/vncviewer. In that case you may run `sudo update-alternatives --config vncviewer` to select your preferred VNC viewer.

VNC viewers are used by epoptes in two cases, and they need to support reverse connections (`-listen`), so some viewers like gvncviewer don't qualify.

- When broadcasting the teacher screen:
  - student (client-functions>receive_broadcast) uses options: fullscreen, menukey, shared, passwd, viewonly.
  - teacher (gui.py>broadcast_screen) runs: `x11vnc -viewonly`.
- When monitoring or assisting students:
  - teacher (gui.py>reverse_connection) uses options: [multi]listen.  
    student (client-functions>get_monitored/get_assisted) runs: `x11vnc -connect`.

## realvnc-vnc-viewer

It's proprietary and can be downloaded from [realvnc.com](https://www.realvnc.com/en/connect/download/viewer/linux). On Raspberry Pi OS, it's preinstalled and available in the repositories.

- Scaling: yes
- License: each user needs to accept it separately. A workaround is to execute it once, and then run:

```shell
sudo cp ~/.vnc/config.d/vncviewer /etc/epoptes/
```

## ssvnc

Of the open source clients, it's the one with the most features. Unfortunately it recommends the default-jre package to support ultravnc file transfers; to avoid default-jre, run the following command before installing epoptes:

```shell
sudo apt-get install --no-install-recommends ssvnc
```

Some notes about ssvnc:

- Scaling: yes, but `-scale auto` only works [in windowed mode](https://bugs.debian.org/801804).
  A workaround is for the students to press F9 twice, or to select it from the F8 menu, or epoptes-client could pass a fixed resolution like `-scale 1600x900`.
- Scrolling is a bit hard: dragging or left-right panning (fullscreen), left-right click on thin scroll bars (windowed).
- The F8 popup menu cannot be disabled.

## xtightvncviewer

- Scaling: no

## xvnc4viewer

It's been removed from most distributions and it's now only available from the [Greek schools PPA](https://launchpad.net/~ts.sch.gr/+archive/ubuntu/ppa).

- Scaling: no

## tigervnc-viewer

While tigervnc-viewer is the one with the highest availability in various Linux distributions, it's unfortunately the one least suitable for epoptes:

- Scaling: no (supports only remote scaling, not compatible with x11vnc)
- Multilisten: no, the teacher can only view [a single student](https://github.com/TigerVNC/tigervnc/issues/400)
- Mouse cursor: [invisible](https://github.com/TigerVNC/tigervnc/issues/1346)
