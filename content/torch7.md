torch7
===

- http://torch.ch/docs/getting-started.html#_

# issue
virtualbox5 needs
virtualbox5.1 not work


install
---

```
# in a terminal, run the commands WITHOUT sudo
git clone https://github.com/torch/distro.git ~/torch --recursive
cd ~/torch; bash install-deps;
./install.sh
source ~/.bashrc
```

package control
---
```sh
# run luarocks WITHOUT sudo
$ luarocks install image
$ luarocks list
```

test
---
```sh
th -h
```

update
---
```sh
torch$ ./update.sh
```
