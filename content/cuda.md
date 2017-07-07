nvidia driver and cudatoolkit
===

nvida driver
---
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```

Now, find Software & Updates under System Settings and select the required driver version form the Additional Drivers tab, select the driver and click Apply Changes. Restart and Enjoy!

cudatoolkit
---

설치 순서는 ...
------------
- https://developer.nvidia.com/cuda-toolkit 가서
- `linux`, `x86_64`, `ubuntu`, `14.04`, `deb(local)` 선택
- 다운로드
- 친절하게도 설치 명령어를 보여준다. 시키는 데로 하자.

현재 cuda 7.5 기준이고, 위 사항이 설치환경이 맞다면 아래 명령어를 줄줄이 실행시키면 됩니다.
터미널 작업만 할수 있는 환경이라면 아래가 편하겠죠?

```sh
# 1.9 기가바이트나 됩니다. 좀 걸려요~
$ wget http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
$ sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
$ sudo apt-get update
$ sudo apt-get install cuda
```


환경 설정
--------
라이브러리
```sh
# cuda 툴킷이 나중에 버전이 올라간다거나 하면, 다른 환경이 바뀌면 불편할 테니.
# cuda-7.5 에 소프트링크를 잡아주고 설정하자.
# 폴더 소프트링크 하나 만들어주고 자동으로 만들어주네요.
# $ sudo ln -s /usr/local/cuda-7.5 /usr/local/cuda

# 라이브러리 설정을 잡아주자.
# 라이브러리 path 7.0, 7.5 두줄 설정이 들어가게 된다.
$ echo "/usr/local/cuda/lib64" | sudo tee -a /etc/ld.so.conf.d/cuda.conf
$ sudo ldconfig

```
쿠다 환경변수

```sh
# 쿠다환경변수 저장
$ sudo nano /etc/profile.d/cuda.sh
# 다음을 쓰고 저장
export CUDA_HOME=/usr/local/cuda
export PATH=${PATH}:${CUDA_HOME}/bin

# 적용
$ source /etc/profile.d/cuda.sh

```
