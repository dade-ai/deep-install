tensorflow r1.1
===

```sh
$ git clone https://github.com/tensorflow/tensorflow
$ cd tensorflow
$ git checkout r1.1

<!-- numpy, dev, pip, wheel -->

sudo apt-get install libcupti-dev
```

```sh
$ ./configure

```

```sh
# $ bazel build --config=opt --config=cuda //tensorflow/tools/pip_package:build_pip_package

$ bazel build -c opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=cuda -k //tensorflow/tools/pip_package:build_pip_package

$ bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
$ sudo -H pip install /tmp/tensorflow_pkg/tensorflow-1.1.0-cp27-cp27mu-linux_x86_64.whl

```
