# 실습을 위한 환경 준비

## 설치환경
Windows 10 Pro 64bit


## 참고 사이트
https://www.tensorflow.org/install/install_windows

## 설치

### 어떤 텐서플로우를 설치할 것인가 결정

텐서플로우를 설치하기 전에 먼저 CPU로 돌릴지 GPU로 돌릴지 결정해야 합니다. 시스템에 NVIDIA® GPU가 없으면 CPU 버전을 설치해야 합니다.

### 텐서플로우 설치 방법 결정

그 다음은 "native" pip으로 설치할지 Anaconda로 설치할지 선택해야 합니다. 
Native pip는 가상 환경을 거치지 않고 시스템에 TensorFlow를 직접 설치하기 때문에 시스템의 다른 Python 기반 설치에 영향을 줄 수 있습니다.

Anaconda에서는 가상 환경을 만들기 위해 conda를 사용할 수 있습니다. 그러나 아나콘다에서는 cond install 명령 대신 pip install 명령을 사용하여 TensorFlow를 설치하는 것이 좋습니다.

참고 : conda 패키지는 공식적으로 지원되지 않는 커뮤니티 지원입니다. 즉, TensorFlow 팀은 conda 패키지를 테스트하거나 유지 관리하지 않습니다.


### Anaconda를 이용한 설치

1.Anaconda 4.3.0 For Windows Python 3.6 version 64-BIT INSTALLER(422m) 설치
	
https://www.continuum.io/downloads

<img src="http://postfiles12.naver.net/MjAxNzAyMTdfMTQz/MDAxNDg3MzIzMTYxNTUx.BFpwB8-3ecPVhGYMcHgFiswqkQuo5so05M8Sx1ikVpYg.H-sJgm69wtkf5bzcVTdBzRpZzYDaiD4h_LoePE19_yQg.JPEG.kioku714/1.jpg?type=w2" width="400px" />

<img src="http://postfiles12.naver.net/MjAxNzAyMTdfMTM0/MDAxNDg3MzIzMTYxNzgz.T7iOl-uNYm4mKoVeM3_S7Clvj2RTPiB1AAcUN53RkyQg.L2yRfUOGYY0gCgEfX4yL2MRCVFx9gBfYdLkfXHKQ-Hkg.JPEG.kioku714/2.jpg?type=w2" width="400px" />

<img src="http://postfiles2.naver.net/MjAxNzAyMTdfMSAg/MDAxNDg3MzIzMTYxOTkx.u-T_156H02ntYWTOl3vnMKpjieMr4DinkL44bWhsRqUg.egptCE_tOuw3XHUv6HGa515Tb462E9dVMImlyCGp68Ug.JPEG.kioku714/3.jpg?type=w2" width="400px" />

<img src="http://postfiles16.naver.net/MjAxNzAyMTdfMjM5/MDAxNDg3MzIzMTYyMTU5.VRcWBqph3Yf86OMVHqn7Q1WOCwW_OPbh4hBA-ghvhvUg.M6Lxx3YgtcL9EtS9zhqKkEGvFi9r-VVQNFXOkvadJdwg.JPEG.kioku714/4.jpg?type=w2" width="400px" />

<img src="http://postfiles14.naver.net/MjAxNzAyMTdfMjcz/MDAxNDg3MzIzMTYyMzk1.ojotEt6M-bw6PoqVIrf-9KHV_wMNhUJUnsAc6UtHzb4g.ewgn9WA6tbu9Snf3JGBO-LF-OJZqthX0VYejr7JFTSAg.JPEG.kioku714/5.jpg?type=w2" width="400px" />

<img src="http://postfiles15.naver.net/MjAxNzAyMTdfMTIx/MDAxNDg3MzIzMTYyNTYw.2S-HEbYGvgekIOrQVmywY04Zs2o2zugz87Y6p1wwTzMg.oV2iZLlQP4z4myblQ9Bsm2OyqDZ12mkk-fh-nQhnwNgg.JPEG.kioku714/6.jpg?type=w2" width="400px" />

<img src="http://postfiles3.naver.net/MjAxNzAyMTdfODgg/MDAxNDg3MzIzMTYyNzkw.2JF3jW6-vfxcTGb3UMpnPIXKME2dv8GEaqayNoCELXgg.k92--uM3ew5GrUF547LauA1EfR1CUu0UNaFNOrnmjXEg.JPEG.kioku714/7.jpg?type=w2" width="400px" />
	
2.tensorflow 라는 이름의 conda env 생성

```
C:> conda create -n tensorflow python=3.5
```

TensorFlow는 Windows용 Python 3.5.x 만 지원합니다. 

Anaconda는 Python 3.6이 기본 설정이므로 명령어에 python=3.5를 추가해야 합니다.

3.conda env 활성화

```
C:> activate tensorflow
(tensorflow)C:> #
```

4.CPU 버전 텐서플로우 설치

(tensorflow)C:> pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.0.0-cp35-cp35m-win_x86_64.whl

5.설치 확인

터미널을 새로 연 후,

```
C:> activate tensorflow
(tensorflow) C:\>python
Python 3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> hello = tf.constant('hello!')
>>> sess = tf.Session()
2017-02-17 15:22:30.423181: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.426415: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE2 instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.428599: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE3 instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.431342: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.434036: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.439169: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.441804: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
2017-02-17 15:22:30.444456: W c:\tf_jenkins\home\workspace\nightly-win\device\cpu\os\windows\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.
>>> sess = tf.Session()
>>> print(sess.run(hello))
b'hello!'
>>>
```

## 에러 리스트

### 설치 중 발생한 에러

#### 에러메세지

tensorflow-1.0.0-cp35-cp35m-win_x86_64.whl is not a supported wheel on this platform.

#### 해결방법

```
(tensorflow)C:> pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.0.0-cp35-cp35m-win_amd64.whl
```

#### 참고사이트

http://stackoverflow.com/questions/42266094/tensorflow-1-0-windows-64-bit-anaconda-4-3-0-error

### 설치 확인 중 발생한 에러

#### 에러메세지

```
(tensorflow) C:\>python
Python 3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> hello = tf.constant('hello!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "BestSplits" device_type: "CPU"') for unknown op: BestSplits
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "CountExtremelyRandomStats" device_type: "CPU"') for unknown op: CountExtremelyRandomStats
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "FinishedNodes" device_type: "CPU"') for unknown op: FinishedNodes
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "GrowTree" device_type: "CPU"') for unknown op: GrowTree
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "ReinterpretStringToFloat" device_type: "CPU"') for unknown op: ReinterpretStringToFloat
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "SampleInputs" device_type: "CPU"') for unknown op: SampleInputs
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "ScatterAddNdim" device_type: "CPU"') for unknown op: ScatterAddNdim
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "TopNInsert" device_type: "CPU"') for unknown op: TopNInsert
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "TopNRemove" device_type: "CPU"') for unknown op: TopNRemove
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "TreePredictions" device_type: "CPU"') for unknown op: TreePredictions
E c:\tf_jenkins\home\workspace\release-win\device\cpu\os\windows\tensorflow\core\framework\op_kernel.cc:943] OpKernel ('op: "UpdateFertileSlots" device_type: "CPU"') for unknown op: UpdateFertileSlots
b'hello!'
```

#### 해결방법

```
(tensorflow)C:> pip install --upgrade http://ci.tensorflow.org/view/Nightly/job/nightly-win/85/DEVICE=cpu,OS=windows/artifact/cmake_build/tf_python/dist/tensorflow-1.0.0rc2-cp35-cp35m-win_amd64.whl
```

### conda env 삭제 명령어

conda remove -n "삭제할 conda env 이름" --all

```
C:> conda remove -n tensorflow --all
```
