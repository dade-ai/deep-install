opencv 3.3 빌드
===

## reference
    - https://github.com/BVLC/caffe/wiki/OpenCV-3.3-Installation-Guide-on-Ubuntu-16.04

## prerequisite

```
apt install -y build-essential cmake git
apt install -y pkg-config unzip ffmpeg qtbase5-dev python-dev python3-dev python-numpy python3-numpy

apt install -y libavcodec-dev libavformat-dev libswscale-dev libxine2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
apt install -y libv4l-dev libtbb-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev
apt install -y libvorbis-dev libxvidcore-dev v4l-utils vtk6
apt install -y liblapacke-dev libopenblas-dev libgdal-dev checkinstall
```

## download source

```
wget https://github.com/opencv/opencv/archive/3.3.0.zip
unzip 3.3.0.zip
```

## build

```
cd opencv-3.3.0
mkdir build
cd build
```

```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D FORCE_VTK=ON \
-D WITH_TBB=ON \
-D WITH_V4L=ON \
-D WITH_QT=ON \
-D WITH_OPENGL=ON \
-D WITH_CUBLAS=ON \
-D WITH_GDAL=ON \
-D WITH_XINE=ON \
-D BUILD_EXAMPLES=0 ..
```

## install

```
sudo make install
sudo /bin/bash -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig
sudo apt update
```

## check cv2.so (for python)

### python2

```sh
$ ll /usr/local/lib/python2.7/dist-packages/cv*
-rw-r--r-- 1 root staff 2988576 Sep 27 11:46 /usr/local/lib/python2.7/dist-packages/cv2.so
```

### python3
```
$ ll /usr/local/lib/python3.5/dist-packages/cv*
-rw-r--r-- 1 root staff 2984688 Sep 27 11:47 /usr/local/lib/python3.5/dist-packages/cv2.cpython-35m-x86_64-linux-gnu.so


```

# 필요하면 *.so파일 복사 혹은 링크

### pyenv
```
ln -s /usr/local/lib/python3.5/dist-packages/cv2.cpython-35m-x86_64-linux-gnu.so  ~/.pyenv/versions/3.5.4/lib/python3.5/cv2.so
```


<!-- cmake -D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_IPP=ON \
-D BUILD_TIFF=ON \
-D BUILD_EXAMPLES=OFF \
-D USE_FFMPEG=YES \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D CUDA_GENERATION=OFF \
-D CUDA_FAST_MATH=0 \
-D WITH_CUBLAS=0 \
-D ENABLE_FAST_MATH=1 \
-D BUILD_PYTHON_SUPPORT=ON \
-D WITH_OPENGL=ON \
-D WITH_TBB=ON \
-D PYTHON2_EXECUTABLE=/usr/bin/python2.7 \
-D PYTHON_INCLUDE_DIR=/usr/include/python2.7/ \
-D PYTHON_INCLUDE_DIR2=/usr/include/x86_64-linux-gnu/python2.7/ \
-D PYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython2.7.so \
-D PYTHON_NUMPY_INCLUDE_DIRS=/usr/local/lib/python2.7/dist-packages/numpy/core/include/ \
-D PYTHON2_NUMPY_INCLUDE_DIRS=/usr/local/lib/python2.7/dist-packages/numpy/core/include/ \
-D WITH_QT=ON -D WITH_OPENGL=ON .. -->
