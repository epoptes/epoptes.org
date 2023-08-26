---
parent: Documentation
---

# ltsp.conf groups

In [LTSP based computer labs](https://ltsp.org), an alternative way to define
[global groups](global-groups.md) and [aliases](aliases.md) is to use the
following `/etc/ltsp/ltsp.conf` structure. Note that a recent Epoptes version
is required (>= 23.08):

```shell
[server]
...

[common]
...

[clients]
...

# EPOPTES_GROUP=Lab A
[01:02:03:04:05:a1]
HOSTNAME=a01

[01:02:03:04:05:a2]
HOSTNAME=a02
...

# EPOPTES_GROUP=Lab B
[01:02:03:04:05:b1]
HOSTNAME=b01

[01:02:03:04:05:b2]
HOSTNAME=b02
...

# EPOPTES_GROUP=X-Hidden-Staff
[01:02:03:04:05:c1]
HOSTNAME=staff01

[01:02:03:04:05:b2]
HOSTNAME=staff02
...

# EPOPTES_GROUP=None
```

- I.e. the line `# EPOPTES_GROUP=Lab A` means that the HOSTNAMEs defined in
subsequent [mac address] sections will be displayed as a group named `Lab A`.
- The same goes for `Lab B`.
- Note that if a group name starts with `X-Hidden-`, then this group won't
appear at all in the Epoptes UI, so you can e.g. hide the staff PCs that way.
- Finally, HOSTNAMEs under `EPOPTES_GROUP=None` will be displayed in the
`Autodetected` group but not in any named group.
