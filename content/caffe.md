caffe install
===

- ubuntu 16.04 기준 install
- bvlc 기준


dependencies
---

- general
```sh
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler libopenblas-dev
sudo apt-get install --no-install-recommends libboost-all-dev
sudo ldconfig
```

- cuda : `CUDA 8 is required on Ubuntu 16.04.`

`
- blas
- python
```sh
sudo apt-get install the python-dev
```
- [opencv](opencv.md)

compilation
---

- download
```sh
git clone --depth=1 https://github.com/BVLC/caffe.git
cd caffe
```
- compile
```sh
cp Makefile.config.example Makefile.config
# Adjust Makefile.config (for example, if using Anaconda Python, or if cuDNN is desired)
vi Makefile.config
```
- Makefile.config uncommented parts
```sh
# example
PYTHON_INCLUDE := /usr/include/python2.7 \
		/usr/local/lib/python2.7/dist-packages/numpy/core/include
WITH_PYTHON_LAYER := 1
USE_CUDNN := 1
USE_OPENCV := 1
USE_LEVELDB := 1
USE_LMDBDB := 0
OPENCV_VERSION := 3
# open for OpenBlas
BLAS := open
INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/
```

- compile
```sh
make all -j 4
make pycaffe
# make test
# make runtest
make distribute
```
- after compile
```sh
$ sudo cp -r distribute /opt/caffe
$ sudo sh -c "echo '/opt/caffe/lib' > /etc/ld.so.conf.d/caffe.conf"
$ sudo ldconfig
```

- python path, path 잡아주기
```sh
$ sudo nano /etc/profile.d/caffe.sh
#  아래 저장하고 나온다.
export CAFFE_HOME=/opt/caffe
export PYTHONPATH=${PYTHONPATH}:${CAFFE_HOME}/python
export PATH=${PATH}:${CAFFE_HOME}/build/tools
```

$ source /etc/profile.d/caffe.sh
