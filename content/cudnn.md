cudnn install
===

cudnn 5.1 for cuda8.0

copy files
---

```sh
$ tar zxvf cudnn-8.0-linux-x64-v5.1.tgz
$ cd cuda
$ sudo cp -P lib64/* /usr/local/cuda/lib64/
$ sudo cp include/* /usr/local/cuda/include/
```

env
---
skip this, if cuda-8-0.conf exists in /etc/ld.so.conf.d/

```sh
$ echo "/usr/local/cuda/lib64" | sudo tee -a /etc/ld.so.conf.d/cudnn.conf
$ echo "/usr/local/cuda/extras/CUPTI/lib64" | sudo tee -a /etc/ld.so.conf.d/cudnn.conf
$ sudo ldconfig
```

