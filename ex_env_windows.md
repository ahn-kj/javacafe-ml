# 텐서플로우(TensorFlow) 설치

텐서플로우 사이트에서 제공하는 설치 가이드를 따라서 설치를 진행해보도록 하겠습니다. 이 문서에서의 윈도우 버전은 Windows 10 Pro 64bit입니다.

https://www.tensorflow.org/install/install_windows

## 어떤 텐서플로우를 설치할 것인가 결정

텐서플로우를 설치하기 전에 CPU만 지원하는 것을 설치할지, GPU까지 지원하는 것을 설치할지 결정해야합니다. CPU는 GPU보다 설치가 쉽고, GPU는 병렬 처리 방식이므로 CPU보다 훨씬 빠른 처리가 가능합니다. 시스템에 NVIDIA® GPU가 없으면 CPU 버전을 설치해야 합니다. 이 문서에서는 CPU 버전을 설치합니다.

## 텐서플로우 설치 방법 결정

TensorFlow에서 지원되는 설치 선택 사항은 **"native" pip, Anaconda**가 있습니다.

Native pip는 가상 환경을 거치지 않고 시스템에 TensorFlow를 직접 설치하기 때문에 시스템의 다른 Python 기반 설치에 영향을 줄 수 있습니다.

Anaconda에서는 가상 환경을 만들기 위해 conda를 사용할 수 있습니다. 그러나 아나콘다에서는 cond install 명령 대신 pip install 명령을 사용하여 TensorFlow를 설치하는 것이 좋습니다. conda 패키지는 공식적으로 지원되지 않는 커뮤니티 지원이므로, TensorFlow 팀은 conda 패키지를 테스트하거나 유지 관리하지 않습니다.

이 문서에서는 Anaconda를 이용하여 설치하도록 하겠습니다.

## Anaconda를 이용한 텐서플로우 설치

### 1. Anaconda 설치

Anaconda 4.3.0 For Windows Python 3.6 version 64-BIT INSTALLER(422m)를 설치합니다.

https://www.continuum.io/downloads

<img src="http://postfiles8.naver.net/MjAxNzAyMTdfMTUg/MDAxNDg3MzI0MDgzMjUw.D5qUa5cVzWXh681YIi4Ef23Iykj3n4nsKRJWpayMtJAg._-iputvfARxh64VALWa7dUww62m0ijp8JURJ-zZFl7Yg.PNG.kioku714/1.png?type=w2" width="450px" />

<img src="http://postfiles10.naver.net/MjAxNzAyMTdfMTcz/MDAxNDg3MzI0MDgzNDcz.kR4EeyY7J1cWKPSSGg_mNgGvmZIbEArk4ihBpWYC6Qog.xFk40A99EYdcYEb23eVivl7apzRShhpV0tE36h3dle4g.PNG.kioku714/2.png?type=w2" width="450px" />

<img src="http://postfiles7.naver.net/MjAxNzAyMTdfOTEg/MDAxNDg3MzI0MDgzODQx.kY5fBYLnL2FXOar5eRFKh-z0d8CaupSxkRkBLVPqv-Ug.Rv6fn099hL8fW0BHockSDMcyiLxoPm7ylGk_fI-G1Ngg.PNG.kioku714/4.png?type=w2" width="450px" />

<img src="http://postfiles12.naver.net/MjAxNzAyMTdfMzgg/MDAxNDg3MzI0MDgzNjYw.g5JcndRc04QI6TsqBZk-k6qEhPu9UsrUnYHRDMfG_K4g.5ANgBYo_S91tLbTRoR_TEHu0XWzzrpujmk7WgatGWfYg.PNG.kioku714/3.png?type=w2" width="450px" />

<img src="http://postfiles2.naver.net/MjAxNzAyMTdfMTEw/MDAxNDg3MzI0MDg0OTE3.4AzGYv6A47yiHK3kPnvWYuLfC_f2LPEZ2IVcYcBKnM8g.eZ3V661lAOZqLdLV9OD5lih2OdPg68dyx4O3WIuW5mYg.PNG.kioku714/5.png?type=w2" width="450px" />

<img src="http://postfiles14.naver.net/MjAxNzAyMTdfMTEg/MDAxNDg3MzI0MDg1MTc1.SqFaRkUMtbNUjy6nrSnkWV1ONwvH8igaeUDmUjZyPdsg.FcIttYmG-J-Wk8l9QPbGjET6F-frDkYDOIjBvRtWPpEg.PNG.kioku714/6.png?type=w2" width="450px" />

<img src="http://postfiles14.naver.net/MjAxNzAyMTdfMTM1/MDAxNDg3MzI0MDg1NDE2.10vt1YlKHGIt-Cm_8FLx0kxGtW43EV4SH6ZhRDDHmMMg._nP4HrrEfuioNeR-PTn0ZIdGNG4dGq5f5XHLnVZx0-og.PNG.kioku714/7.png?type=w2" width="450px" />

### 2. conda env 생성

명령 프롬프트를 열고 tensorflow 라는 이름의 conda env를 만듭니다.

```
C:> conda create -n tensorflow python=3.5
```

**TensorFlow는 Windows에서 Python 버전 3.5.x만 지원합니다.**
우리가 설치한 Anaconda는 Python 3.6이 기본 설정이므로, 명령어에 python=3.5를 추가해야 합니다.

### 3. conda env 활성화

```
C:> activate tensorflow
(tensorflow)C:> #
```

### 4. 텐서플로우 CPU 버전 설치

```
(tensorflow)C:> pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.0.0-cp35-cp35m-win\_x86\_64.whl
```

### 5. 설치 확인

새로운 명령 프롬프트를 연 후,
```
# conda env 활성화
C:> activate tensorflow

# 파이썬 호출
(tensorflow) C:\> python

# 프로그램 입력
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))

# 아래 메세지가 출력되면 설치 성공
b'Hello, TensorFlow!'
>>>
```

### conda env 삭제 명령어

> conda remove -n (삭제할 conda env 이름) --all

```
C:> conda remove -n tensorflow --all
```

## 텐서플로우 설치 중 발생한 에러

### 에러메세지

tensorflow-1.0.0-cp35-cp35m-win_x86_64.whl is not a supported wheel on this platform.

### 해결방법

```
(tensorflow)C:> pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.0.0-cp35-cp35m-win\_amd64.whl
```

### 참고사이트

http://stackoverflow.com/questions/42266094/tensorflow-1-0-windows-64-bit-anaconda-4-3-0-error

## 텐서플로우 설치 확인 중 발생한 에러

### 에러메세지

```
(tensorflow) C:\>python
Python 3.5.2 |Continuum Analytics, Inc.| (default, Jul 5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)] on win32
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

### 해결방법

```
(tensorflow)C:> pip install --upgrade http://ci.tensorflow.org/view/Nightly/job/nightly-win/85/DEVICE=cpu,OS=windows/artifact/cmake\_build/tf\_python/dist/tensorflow-1.0.0rc2-cp35-cp35m-win\_amd64.whl
```

## 텐서플로우 설치 확인 중 발행한 warning

```
C:> activate tensorflow
(tensorflow) C:\>python
Python 3.5.2 |Continuum Analytics, Inc.| (default, Jul 5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)] on win32
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

https://github.com/tensorflow/tensorflow/issues/7716
