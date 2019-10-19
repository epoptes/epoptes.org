---
parent: Documentation
---

# Windows client

No Windows port of epoptes-client currently exists and the developers have no plans to implement one in the near future. However, in case anyone's up to the task, here are some key parts that are needed. The client should be able to:

- Communicate with the server over an OpenSSL socket and receive commands from it.
- Generate thumbnails of the user screen in an efficient way.
- Lock the user screen, disabling all special keyboard shortcuts like Alt+F4 or Alt+Ctrl+Del.
- Mute the sound volume.
- Launch a vncviewer to receive screen broadcasting.
- Launch a vncserver to give control of the local screen.
- Login, logout, reboot and shutdown the client.
- Try to mimic some Linux shell commands, e.g. `xdg-open ~/Documents/file.odt` would become `start C:\Users\username\Documents\file.odt`.

If someone implements those and plans to maintain the Windows port of epoptes-client, the developers would happily help with any missing bits.
