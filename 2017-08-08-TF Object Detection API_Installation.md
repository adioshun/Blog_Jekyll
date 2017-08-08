# Tensorflow Object Detection API Installation

> 설치 환경 ubunutu 16.4, python3, tf 1.2



## 1. 설치 

필수 패키지 (TF)
```bash
# For CPU
pip install tensorflow
# For GPU
#pip install tensorflow-gpu
conda install tensorflow-gpu
```

관련 패키지 설치
```bash
sudo apt-get install protobuf-compiler python-pil python-lxml
sudo pip install matplotlib pillow lxml
```

소스 다운로드
```bash
git clone https://github.com/tensorflow/models.git
```

## 2. 설정
Protobuf 컴파일
```bash
# From tensorflow/models/
protoc object_detection/protos/*.proto --python_out=.
```

Add Libraries to PYTHONPATH : slim 디렉터리를 append시키기 위함이다.
```bash
# From tensorflow/models/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
```

## 3. 설치 확인
```bash
python object_detection/builders/model_builder_test.py

.......
----------------------------------------------------------------------
Ran 7 tests in 0.013s

OK
```
