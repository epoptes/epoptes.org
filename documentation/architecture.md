# Architecture

A few notes about the Epoptes architecture:

- Epoptes utilizes reverse connections, i.e. the clients connect to the server and offer it an actual /bin/sh shell for remote command execution.
- This means that epoptes-client consumes less than 1 MB RAM!
- Well, 2 MB, as for each computer there are 2 epoptes-client processes, one running as a system service that handles tasks like reboot, shutdown, or screen broadcasting, and another running inside the user session that handles logout, screen locking and launching documents, applications or URLs.
- The epoptes-server package consists of two components, the daemon and the GUI.
- The daemon is implemented in python/twisted. It's accepting client connections at the privileged port 789. It uses a socket in /var/run/epoptes/epoptes.socket to accept GUI connections. That socket is also used for authentication purposes, as it's owned by group "epoptes", so only users in that group can control the clients. To change the group, modify /etc/default/epoptes. Multiple GUIs can connect to the daemon, so one daemon can serve multiple computer labs.
- The GUI part is implemented in python/gtk. It receives events from the daemon as clients connect and disconnect, and periodically asks the clients to provide thumbnails of their screens. It also displays any dialogs required for user interaction.
- The commands that are sent to the clients, like logoff or sound muting, are mostly small shell scripts. Using shell scripts for the DE-specific parts not only saves RAM but also makes the code smaller and more maintainable.
