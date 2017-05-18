
# Packages Installation

## Pip
```bash
apt-get install -y python3-pip python3-dev
pip3 install --upgrade pip
pip3 install opencv_python ipython jupyter scipy matplotlib scikit-learn scikit-image keras pandas
pip3 install moviepy

#Tensorflow 설치
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.1-cp34-cp34m-linux_x86_64.whl
pip3 install --ignore-installed --upgrade $TF_BINARY_URL
```

## Conda
Anaconda3설치
```
wget https://repo.continuum.io/archive/Anaconda3-4.3.0-Linux-x86_64.sh
bash Anaconda3-4.3.0-Linux-x86_64.sh
export PATH="/home/username/anaconda/bin:$PATH" # OR 설치 설정시 pretend하기
```
> [https://www.continuum.io/downloads](https://www.continuum.io/downloads) 에서 최신 버전 확인 가능


```
conda install -c https://conda.binstar.org/menpo opencv3 #conda install -c menpo opencv3=3.2.0
apt-get install libgtk2.0-0 #opencv에러시
conda install -c conda-forge tensorflow
conda install -y scipy matplotlib scikit-learn scikit-image keras pandas ipython jupyter
pip install moviepy
```

### Jupyter설정하기
```bash
jupyter notebook --generate-config
vi /root/.jupyter/jupyter_notebook_config.py
```
`jupyter_notebook_config.py` 설정파일
```
#c = get_config()
c.NotebookApp.ip = '*'  #L158
c.NotebookApp.open_browser = False # L201 원격접속으로 활용할 것이기 때문에 비활성화 시켰다.
c.NotebookApp.port = 8585 # L213 포트를 설정해준다. 기본포트로 8888이 자동 배정된다.
c.NotebookApp.password = 'sha1:a8dee43a3a44:b18f1ad149a60efb4838da44cf127985d64a5e70' # L210 python 실행후 from notebook.auth import passwd; passwd\(\)
c.NotebookApp.notebook_dir = '/home/adioshun/Jupyter' # L195 기본 디렉터리를 지정시켜준다.
```

jupyter 테마: [#1](https://github.com/powerpak/jupyter-dark-theme), [#2](http://haanjack.github.io/jupyter/theme/2016/03/08/jupyter-theme.html), [#3](https://github.com/dunovank/jupyter-themes)



## 기타 필요 툴

### Jupyter Lab설치


Unonffical
```
# you will need jupyter notebook >= v4.2
pip3 install jupyterlab
jupyter serverextension enable --py jupyterlab --sys-prefix
jupyter lab
```
### Jupyter Extension설치
##### Official:[ref](https://docs.continuum.io/anaconda/jupyter-notebook-extensions)
```
conda install nb_conda -c conda-forge
# conda install nb_conda
# conda install -c anaconda-nb-extensions nbpresent

```
> UnsatisfiableError: [solved](https://github.com/ContinuumIO/anaconda-issues/issues/1423)


##### Unofficial:[ref](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html)
```
conda install -c conda-forge jupyter_contrib_nbextensions
#pip install https://github.com/ipython-contrib/jupyter_contrib_nbextensions/tarball/master
jupyter contrib nbextension install --user
```
[참고](https://github.com/ipython-contrib/jupyter_contrib_nbextensions)

### Jupyter 커널추가
```
conda create -n py36 python=3.6
source activate py36
conda install notebook ipykernel
ipython kernel install --user
```

## Python GUI Debuger
```bash
sudo apt-get install python-pudb
python -m pudb.run foo.py
```

> 참고 : [[파이썬] PUDB 콘솔 디버거](http://egloos.zum.com/mcchae/v/10918232)


## GPU Monitor 

```
apt-get install nmon
```

---
# 리눅스 설치후
## zsh변경

```
sudo apt-get install zsh
chsh -s `which zsh`
sudo curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
> zsh가 느리게 시작 할때 `sudo rm -rf /private/var/log/asl*.as`

[참고](https://nolboo.kim/blog/2015/08/21/oh-my-zsh/)

## TMUX
[설치](http://code4rain.tistory.com/1169527180), [자동설치 스크립트](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=tmux+install+script)

```
apt-get install tmux
tmux new -s <원하는 이름>
```

	- Ctrl+j를 누른 후에 | 를 누르면 좌우로 분할되고
	- Ctrl+j를 누른 후에 - 를 누르면 상하로 분할됩니다.,
	- 미리 창 분활 해놓기 : [Tmuxinator](https://github.com/tmuxinator/tmuxinator)

출처: http://code4rain.tistory.com/1169527180 [codeRain's Life Blog]

## 원격 접속

#### GUI Desttop 환경설치
```
$ sudo apt-get install aptitude tasksel
$ sudo tasksel install gnome-desktop --new-install
```


### 원격 접속 툴
```
apt-get install xrdp
/etc/xrdp/xrdp.ini

[xrdp1]
name=Active Local Login
lib=libvnc.so
username=
password=ask
ip=127.0.0.1
port=5900

service xrdp restart
```

### VNC
Server side
```
sudo apt-get install -y tightvncserver
vncserver

```
vim .vnc/xstartup
```bash
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

metacity &
gnome-settings-daemon &
gnome-panel &

client side
```
nc localhost 5901 #port open check

```

### X11 Forwarding
client Side
```
# ~/.ssh/config file have these lines:
Host *
  ForwardAgent yes
  ForwardX11 yes
```  

Server Side 
```
sudo apt-get install xauth
vi /etc/ssh/sshd_config  # X11 관련 3줄 Uncomment
service sshd restart

$ echo $DISPLAY  # export DISPLAY=localhost:10.0
ls -l ~/.Xauthority # Check user ID
xclock # it will show clock
```

make connection
```
ssh -v -X -C xxx@xxx
sudo apt-get insatll spyder3 #conda install spyder
```

> No Qt bindings could be found : `pip3 install pyqt5`

> libGL.so.1: cannot open shared object file: `apt-get --reinstall install libgl1-mesa-glx`

> libsmime3.so: cannot open shared object file: `apt-get install libnss3-dbg`

> libasound.so.2: cannot open shared object file: `sudo apt-get install libasound2`

> libXtst.so.6: cannot open shared object file: `sudo apt-get install libxtst6`

### Chrome RND
http://timbot-inc.blogspot.com/2015/11/cloud-workstation-howto-chromebook.html

# Tip

## 공간 환보
apt-get clean

pip clean?


###### 가상공간설정저장및불러오기

```
#저장하기
source activate CarND-Vehicle-Detection
conda env export > environment.yml

#불러오기
conda env create --file environment.yml --name CarND-Vehicle-Detection
source activate CarND-Vehicle-Detection
```


#### Spyder remote kernel connection
1. In jupyter run `%connect_info'
2. save it as `kernel.json`
3. Run spyder -

참고 : http://stackoverflow.com/questions/39007571/running-jupyter-with-multiple-python-and-ipython-paths

#### OpenAI Gym

```
sudo apt-get install -y python-numpy python-dev cmake zlib1g-dev libjpeg-dev 

xvfb libav-tools xorg-dev python-opengl libboost-all-dev libsdl2-dev swig

sudo -H pip install gym

sudo -H pip install gym[atari]

```
 



### GPU버젼 Tensorflow설치

[참고](http://goodtogreate.tistory.com/entry/TensorFlow-GPU-%EB%B2%84%EC%A0%84-%EC%9A%B0%EB%B6%84%ED%88%AC-1604%EC%97%90-%EC%84%A4%EC%B9%98-%ED%95%98%EA%B8%B0)

CUDA installation

```bash
apt-get update
apt-get install wget vim
wget https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64-deb #1.9G
dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64-deb
apt-get update
apt-get install cuda # 3699M
apt-get install openssh-client #scp
```

cudaa installation
- Download : https://developer.nvidia.com/cudnn ->  cuDNN 5.1 (August 10, 2016) for CUDA 8.0


```bash

wget tar cvzpf cudnn-8.0-linux-x64-v5.1.tgz /
tar cvzpf cudnn-8.0-linux-x64-v5.1.tgz ./

cp -P cuda/include/cudnn.h /usr/local/cuda/include
cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

```

tensorflow, opencv, keras, etc. installation

```bash
apt-get install -y libcupti-dev  #에러발생 "/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link"

apt-get install -y python3-pip python3-dev

pip3 install tensorflow-gpu

pip3 install opencv_python ipython jupyter

pip3 install --upgrade pip

pip3 install -y scipy matplotlib scikit-learn scikit-image keras pandas

```

> libcudnn.so.5: cannot open shared object file 

> ldconfig -v 로해당라이브러리위치확인

> LD_LIBRARY_PATH="/usr/local/cuda-8.0/targets/x86_64-linux/lib

> export LD_LIBRARY_PATH

> echo $LD_LIBRARY_PATH




### R 설치

```bash
sudo apt-get update
sudo apt-get install r-base
```
> 윈도우용 설치 : [r-project](https://cloud.r-project.org/bin/windows/base/)

#### 2. R-Studio 설치

```bash
$ sudo apt-get install gdebi-core
$ wget https://download2.rstudio.org/rstudio-server-1.0.136-amd64.deb
$ sudo gdebi rstudio-server-1.0.136-amd64.deb
```
> 최신버젼 확인 [R Studio](www.rstudio.com/products/rstudio/download/)

#### 2. Python 용 R 설치 \(/w conda\)

```bash
conda install -c r r-irkernel
conda install -c r r-essentials
```

###### ipython에서 R 패지키 설치 방법 \(R 콘솔에서 실행??\)

sudo apt-get install libcurl4-openssl-dev
sudo apt-get install libssl-dev
```
#R쉘진입
install.packages(c('repr', 'IRdisplay', 'evaluate', 'crayon', 'pbdZMQ', 'devtools', 'uuid', 'digest'))
devtools::install_github('IRkernel/IRkernel')
IRkernel::installspec()
```

> 패키지설치시: install.packages("ldavis", "/home/user/anaconda3/lib/R/library")
> [메뉴얼필독](https://www.r-bloggers.com/jupyter-and-r-markdown-notebooks-with-r/amp/)
