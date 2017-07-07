pyenv 설치
===

설치
---

```sh
$ curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```

환경설정
---
```sh
$ nano .bashrc
export PYENV_ROOT=$HOME/.pyenv
export PATH=$PYENV_ROOT/bin:$PATH
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

```

추가 플러그인 설치
---
```sh
$ git clone https://github.com/yyuu/pyenv-pip-rehash.git ~/.pyenv/plugins/pyenv-pip-rehash
```

쉘 리스타트
---
```
$ exec $SHELL
```

python 3.5.0 설치
---
```sh
# $ pyenv install 3.5.0
# 대신 몇가지 빌드 플래그를 추가한다.
$ env CFLAGS="-O3 -fPIC" CONFIGURE_OPTS="--enable-shared" pyenv install 3.5.0
```

python 버전 선택
---
```sh
# pyenv 사용법은 생략한다.
$ pyenv global 3.5.0
```

잘 설치되었는지 확인
```sh
$ python --version
Python 3.5.0
$ which python
$ which pip
```

pip 업그레이드
---
```sh
# 패키지 빌드 캐시 폴더 생성
$ mkdir ~/.pyenv/cache
# 앞으로 sudo는 붙이지 않는다.
$ pip install -U pip
```

python build requirements
---
```sh
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils
```

ipython
---

```sh
$ pip install jupyter
```
qtconsole이 필요하다면 pyside 3.5 설치가 pip 에러 발생
```sh
$ sudo apt-get install libqt4-dev libphonon-dev libxml2-dev libxslt1-dev qtmobility-dev libqtwebkit-dev libshiboken-dev
# sudo apt-get install build-essential git cmake qt5-default libxml2 libxslt
# $ wget https://pypi.python.org/packages/source/P/PySide/PySide-1.2.4.tar.gz
# $ tar -xvzf PySide-1.2.4.tar.gz
# $ cd PySide-1.2.4
$ git clone https://github.com/PySide/pyside-setup.git pyside-setup
# setup.py 편집 3.5 서포트 추가
$ python setup.py build --jobs=8
$ python setup.py install
$ pip install pygments pyzmq

```
