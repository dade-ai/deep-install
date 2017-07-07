opencv 3.2 install
===

important
! deactivate torch7 in .bashrc if exist

prerequisite
---

```sh
# python-numpy removed
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
sudo apt-get install qt5-default
sudo apt-get install libgflags-dev libgoogle-glog-dev libavresample-dev libgphoto2-dev
```
or

```
sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config   libavcodec-dev libavformat-dev libswscale-dev python-dev libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev qt5-default libavresample-dev libgphoto2-dev
```


소스코드 받기
---

```sh
$ git clone --depth=1 https://github.com/opencv/opencv.git
$ git clone --depth=1 https://github.com/opencv/opencv_contrib.git
$ git clone --depth=1 https://github.com/opencv/opencv_extra.git
$ cd opencv && mkdir build && cd build
```

build settings
---


```sh
cmake -D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_IPP=ON \
-D BUILD_TIFF=ON \
-D BUILD_EXAMPLES=OFF \
-D USE_FFMPEG=YES \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D CUDA_GENERATION=Auto -D CUDA_ARCH_BIN=6.1 -D CUDA_ARCH_PTX=6.1 \
-D CUDA_FAST_MATH=1 -D WITH_CUBLAS=1 \
-D ENABLE_FAST_MATH=1 \
-D BUILD_PYTHON_SUPPORT=ON \
-D WITH_OPENGL=ON \
-D WITH_TBB=ON \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules/ \
-D OPENCV_TEST_DATA_PATH=../../opencv_extra/testdata/ \
-D PYTHON2_EXECUTABLE=/usr/bin/python2.7 \
-D PYTHON_INCLUDE_DIR=/usr/include/python2.7/ \
-D PYTHON_INCLUDE_DIR2=/usr/include/x86_64-linux-gnu/python2.7/ \
-D PYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython2.7.so \
-D PYTHON_NUMPY_INCLUDE_DIRS=/usr/local/lib/python2.7/dist-packages/numpy/core/include/ \
-D PYTHON2_NUMPY_INCLUDE_DIRS=/usr/local/lib/python2.7/dist-packages/numpy/core/include/ \
-D WITH_QT=ON -D WITH_OPENGL=ON ..

```


build and install
---

```sh
$ make -j4
$ sudo make install
$ sudo cp lib/cv2.so /usr/local/lib/python2.7/dist-packages/cv2.so
$ sudo cp 3rdparty/ippicv/ippicv_lnx/lib/intel64/libippicv.a /usr/local/lib/
$ cd ..
# $ sudo cp 3rdparty/ippicv/unpack/ippicv_lnx/lib/intel64/libippicv.a /usr/local/lib/
# cat /etc/ld.so.conf.d/opencv.conf
$ echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf.d/opencv.conf
$ sudo ldconfig
```


test
---
```sh
$ ipython
> import cv2

```
