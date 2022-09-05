---
description: 2022.09.02 작성
---

# SOTA 알고리즘 찾기

## 일단 최신 모델로 시작하기

고전 알고리즘들을 살펴볼 수도 있지만 그건 시간 될때 정리해보고, **우선 SOTA 알고리즘들 부터 찾아서 follow-up** 해보자.

**Papers with code**에 scene text recognition, scene text detection 각각에 대해 데이터셋이 여러개가 있다.

{% embed url="https://paperswithcode.com/sota/scene-text-recognition-on-icdar2013" %}

현재 내 경우는 이미 텍스트가 있는 좌표값을 알고있기 때문에 detection을 생략할 수 있어서, Scene Text Recognition (STR)을 기준으로 봤다.&#x20;

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Recognition 데이터는 **synthetic/real**, 그리고 **반듯한 텍스트/구불구불한 텍스트** 데이터셋으로 나뉜다. 후자가 어렵고, CUTE80같은 데이터셋이 여기에 속한다.

일단은 어떤 모델이 새로 나왔는지 살펴보는게 목적이기 때문에 가장 대표적인 **ICDAR13** 기준 순위권 모델 몇개를 보면 될 것 같다. 반듯반듯해서 웬만한 모델의 인식 성능이 매우 높은 데이터셋이다.



현재 기준, 여러 데이터셋에서 1위 모델은 **ParSeq** (ECCV 2022)이다.

* 논문: [https://arxiv.org/pdf/2207.06966v1.pdf](https://arxiv.org/pdf/2207.06966v1.pdf)
* 코드: [https://github.com/baudm/parseq](https://github.com/baudm/parseq)

huggingface에서 돌려볼 수 있다.

{% embed url="https://huggingface.co/spaces/baudm/PARSeq-OCR" %}

<figure><img src="../../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

그러면 이제 이 모델을 셋업하고 내가 적용하려는 데이터셋에서도 잘 동작하는지 확인해보자.

깃허브 보니까 pretrained weight을 huggingface에 올려뒀다고 하니까 참고해야겠다.



**Summary**

* paperswthcode 들어간다.
* 목적에 맞는 task & 데이터셋 선택
* SOTA 알고리즘 확인하고, 언제나온 논문인지 체크
* 논문, 코드, pre-trained model 확인
