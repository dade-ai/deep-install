dlib install
===
    - c++ machine learning algorithms and tools
    - http://dilb.net
https://github.com/davisking/dlib


install
===

```sh
git clone https://github.com/davisking/dlib.git
cd dlib
mkdir build; cd build; cmake .. -DUSE_AVX_INSTRUCTIONS=1; cmake --build .
python setup.py install --yes USE_AVX_INSTRUCTIONS


```


unit test
===

```sh
cd dlib/test
mkdir build
cd build
cmake ..
cmake --build . --config Release
./dtest --runall
```
