> 출처 : http://www.whydsp.org/337

공식 매뉴얼 참조
http://caffe.berkeleyvision.org/installation.html#prerequisites
http://caffe.berkeleyvision.org/install_apt.html

설치 환경 (Google 클라우드)
- OS: Ubuntu 14.04 LTS 
- GPU


## 1. General Dependencies
```
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
sudo apt-get install --no-install-recommends libboost-all-dev
```

## 2. CUDA 설치
https://github.com/adioshun/Blog_Jekyll/blob/master/2017-07-18-CUDA_CuDNN_Installation.md

## 3. BLAS 설치
여러 종류가 있지만 ATLAS를 설치하면 뒤에서 설정에 편리
```
sudo apt-get install libatlas-base-dev 
```

## 4. Python 설치 (Anaconda2 추천)
```
wget https://repo.continuum.io/archive/Anaconda2-4.4.0-Linux-x86_64.sh
bash Anaconda2-4.4.0-Linux-x86_64.sh 
```

## 5. Remaining dependencies, 14.04
```
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
```

## 6. OpenCV 설치 

OpenCV3는Dependency Error로Opencv2설치: `pip install opencv_python`


## 7. Caffe 설치
- git clone, Makefile.config 파일복사
```bash 
git clone https://github.com/BVLC/caffe.git  
cd caffe
cp Makefile.config.example Makefile.config
```
- Makefile.config 문서 수정 (https://github.com/BVLC/caffe/pull/1667참조)
```
USE_CUDNN := 1

WITH_PYTHON_LAYER := 1
USE_PKG_CONFIG := 1

#(OpenCV 3.x 사용 시)
#OPENCV_VERSION := 3

# (Anaconda 설치 시 python path는 주석처리 하고)
## Anaconda2
ANACONDA_HOME:=$(HOME)/anaconda2
PYTHON_INCLUDE:=$(ANACONDA_HOME)/include \
  $(ANACONDA_HOME)/include/python2.7 \
  $(ANACONDA_HOME)/lib/python2.7/site-packages/numpy/core/include \
PYTHON_LIB := $(ANACONDA_HOME)/lib
```

## 8. Compile 
```
make clean
make all  (여기서 error가 많이 발생. 앞의 조건들 충족했는지 확인!)
make test
sudo vi ~/.bashrc

bashrc 문서 맨 아래에 다음을 추가
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/home/hjlim99/anaconda2/lib"

make runtest
```

## 9. pycaffe
```
make pycaffe
sudo gedit ~/.bashrc

bashrc 문서 맨 아래에 다음을 추가
PYTHONPATH=/home/hjlim99/caffe/python:$PYTHONPATH
```

## 10. distribute 실행
```
make distribute
```

## 설치확인
```
cd (caffe home)/python
python
import caffe
```

> [Tutorial](http://caffe.berkeleyvision.org/gathered/examples/mnist.html)



[Caffe에서 요구하는 라이브러리 설치 목록] 
Cython>=0.19.2
numpy>=1.7.1
scipy>=0.13.2
scikit-image>=0.9.3
matplotlib>=1.3.1
ipython>=3.0.0
h5py>=2.2.0
leveldb>=0.191
networkx>=1.8.1
nose>=1.3.0
pandas>=0.12.0
python-dateutil>=1.4,<2
protobuf>=2.5.0
python-gflags>=2.0
pyyaml>=3.10
Pillow>=2.3.0
six>=1.1.0



---
에러처리

cannot open shared object file lib hdf5_hl.so.10
- cd /usr/lib/x86_64-linux-gnu
- sudo ln -s libhdf5_hl.so.7 libhdf5_hl.so.10
- sudo ln -s libhdf5.so.7 libhdf5.so.10

Cannot create Cublas handle. Cublas won't be available.


(ffmpeg 에러 시)
>> sudo add-apt-repository ppa:mc3man/trusty-media
>> sudo apt-get update
>> sudo apt-get install ffmpeg gstreamer0.1.0-ffmpeg

(pyconfig.h 에러 시)
>> make clean
>> export CPLUS_INCLUDE_PATH=/usr/include/python2.7
>> make all –j8


출처: http://www.whydsp.org/337 [모두의연구소 기술블로그]