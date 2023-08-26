---
parent: Documentation
---

# Personal Package Archives

Epoptes packages are available in the stock repositories of many Linux distributions, such as Ubuntu, Debian, ArchLinux etc. However, for Ubuntu, there are also two Personal Package Archives (PPAs) available:

- [Epoptes stable repository](https://launchpad.net/~epoptes/+archive/ubuntu/ppa): it contains the most recent stable epoptes releases for all supported Ubuntu versions.
- [Epoptes proposed repository](https://launchpad.net/~epoptes/+archive/ubuntu/proposed): it contains prerelease epoptes packages for testing purposes.

## Adding the stable PPA

To add the epoptes stable repository to your sources and update to the newest version, execute the following commands:

```shell
sudo -i
add-apt-repository ppa:epoptes
apt-get update
apt-get install epoptes epoptes-client
```

## Adding the proposed PPA

It's recommended to only add the proposed PPA temporarily, in order to update to the epoptes release that you wish to test, and then delete the proposed PPA from your sources:

```shell
sudo -i
add-apt-repository ppa:epoptes/proposed
apt-get update
apt-get install epoptes epoptes-client
rm /etc/apt/sources.list.d/epoptes*proposed*.list
```
