gmov
===

http://www.cs.cmu.edu/~junggon/tools/gmov.html

wget http://www.cs.cmu.edu/~junggon/tools/gmov-r15.zip
unzip gmov-r15.zip
cd gmov-r15
make install_dependencies_ubuntu
make

```
Linux (Tested with Ubuntu)
Extract the zipped source code to a directory and move in to the directory in the Terminal.
>>make install_dependencies_ubuntu (for installing necessary prerequisites such as cmake and freeglut)
>>make (for compiling the source code)
>>./gmov -bvh data/test.bvh (to run gmov and open a bvh file)
```


