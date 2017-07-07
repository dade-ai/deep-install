cgkit install
===

problems in linux

prerequisite
---
- libboost, libboost-python
- pygame
- vpython


```sh
$ sudo apt install scons libboost-dev libboost-python-dev
$ sudo -H pip install pygame
$ sudo -H pip install vpython
$ 
$ # download from (sourceforge)[https://sourceforge.net/projects/cgkit]
$ wget http://jaist.dl.sourceforge.net/project/cgkit/cgkit/cgkit-2.0.0/cgkit-2.0.0-py2k.zip
$ 
$ unzip cgkit-2.0.0-py2k.zip
$ 
$ cd cgkit-2.0.0/supportlib
$ scons
$ cd ..
$ python setup.py build
$ sudo python setup.py install

```
