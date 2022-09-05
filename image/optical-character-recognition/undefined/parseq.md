# ParSeq 셋업

현재 기준, 여러 데이터셋에서 1위 모델은 **ParSeq** (ECCV 2022)이다.

* 논문: [https://arxiv.org/pdf/2207.06966v1.pdf](https://arxiv.org/pdf/2207.06966v1.pdf)
* 코드: [https://github.com/baudm/parseq](https://github.com/baudm/parseq)



Step 1. 데이터셋 셋업

정리해서 구글드라이브에 올려둔게 있음. 여기서 다운 받음.

[https://github.com/baudm/parseq/blob/main/Datasets.md](https://github.com/baudm/parseq/blob/main/Datasets.md)



Step 2. github 코드와 pretrained model 가져와 실행확인

원래 huggingface에 pretrained model 파일이 git lfs로 올라가있던데 (받아보니까 bin file), 굳이 그걸 다운받지 않아도 괜찮았음.

그냥 실행시에 'pretrained=parseq' 넣어주면 알아서 pretrained 다운됨.

```
./test.py pretrained=parseq
```

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>실행 확인.</p></figcaption></figure>



Step 3. 코드 분석

Step 4. Custom Dataset 전처리 & 인퍼런스 확인
