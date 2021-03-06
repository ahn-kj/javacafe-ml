# 텐서플로우\(TensorFlow\) 설치

텐서플로우는 머신러닝\(기계학습\)을 위한 오픈소스 소프트웨어 라이브러리입니다. 텐서플로우 사이트에서 제공하는 설치 가이드를 따라서 설치를 진행해보도록 하겠습니다. 이 문서에서의 OSX 버전은 macOS Sierra 10.12.3입니다.

[https://www.tensorflow.org/install/install\_mac](https://www.tensorflow.org/install/install_mac)

## 어떤 텐서플로우를 설치할 것인가 결정

텐서플로우를 설치하기 전에 CPU만 지원하는 것을 설치할지, GPU까지 지원하는 것을 설치할지 결정해야합니다. CPU는 GPU보다 설치가 쉽고, GPU는 병렬 처리 방식이므로 CPU보다 훨씬 빠른 처리가 가능합니다. 시스템에 NVIDIA® GPU가 없으면 CPU 버전을 설치해야 합니다. 이 문서에서는 CPU 버전을 설치합니다.

## 텐서플로우 설치 방법 결정

TensorFlow에서 지원되는 설치 선택 사항은 **virtualenv, "native" pip, Docker, 소스에서 설치하기 \(전문가를 위한 설치 방법\)**가 있습니다.  Tensorflow에서는 virtualenv를 권장하므로, 그 방법으로 설치하도록 하겠습니다.

## virtualenv를 이용한 텐서플로우 설치

Virtualenv는 다른 Python 개발과 분리된 가상의 Python 환경으로, 동일한 컴퓨터에서 다른 Python 프로그램을 방해하거나 영향을 받을 수 없습니다. virtualenv 설치 과정 중에 TensorFlow 및 TensorFlow에 필요한 모든 패키지를 설치해야 하는데 그 방법이 매우 쉽습니다. 전체적으로 보면 virtualenv는 TensorFlow를 설치하고 실행하기 위한 안전하고 신뢰할 수 있는 방법을 제공합니다.

### 1. 터미널 시작

### 2. pip 및 virtualenv 설치

```
 $ sudo easy_install pip
 $ sudo pip install --upgrade virtualenv
```

### 3. virtualenv 환경 만들기

> virtualenv --system-site-packages targetDirectory

targetDirectory는 virtualenv tree의 최상위 루트로 간주합니다. 예시에는 targetDirectory가 ~/tensorflow이지만 사용자 마음대로 지정할 수 있습니다. --system-site-packages 옵션은 가상 환경에게 global site-packages의 액세스 권한 부여합니다.

```
$ virtualenv --system-site-packages ~/tensorflow
```

### 4. virtualenv 환경 활성화

```
# bash, sh, ksh, or zsh를 사용할 경우
$ source ~/tensorflow/bin/activate

# csh or tcsh를 사용할 경우      
$ source ~/tensorflow/bin/activate.csh
```

위의 명령어를 실행하면 아래와 같이 프롬프트가 변경됩니다.

```
(tensorflow)$
```

### 5. 텐서플로우 설치

```
# pip 버전 확인
$ pip --version
```

시스템에 설치된 pip 버전이 8.1 이상일 경우에는 아래 명령 중 하나를 실행하여, 활성화된 Virtualenv 환경에 TensorFlow 및 TensorFlow에 필요한 모든 패키지를 설치합니다. 아래 명령어가 성공했다면 6단계는 넘어가고, 실패했다면 6단계를 실행합니다.  
pip 버전이 8.1보다 낮을 경우에도 6단계를 실행합니다.

```
# Python 2.7일 경우
$ pip install --upgrade tensorflow

# Python 3.n일 경우
$ pip3 install --upgrade tensorflow
```

### 6. 5단계에서 실패했을 경우

5단계가 실패한 경우 \(일반적으로 8.1보다 낮은 pip 버전을 호출했기 때문에\) 다음 형식의 명령을 실행하여 활성화된 Virtualenv 환경에 TensorFlow를 설치합니다.

> pip install --upgrade TF\_BINARY\_URL

여기서 TF\_BINARY\_URL은 TensorFlow Python 패키지의 URL입니다. TF\_BINARY\_URL의 적절한 값은 운영 체제, Python 버전 및 GPU 지원에 따라 다릅니다. 그러므로 시스템에 적합한 TF\_BINARY\_URL 값을 찾아서 사용해야 합니다.

```
# Mac OS X, Python 버전 2.7 및 CPU 전용
$ pip install --upgrade https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.0.0-py2-none-any.whl

# Mac OS X, Python 버전 3.4 또는 3.5 및 CPU 전용
$ pip3 install --upgrade https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.0.0-py3-none-any.whl
```

참고 : 시스템에 적합한 TF\_BINARY\_URL는 아래 링크에서 찾을 수 있습니다. [https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get\_started/os\_setup.md](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get_started/os_setup.md)

### 7. 설치 확인

새로운 터미널을 연 후,

```
1. virtualenv 환경 활성화
# bash, sh, ksh, or zsh를 사용할 경우
$ source ~/tensorflow/bin/activate

# csh or tcsh를 사용할 경우      
$ source ~/tensorflow/bin/activate.csh 

2. 파이썬 호출
(tensorflow) $ python

3. 프로그램 입력
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))

4. 아래 메세지가 출력되면 설치 성공
Hello, TensorFlow!
>>>
```

## virtualenv 환경 비활성화

아래 명령어를 실행하면 기본 프롬프트로 되돌아갑니다.

```
(tensorflow)$ deactivate
```

## virtualenv 환경 삭제

> $ rm -r targetDirectory

virtualenv 환경을 삭제하려면, 우리가 만들었던 targetDirectory를 지우면 됩니다.

```
$ rm -r ~/tensorflow
```

## 텐서플로우를 설치하면서 발생한 이슈

텐서플로우 1.0 버전 업 후에 발생하는 문제로, 프로그램은 실행되지만 아래와 같은 경고 메세지가 뜬다.

```
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
```

[https://www.facebook.com/groups/TensorFlowKR/permalink/425382234469507/](https://www.facebook.com/groups/TensorFlowKR/permalink/425382234469507/)

# virtualenv 환경에 OpenAI Gym 설치하기

## 참고 사이트

[https://github.com/openai/gym\#pip-version](https://github.com/openai/gym#pip-version)

## 설치 과정

#### 1. virtualenv 환경 활성화

```
# bash, sh, ksh, or zsh를 사용할 경우
$ source ~/tensorflow/bin/activate

# csh or tcsh를 사용할 경우      
$ source ~/tensorflow/bin/activate.csh
```

#### 2. 원격 저장소 복제

```
(tensorflow)$ sudo git clone https://github.com/openai/gym
```

#### 3. gym 디렉토리로 이동

```
(tensorflow)$ cd gym
```

#### 4. gym 설치

```
(tensorflow)$ sudo pip install -e .
```

#### 5. 설치 확인

ImportError가 발생하지 않으면 설치 성공

```
>>> import gym
>>>
```



