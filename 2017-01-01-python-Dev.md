# Python Setup

## 1. Pip based Installation

- pip 설치및업그레이드
```bash
apt-get install -y python3-pip python3-dev
pip3 install --upgrade pip
```
- OpenCV + jupyter
```bash
pip3 install opencv_python ipython jupyter
```

-Tensorflow 설치
```bash
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.1-cp34-cp34m-linux_x86_64.whl
pip3 install --ignore-installed --upgrade $TF_BINARY_URL
```

-Tensorflow(GPU) 설치

> CUDA installation : [외부링크참고](https://github.com/adioshun/Blog_Jekyll/blob/master/2017-07-18-CUDA_CuDNN_Installation.md)

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

- 기타패키지:
```bash
pip3 install scipy matplotlib scikit-learn scikit-image keras pandas
pip3 install moviepy
```






## 2. Anaconda based Installation

- Anaconda설치
```bash
# Python 3
wget https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh
bash Anaconda3-4.4.0-Linux-x86_64.sh 

# Python 2
wget https://repo.continuum.io/archive/Anaconda2-4.4.0-Linux-x86_64.sh
bash Anaconda2-4.4.0-Linux-x86_64.sh 
```

- OpenCv 
```bash
# python3
conda install -c https://conda.binstar.org/menpo opencv3 #conda install -c menpo opencv3=3.2.0

#pytbon2
pip install opencv_python

# apt-get install libgtk2.0-0 #opencv에러시
```
- Jupyter :`conda install -y ipython jupyter`

- Tensorflow 설치:`conda install -c conda-forge tensorflow`

- 기타패키지 : `conda install -y scipy matplotlib scikit-learn scikit-image keras pandas `

> [주피터설정하기](https://github.com/adioshun/Blog_Jekyll/blob/master/2017-07-18_Jupyter_setup.md)


--- 

###### [Tip] 가상공간설정저장및불러오기

```
#저장하기
source activate CarND-Vehicle-Detection
conda env export > environment.yml

#불러오기
conda env create --file environment.yml --name CarND-Vehicle-Detection
source activate CarND-Vehicle-Detection
```

```bash
pip install virtualenv
virtualenv -p /usr/bin/python2.7 my_project
source my_project/bin/activate
```


###### [Tip] requirement.txt 파일이용하여한번에설치하기

```
Cython>=0.19.2
numpy>=1.7.1
...
pyyaml>=3.10
Pillow>=2.3.0
```

- pip :`for req in $(cat requirements.txt); do pip install $req | cut -d ">" -f1; done`
- conda : `while read requirement; do conda install --yes $requirement; done < requirements.txt`

출처: http://goodtogreate.tistory.com/entry/FasterRCNN-Install-on-Ubuntu-1604GTX1080-CUDA-80cuDNN-51 [GOOD to GREAT]


###### [Tip] [requirement.yml](https://github.com/datitran/Object-Detector-App/blob/master/environment.yml) 파일이용하여 한번에 가상환경 설치하기


```
name: object-detection
channels: !!python/tuple
- menpo
- defaults
dependencies:
- freetype=2.5.5=2
- jbig=2.1=0
- pip:
  - backports.weakref==1.0rc1
prefix: /Users/datitran/anaconda/envs/object-detection
```

- `conda env create -f environment.yml`



#### Spyder remote kernel connection
1. In jupyter run `%connect_info'
2. save it as `kernel.json`
3. Run spyder -

참고 : http://stackoverflow.com/questions/39007571/running-jupyter-with-multiple-python-and-ipython-paths






