opencv 3.1 install
===


prerequisite
---

```sh
# python-numpy removed
sudo apt-get install build-essential 
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev 
sudo apt-get install python-dev libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
sudo apt-get install qt5-default

```


소스코드 받기
---

```sh
$ git clone https://github.com/opencv/opencv.git
$ git clone https://github.com/opencv/opencv_contrib.git
$ cd opencv && mkdir build && cd build
```


build settings
---

아래 옵션 중
-D OPENCV_EXTRA_MODULES_PATH=/home/dade/src/opencv_contrib/modules/ \
에 자신의 opencv_contrib path 적어줄 것.

```

```sh
cmake -D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_IPP=ON \
-D BUILD_TIFF=ON \
-D BUILD_EXAMPLES=OFF \
-D USE_FFMPEG=YES \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D CUDA_GENERATION=OFF \
-D CUDA_FAST_MATH=0 -D WITH_CUBLAS=0 \
-D ENABLE_FAST_MATH=1 \
-D BUILD_PYTHON_SUPPORT=ON \
-D MATLAB_ROOT_DIR=/usr/local/MATLAB/MATLAB_Production_Server/R2015a/ \
-D WITH_OPENGL=ON \
-D WITH_TBB=ON \
-D OPENCV_EXTRA_MODULES_PATH=/home/dade/src/opencv_contrib/modules/ \
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
$ cd ..
$ sudo cp 3rdparty/ippicv/unpack/ippicv_lnx/lib/intel64/libippicv.a /usr/local/lib/
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


