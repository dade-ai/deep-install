virtualbox
===

virtualbox5.1 for 16.04

reference
---
- https://www.virtualbox.org/wiki/Linux_Downloads

install
---

```
sudo sh -c "echo 'deb http://download.virtualbox.org/virtualbox/debian '$(lsb_release -cs)' contrib non-free' > /etc/apt/sources.list.d/virtualbox.list"

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get install dkms
sudo apt-get install virtualbox-5.1 virtualbox-ext-pack
```
