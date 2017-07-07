shareing by nfs
===

reference
---
- https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-16-04


server side
===
```
sudo apt-get update
sudo apt-get install nfs-kernel-server
sudo chown nobody:nogroup /data
sudo nano /etc/export

```
```
# /etc/export
# directory_to_share    client(share_option1,...,share_optionN)
/data       10.10.xxx.xxx/toxxx(rw,sync,no_subtree_check)


```

```
sudo systemctl restart nfs-kernel-server

```

firewall check
---
```
sudo ufw status

# if active
sudo ufw allow from 203.0.113.0 to any port nfs
sudo ufw status

```


client side
===

install
---
```
sudo apt-get update
sudo apt-get install nfs-common
```

mount
---
```
mkdir /data
sudo mount 203.0.113.0:/data /data
```

fstab
---

```
sudo nano /etc/fstab
```
```
203.0.113.0:/data       /data      nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```
