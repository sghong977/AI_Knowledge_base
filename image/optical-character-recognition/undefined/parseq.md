# ParSeq 셋업

현재 기준, 여러 데이터셋에서 1위 모델은 **ParSeq** (ECCV 2022)이다.

* 논문: [https://arxiv.org/pdf/2207.06966v1.pdf](https://arxiv.org/pdf/2207.06966v1.pdf)
* 코드: [https://github.com/baudm/parseq](https://github.com/baudm/parseq)



### Step 1. 데이터셋 셋업

\[IC13 데이터] 대략 이런식으로 생겼다.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

![](<../../../.gitbook/assets/image (4).png>)



**Dataset**

* **\[Synthetic]** MJSynth, SynthText
* **\[Real]** IIIT5k, SVT, SVTP, IC13, IC15, CUTE80, ArT, RCTW17, ReCTS, LSVT, MLT19, COCO-Text, Uber-Text, TextOCR, OpenVINO
* 참고. [https://github.com/baudm/parseq/blob/main/Datasets.md](https://github.com/baudm/parseq/blob/main/Datasets.md)
  * 정리해서 구글드라이브에 올려둔게 있음. 여기서 다운 받음.
* 고전적인 데이터셋이라 테스트에는 쓰지만 양이 너무 작아 요즘은 학습용으로는 안쓰는 것도 있고 그렇다.

다운 받으면 각 폴더 내에 **data.mdb**, **lock.mdb** 형태로 되어있다.



**Lightning Memory-Mapped Database Manager (LMDB)?**

* lmdb 페이지 설명 [http://www.lmdb.tech/doc/](http://www.lmdb.tech/doc/)
* 어떤 분의 한국어 번역 [https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true\&blogId=tosemfaos\&logNo=220919092977](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true\&blogId=tosemfaos\&logNo=220919092977)
* 아무튼 이 코드에서는 OCR에 필요한 다양한 데이터셋들을 lmdb.open()해서 가져온다.



### Step 2. github 코드와 pretrained model 가져와 실행확인

원래 huggingface에 pretrained model 파일이 git lfs로 올라가있던데 (받아보니까 bin file), 굳이 그걸 다운받지 않아도 괜찮았음.

**Torch Hub 지원**: 그냥 실행시에 'pretrained=parseq' 넣어주면 알아서 pretrained 다운됨.

```
./test.py pretrained=parseq
```

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>실행 확인.</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>refine_iter를 주면 성능이 약간 오르기도.</p></figcaption></figure>



### Step 3. 코드 분석

Custom Dataset에서 돌리는 것이 첫번째 목적이라서 이를 중점적으로 봄.

깃허브: cusion dataset 관련 이슈

* 일단은 데이터들을 mdb 형태로 만들어야하므로, [https://github.com/chibohe/CdistNet-pytorch/blob/main/tool/create\_lmdb\_dataset.py](https://github.com/chibohe/CdistNet-pytorch/blob/main/tool/create\_lmdb\_dataset.py) 참고하기.
* finetuning: [https://github.com/baudm/parseq/issues/7](https://github.com/baudm/parseq/issues/7)
* test: [https://github.com/baudm/parseq/issues/27](https://github.com/baudm/parseq/issues/27).



### Step 4. Custom Dataset 전처리 & 인퍼런스 확인

1. creade\_lmdb()를 돌리기 위해서 아래 내용을 준비한다.

고려사항.

* 인식하기 어려운 해상도의 경우가 있음.
* 문서 혹은 input scene에 특정 양식이 있는데, 텍스트 정보가 없는 경우가 있고 있는 경우가 있음.

```
    inputPath  : input folder path where starts imagePath
    gtFile     : list of image path and label
```
