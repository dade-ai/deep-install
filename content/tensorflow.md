tensorflow
===

현재 release 1.2 기준

build
---

```sh
<!-- numpy, dev, pip, wheel -->

sudo apt-get install libcupti-dev
sudo -H pip install --upgrade \
  https://storage.googleapis.com/tensorflow/linux/cpu/protobuf-3.1.0-cp27-none-linux_x86_64.whl


```

```sh
$ git clone https://github.com/tensorflow/tensorflow
$ cd tensorflow
# $ git checkout v1.2.1
$ ./configure

```

```sh
# $ bazel build --config=opt --config=cuda //tensorflow/tools/pip_package:build_pip_package

$ bazel build -c opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=cuda -k //tensorflow/tools/pip_package:build_pip_package

$ bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
$ sudo -H pip install /tmp/tensorflow_pkg/tensorflow-1.2.1-cp27-cp27mu-linux_x86_64.whl

```

test
---
```bash
$ cd ..
$ python -c "import tensorflow as tf; s=tf.InteractiveSession(); print(tf.ones((3,2)).eval())"

```
