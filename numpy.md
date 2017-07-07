numpy openblas
===

reference
---
- https://docs.scipy.org/doc/numpy-1.10.1/user/install.html


check dependency
```
$ ldd /usr/lib/libblas.so
	linux-vdso.so.1 =>  (0x00007fff91df7000)
	libopenblas.so.0 => /usr/lib/libopenblas.so.0 (0x00007f2d1ca93000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f2d1c78a000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2d1c3c0000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f2d1c1a3000)
	libgfortran.so.3 => /usr/lib/x86_64-linux-gnu/libgfortran.so.3 (0x00007f2d1be78000)
	/lib64/ld-linux-x86-64.so.2 (0x0000560aa8d70000)
	libquadmath.so.0 => /usr/lib/x86_64-linux-gnu/libquadmath.so.0 (0x00007f2d1bc38000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f2d1ba22000)

```

libgfortran.so.3 => gfortran (--fcompiler=gnu95)
- If libg2c.so is a dependency, fortran compiler option to g77
  --fcompiler=gnu


```sh

$ sudo -H pip install cython

# 소스를 적당한 곳에 ..
$ git clone https://github.com/numpy/numpy.git
$ cd numpy
# git tag를 치고 적당한 신뢰할만한 버전을 찾자.
$ git checkout v1.12.1rc1
$ cp site.cfg.example site.cfg
$ nano site.cfg
# 이래 부분 커멘트 풀어주기

#[openblas]
#libraries = openblas
#library_dirs = /opt/OpenBLAS/lib
#include_dirs = /opt/OpenBLAS/include
#runtime_library_dirs = /opt/OpenBLAS/lib
--> change to

[openblas]
libraries = openblas
library_dirs = /usr/lib
include_dirs = /usr/include
runtime_library_dirs = /usr/lib


# openblas settings
$ python setup.py build --fcompiler=gnu95
$ sudo -H pip install .


# 설치 확인
$ cd .. (동일 디렉토리에서 하면안)
$ python
>> import numpy as np
>> np.__config__.show()
```

참고로 numpy 소스빌드를 하면 기본이
`/usr/local/lib/python2.7/dist-packages/numpy` 로 설치된다.


scipy
---

```
sudo -H pip install scipy
```
