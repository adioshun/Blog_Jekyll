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

## Visdom for PyTorch Visualization
```bash
pip install visdom
python -m visdom.server
```
Open `http://localhost:8097`

> 출처 : [Visdom github](https://github.com/facebookresearch/visdom)

###### [Error] unsupported GNU version! gcc versions later than 5 are not supported!
```bash 
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install gcc-4.9
sudo apt-get install g++-4.9

sudo rm /usr/bin/g++
sudo ln -s /usr/bin/g++-4.9 /usr/bin/g++

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.9 /usr/bin/gcc
```
