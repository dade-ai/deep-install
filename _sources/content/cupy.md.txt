cupy
===

- https://docs-cupy.chainer.org/en/stable/install.html

trouble-shooting
---
- `libcuda.so` 못찾을 때

apt update
apt install software-properties-common python-software-properties


```sh
add-apt-repository ppa:graphics-drivers/ppa
apt update
apt install nvidia-378-dev  # 적당한것.
ll /usr/local/cuda/lib64/libcuda*
pip install cupy
```
