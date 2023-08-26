---
parent: Documentation
---

# Global groups

> 💡 **Tip:**
  If using LTSP, see also [ltsp.conf groups](ltsp-groups.md).

Suppose that a school has 5 computer labs and 50 teachers. It would be tiresome
if each teacher had to manually [create Epoptes groups](groups.md) for these
labs. The following solution is provided:

1.  Login as the school "administrator" (it can be one of the teachers) and run
    Epoptes at least once so that the ~/.config/epoptes/groups.json file gets
    created.
2.  Then close Epoptes and execute the following command:
    ```shell
    sudo mv ~/.config/epoptes/groups.json /etc/epoptes/
    ```
    Make sure to use `mv` instead of `cp`, otherwise Epoptes won't have write
    access to /etc/epoptes/groups.json. Or at least use `cp -a`.
3.  From now on, all Epoptes instances will be using /etc/epoptes/groups.json
    instead of per-user configuration files. That means that any Epoptes group
    that the administrator creates, will be visible to the other teachers the
    next time that they run Epoptes.
4.  The other teachers will be able to create or delete groups, but their
    changes will be lost the next time they run Epoptes.

An additional feature was also implemented: the ability to hide some Epoptes
clients, for example staff PCs, from everyone except the administrator. To do
this, the administrator just needs to create a group named "X-Hidden" and to
drag the clients he wants in it. The teachers won't be seeing those clients
anymore, nor the "X-Hidden" group. Multiple hidden groups are also supported,
as long as their names start with "X-Hidden".
