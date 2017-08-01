

## 0. NVIDIA 드라이버 설치 
- CUDA를 지원하는 nvidia [GPU확인](https://developer.nvidia.com/cuda-gpus)

- nvidia graphic driver [설치](http://www.nvidia.com/Download/index.aspx?lang=en-us) 
	- 드라이버확인 cat /proc/driver/nvidia/version
	- at latest NVIDIA driver is installed a
	- [Nvidia Driver Instalation](https://goo.gl/kfzWfJ) 

### 0.0 
```
sudo add-apt-repository -y ppa:xorg-edgers/ppa -y
sudo apt-get update
sudo apt-get install nvidia-current


출처: http://moothink.tistory.com/entry/우분투-1404-nvidia-드라이버-설치 [끄적임]
```


### 0.1 For Ubuntu 14.04
```
CUDA_REPO_PKG=http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-repo-ubuntu1404_8.0.61-1_amd64.deb
ML_REPO_PKG=http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1404/x86_64/nvidia-machine-learning-repo-ubuntu1404_4.0-2_amd64.deb
```
### 0.2 For Ubuntu 16.04
```
CUDA_REPO_PKG=http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
ML_REPO_PKG=http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/nvidia-machine-learning-repo-ubuntu1604_1.0.0-1_amd64.deb
```
### 0.3 Install repo packages
```
wget "$CUDA_REPO_PKG" -O /tmp/cuda-repo.deb && sudo dpkg -i /tmp/cuda-repo.deb && rm -f /tmp/cuda-repo.deb
wget "$ML_REPO_PKG" -O /tmp/ml-repo.deb && sudo dpkg -i /tmp/ml-repo.deb && rm -f /tmp/ml-repo.deb
```



## 1. CUDA설치 

### 1.0 사전 작업 
```
sudo apt-get install build-essential
sudo apt-get update
sudo apt-get install linux-generic (VM 사용시 설치) 
```

### 1.1 CUDA by apt-get install 
sudo apt-get update

|Apt-get 설치|
|-|
|apt-get install cuda|
|This will install the latest toolkit  and the latest driver |
|IMPORTANT: Don't install this package if you installed your driver with a run file. The Deb package may not be able to fully uninstall your run file driver installation.|

### 1.1 CUDA 8 for Ubuntu16.04 x86
Network 버젼 : `wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.61-1_amd64.deb`

Local 버젼 : `wget https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64-deb` 1.9G

```
sudo dpkg -i cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda
```

### 1.2 CUDA 8 for Ubuntu14.04 x86

Network 버젼: `wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-repo-ubuntu1404_8.0.61-1_amd64.deb`



```
sudo dpkg -i cuda-repo-ubuntu1404_8.0.61-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda
```

### 1.3 사후 작업 
```
echo "export PATH=/usr/local/cuda/bin/:\$PATH; export LD_LIBRARY_PATH=/usr/local/cuda/lib64/:\$LD_LIBRARY_PATH; " >>~/.bashrc && source ~/.bashrc
```

CUDA설치 확인 : nvcc -v


## 2. cuDNN 설치 

### 2.1 소스코드 설치 
- Download : https://developer.nvidia.com/cudnn ->  cuDNN 5.1 (August 10, 2016) for CUDA 8.0


```bash

wget tar cvzpf cudnn-8.0-linux-x64-v5.1.tgz /
tar cvzpf cudnn-8.0-linux-x64-v5.1.tgz ./

cp -P cuda/include/cudnn.h /usr/local/cuda/include
cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```

### 2.2 CuDNN Ubuntu 16.04

### 2.3 CuDNN Ubuntu 14.04

```
wget http://developer.download.nvidia.com/compute/redist/cudnn/v6.0/cudnn-8.0-linux-x64-v6.0.tgz
sudo cp cuda/include/*.h /usr/local/cuda/include
sudo cp cuda/lib64/*.so* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
sudo apt-get install libcupti-dev
```

에러 : "/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link"
```
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.39 /usr/lib/nvidia-375/libEGL.so.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.39 /usr/lib32/nvidia-375/libEGL.so.1
```
---
