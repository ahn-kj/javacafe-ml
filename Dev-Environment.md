# 실습환경 구성(맥 OSX)

## 참고 사이트
https://www.tensorflow.org/install/install_mac

## 설치 환경

macOS Sierra 10.12.3

## 설치 과정

### 어떤 텐서플로우를 설치할 것인가 결정

텐서플로우를 설치하기 전에 먼저 CPU로 돌릴지 GPU로 돌릴지 결정해야 합니다. 시스템에 NVIDIA® GPU가 없으면 CPU 버전을 설치해야 합니다. 이 문서에서는 CPU 버전을 설치합니다.

### 텐서플로우 설치 방법 결정

TensorFlow에서 지원되는 선택 사항은 다음과 같습니다.

* virtualenv
* "native" pip
* Docker
* 소스에서 설치하기 (전문가를 위한 설치 방법으로 별도 가이드 문서가 있음. https://www.tensorflow.org/install/install_sources)

### virtualenv를 이용한 텐서플로우 설치

Tensorflow에서는 virtualenv를 권장합니다. Virtualenv는 다른 Python 개발과 분리된 가상의 Python 환경으로, 동일한 컴퓨터에서 다른 Python 프로그램을 방해하거나 영향을 받을 수 없습니다. virtualenv 설치 과정 중에 TensorFlow 및 TensorFlow에 필요한 모든 패키지를 설치해야 하는데 그 방법이 매우 쉽습니다. 전체적으로 virtualenv는 TensorFlow를 설치하고 실행하기 위한 안전하고 신뢰할 수 있는 방법을 제공합니다.

#### 1. 터미널 시작

#### 2. pip 및 virtualenv 설치

```
 $ sudo easy_install pip
 $ sudo pip install --upgrade virtualenv
```

#### 3. virtualenv 환경 만들기

>virtualenv --system-site-packages targetDirectory

targetDirectory는 virtualenv tree의 최상위 루트로 간주합니다. 예시에는 targetDirectory가 ~/tensorflow이지만 사용자 마음대로 지정할 수 있습니다.

```
$ virtualenv --system-site-packages ~/tensorflow
```

#### 4. virtualenv 환경 활성화

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

#### 5. 텐서플로우 설치

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

#### 6. 5단계에서 실패했을 경우

5단계가 실패한 경우 (일반적으로 8.1보다 낮은 pip 버전을 호출했기 때문에) 다음 형식의 명령을 실행하여 활성화된 Virtualenv 환경에 TensorFlow를 설치합니다.

> pip install --upgrade TF_BINARY_URL

여기서 TF_BINARY_URL은 TensorFlow Python 패키지의 URL을 식별합니다. TF_BINARY_URL의 적절한 값은 운영 체제, Python 버전 및 GPU 지원에 따라 다릅니다. 그러므로 시스템에 적합한 TF_BINARY_URL 값을 찾아서 사용해야 합니다.

```
# Mac OS X, Python 버전 2.7 및 CPU 전용
$ pip install --upgrade \
 https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.0.0-py2-none-any.whl

# Mac OS X, Python 버전 3.4 또는 3.5 및 CPU 전용
$ pip3 install --upgrade \
 https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.0.0-py3-none-any.whl
```

참고 : 시스템에 적합한 TF_BINARY_URL는 아래 링크에서 찾을 수 있습니다. https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get_started/os_setup.md

#### 7. 설치 확인

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
## 에러 리스트

### 설치 후 발생한 warning

#### warning 메세지

```
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
```

https://www.facebook.com/groups/TensorFlowKR/permalink/425382234469507/

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


