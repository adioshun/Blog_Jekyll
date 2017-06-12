# Packages Installation

## Pip
```bash
apt-get install -y python3-pip python3-dev
pip3 install --upgrade pip

#OpenCV + jupyter
pip3 install opencv_python ipython jupyter 

#Tensorflow 설치
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.1-cp34-cp34m-linux_x86_64.whl
pip3 install --ignore-installed --upgrade $TF_BINARY_URL

pip3 install scipy matplotlib scikit-learn scikit-image keras pandas
pip3 install moviepy

```

## Conda
```bash
# OpenCv 
python3 : conda install -c https://conda.binstar.org/menpo opencv3 #conda install -c menpo opencv3=3.2.0
pytbon2 : pip install opencv_python

# apt-get install libgtk2.0-0 #opencv에러시



# Jupyter
conda install -y ipython jupyter

#Tensorflow 설치
conda install -c conda-forge tensorflow

conda install -y scipy matplotlib scikit-learn scikit-image keras pandas 
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
# conda2 OR 3 install 

conda create -n pyton3 python=3

jupyter kernelspec list #설치된 커널 확인 
conda install notebook ipykernel
ipython kernel install --user
```

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
# Debuger 

GUI Debuger
```bash
sudo apt-get install python-pudb
python -m pudb.run foo.py
```

> 참고 : [[파이썬] PUDB 콘솔 디버거](http://egloos.zum.com/mcchae/v/10918232)

better-exceptions
```bash
pip install better_exceptions
import better_exceptions
```
> 참고 : https://github.com/Qix-/better-exceptions

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

# PyTorch installation 

```bash 
# conda (linux, osx)
$ conda install pytorch torchvision -c soumith

# pip : linux + python2.7 + cuda7.5
$ pip install https://s3.amazonaws.com/pytorch/whl/cu75/torch-0.1.6.post22-cp27-cp27mu-linux_x86_64.whl 
$ pip install torchvision

# pip : linux + python2.7 + cuda8.0
$ pip install https://s3.amazonaws.com/pytorch/whl/cu80/torch-0.1.6.post22-cp27-cp27mu-linux_x86_64.whl 
$ pip install torchvision

# pip : linux + python3.5 + cuda7.5
$ pip install https://s3.amazonaws.com/pytorch/whl/cu75/torch-0.1.6.post22-cp35-cp35m-linux_x86_64.whl
$ pip install torchvision

# pip : linux + python3.5 + cuda8.0
$ pip install https://s3.amazonaws.com/pytorch/whl/cu80/torch-0.1.6.post22-cp35-cp35m-linux_x86_64.whl
$ pip install torchvision
```
