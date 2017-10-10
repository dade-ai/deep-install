# OpenCV3 install (OSX)

## requirement
- homebrew
- xcode `app store`
- python (homebrew) `brew install python`
- numpy `pip install numpy`

## xcode install

```
# install from app store
$ sudo xcodebuild -license
$ sudo xcode-select --install
```

이런 에러가 뜨면
```
xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance #569
```
`$ sudo xcode-select -s /Applications/Xcode.app/Contents/Developer` 실행
- https://github.com/nodejs/node-gyp/issues/569


## build env

```
$ brew install cmake pkg-config
$ brew install jpeg libpng libtiff openexr
$ brew install eigen tbb
```

## git clone

```sh
$ git clone --depth 1 https://github.com/opencv/opencv
$ git clone --depth 1 https://github.com/opencv/opencv_contrib
```

## configure

```sh
$ cd ~/opencv
$ mkdir build
$ cd build
```

## PYTHON2_LIBRARY
```
$ $ ls /usr/local/Cellar/python/2.7.*/Frameworks/Python.framework/Versions/2.7/lib/python2.7/config/libpython2.7.dylib
```

## PYTHON2_INCLUDE_DIR
```
$ ls -d /usr/local/Cellar/python/2.7.*/Frameworks/Python.framework/Versions/2.7/include/python2.7/
```

```sh
$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
    -D PYTHON2_LIBRARY=/usr/local/Cellar/python/2.7.13/Frameworks/Python.framework/Versions/2.7/lib/python2.7/config/libpython2.7.dylib \
    -D PYTHON2_INCLUDE_DIR=/usr/local/Cellar/python/2.7.13/Frameworks/Python.framework/Versions/2.7/include/python2.7/ \
    -D PYTHON2_EXECUTABLE=/usr/local/bin/python \
    -D BUILD_opencv_python2=ON \
    -D BUILD_opencv_python3=OFF \
    -D INSTALL_PYTHON_EXAMPLES=OFF \
    -D INSTALL_C_EXAMPLES=OFF \
    -D BUILD_EXAMPLES=ON ..
```

## build and install

```
$ make -j4
$ sudo make install

```



## reference
- http://www.pyimagesearch.com/2016/11/28/macos-install-opencv-3-and-python-2-7/
