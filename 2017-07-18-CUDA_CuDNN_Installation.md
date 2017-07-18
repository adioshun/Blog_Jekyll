> [Nvidia Driver Instalation](http://moothink.tistory.com/entry/%EC%9A%B0%EB%B6%84%ED%88%AC-1404-nvidia-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98)
> 드라이버확인 cat /proc/driver/nvidia/version

# Install CUDA Ubuntu 16.04
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

---
# Install CUDA Ubuntu 14.04
```bash
sudo apt-get install build-essential
sudo apt-get update
sudo apt-get install linux-generic (VM 사용시 설치) 
sudo wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-repo-ubuntu1404_8.0.61-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1404_8.0.61-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda
echo "export PATH=/usr/local/cuda/bin/:\$PATH; export LD_LIBRARY_PATH=/usr/local/cuda/lib64/:\$LD_LIBRARY_PATH; " >>~/.bashrc && source ~/.bashrc
```
# Install CuDNN Ubuntu 14.04
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
