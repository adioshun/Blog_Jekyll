## Pip based Installation

```bash
apt-get install -y python3-pip python3-dev
pip3 install --upgrade pip
```
- OpenCV + jupyter
```bash
pip3 install opencv_python ipython jupyter
```

~~-Tensorflow 설치
```bash
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.1-cp34-cp34m-linux_x86_64.whl
pip3 install --ignore-installed --upgrade $TF_BINARY_URL
```~~(Gitbook으로이동)

- 기타패키지:
```bash
pip3 install scipy matplotlib scikit-learn scikit-image keras pandas
pip3 install moviepy
```

## Anaconda based Installation

- Python 3
```bash
wget https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh
bash Anaconda3-4.4.0-Linux-x86_64.sh 
```
- Python 2
```bash
wget https://repo.continuum.io/archive/Anaconda2-4.4.0-Linux-x86_64.sh
bash Anaconda2-4.4.0-Linux-x86_64.sh 
```

- OpenCv 
```bash
python3 : conda install -c https://conda.binstar.org/menpo opencv3 #conda install -c menpo opencv3=3.2.0
pytbon2 : pip install opencv_python

# apt-get install libgtk2.0-0 #opencv에러시
```
- Jupyter :`conda install -y ipython jupyter`

~~- Tensorflow 설치:`conda install -c conda-forge tensorflow`~~(Gitbook으로이동)

- 기타패키지 : `conda install -y scipy matplotlib scikit-learn scikit-image keras pandas `

> [주피터설정하기](https://github.com/adioshun/Blog_Jekyll/blob/master/2017-07-18_Jupyter_Installation.md)

###### 가상공간설정저장및불러오기

```
#저장하기
source activate CarND-Vehicle-Detection
conda env export > environment.yml

#불러오기
conda env create --file environment.yml --name CarND-Vehicle-Detection
source activate CarND-Vehicle-Detection
```

### GPU버젼 Tensorflow설치 [참고](http://goodtogreate.tistory.com/entry/TensorFlow-GPU-%EB%B2%84%EC%A0%84-%EC%9A%B0%EB%B6%84%ED%88%AC-1604%EC%97%90-%EC%84%A4%EC%B9%98-%ED%95%98%EA%B8%B0)

CUDA installation
- [외부링크참고](https://github.com/adioshun/Blog_Jekyll/blob/master/2017-07-18-CUDA_CuDNN_Installation.md)


tensorflow, opencv, keras, etc. installation

```bash
apt-get install -y libcupti-dev  #에러발생 "/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link"
apt-get install -y python3-pip python3-dev
pip3 install tensorflow-gpu
pip3 install --upgrade pip
```

> libcudnn.so.5: cannot open shared object file 
> - ldconfig -v 로해당라이브러리위치확인
> - LD_LIBRARY_PATH="/usr/local/cuda-8.0/targets/x86_64-linux/lib
> - export LD_LIBRARY_PATH
> - echo $LD_LIBRARY_PATH

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







