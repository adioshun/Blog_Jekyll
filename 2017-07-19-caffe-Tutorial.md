## 실습 

Datasets
- cd $CAFFE_ROOT
- ./data/mnist/get_mnist.sh 
	- 파일 다운로드 : t10k-images-idx3-ubyte, t10k-labels-idx1-ubyte,  train-images-idx3-ubyte,  train-labels-idx1-ubyte
- ./examples/mnist/create_mnist.sh
	- 파일 변환/생성 : mnist_test_lmdb, mnist_train_lmdb
실행
- ./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt
> CPU 버전일 경우 lenet_solver.prototxt 의 solver mode를 CPU로 변경

로그파일 
- /tmp 

Training/Testing을 위해 보통 두 가지 파일을 정의함
- Solver 정보를 담은 파일
  - Gradient update를 어떻게 시킬 것인가에 대한 정보를 담음
  - learning rate, weight decay 등의 parameter가 정의됨
  - Test interval, snapshot 횟수 등 정의
- Network 구조 정보를 담은 파일 : 실제 CNN 구조 정의
	- Net
    	- Caffe에서 CNN (혹은 RNN 또는 일반 NN) 네트워크는 ‘Net’이라는 구조로 정의됨
        - Net은 여러 개의 Layer 들이 연결된 구조 Directed Acyclic Graph(DAG) 구조만 만족하면 어떤 형태이든 training이 가능함
	- Layer
    	- CNN의 한 ‘층＇을 뜻함
        - Convolution을 하는 Layer, Pooling을 하는 Layer, activation function을 통과하는 layer, input data layer, Loss를 계산하는 layer 등이 있음
        - 소스코드에는 각 layer별로 Forward propagation, Backward propagation 방법이 CPU/GPU 버전별로 구현되어 있음
     - Blob
     	-  Layer를 통과하는 데이터 덩어리
        - Image의 경우 주로 NxCxHxW 의 4차원 데이터가 사용됨 (N : Batch size, C :Channel Size, W : width, H : height)
        
- 확장자가 .prototxt 파일로 만들어야 함
- Google [Protocol Buffers](https://developers.google.com/protocol-buffers/) 기반 

---

##### lenet_train_test.prototxt
```bahs 
name: "LeNet"
layer {
  name: "mnist"
  type: "Data"
  top: "data"
  top: "label"
  include {
    phase: TRAIN
  }
  transform_param {
    scale: 0.00390625
  }
  data_param {
    source: "examples/mnist/mnist_train_lmdb"
    batch_size: 64
    backend: LMDB
  }
}
layer {
  name: "mnist"
  type: "Data"
  top: "data"
  top: "label"
  include {
    phase: TEST
  }
  transform_param {
    scale: 0.00390625
  }
  data_param {
    source: "examples/mnist/mnist_test_lmdb"
    batch_size: 100
    backend: LMDB
  }
}
```

###### lenet_solver.prototxt
```bash
# The train/test net protocol buffer definition
net: "examples/mnist/lenet_train_test.prototxt"
# test_iter specifies how many forward passes the test should carry out.
# In the case of MNIST, we have test batch size 100 and 100 test iterations,
# covering the full 10,000 testing images.
test_iter: 100
# Carry out testing every 500 training iterations.
test_interval: 500
# The base learning rate, momentum and the weight decay of the network.
base_lr: 0.01
momentum: 0.9
weight_decay: 0.0005
# The learning rate policy
lr_policy: "inv"
gamma: 0.0001
power: 0.75
# Display every 100 iterations
display: 100
# The maximum number of iterations
max_iter: 10000
# snapshot intermediate results
snapshot: 5000
snapshot_prefix: "examples/mnist/lenet"
# solver mode: CPU or GPU
solver_mode: GPU
```
