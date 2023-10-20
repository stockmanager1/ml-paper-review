# 논문요약

facebook에서 새롭게 제시하는 새로운 데이터 증강 라이브러리다. 이때 증강이 가능한 데이터는 text,image등 4가지 카테고리애서 모두 적용가능하다. 이번 논문은 주로 기존의 방법론들과 비교를 중심으로 구성되어 있다. 근데 일단 증강가능한 부분이 많은건 알겠는데, 논문의 결과를 보나 **[이번 대회](https://dacon.io/competitions/official/236082/data)**에 적용해보나 별로 큰 인사이트는 못보는 것 같다. 

p.s. 이번 대회를 준비하면서 거의 처음으로 정규 이미지 분류 대회에 좀 인사이트를 얻을까 해서 논문을 읽게 되었다. 특히 데이터가 너무 imbalance 해서 이걸 좀 해결할 수 있을까 하고 찾아 본건데 딱히 구현할 것도 없고, 좀 신기하다 이거지 큰 소득은 없는 것 같다. 다른 증강 방법론을 찾아야 할 것 같다.

# 논문 내용

## -Audio
![스크린샷 2023-05-03 235105](https://user-images.githubusercontent.com/95357946/235966542-37956a61-79ea-4a1b-9771-082cdd9b6896.png)



위 그래프는 걸리는 시간을 측정한 테이블이다. 근데 이걸 보면 모두 알겠지만, 모든 기능을 지원하기는 하지만 걸리는 시간이 너무 많이 걸린다. 

아래 테이블은 각 라이브러리가 지원하는 증강 방법을 보여주는 테이블이다. 근데 일단 오디오 부분에서 torchaudio에 비해서 지원하는 기능의 갯수도 떨어지고, 적용 시간도 너무 오래 걸린다. 아직 audio에 대해서 적용해본 적은 없지만 만약 audio 데이터를 증강해야 하는 때에는 torchaudio 내에서 해결하자. 

![스크린샷 2023-05-03 235253](https://user-images.githubusercontent.com/95357946/235966635-72fe433e-11ae-4ab7-81d4-d81e56613816.png)


## image

![스크린샷 2023-05-04 000409](https://user-images.githubusercontent.com/95357946/235966784-e6e2e419-e202-4e11-b761-c8c34425aea5.png)


보면 image의 경우 지원하는 증강 방식이 압도적으로 많다. 보면 이모지를 추가하는 방법부터 페이스북 화면에 적용하는 방법까지 정말 다양한 방법이 있다. 그래서 이번에 몇개 적용해보기는 했는데, 너무 많다 보니까 기능을 다 사용해보기는 좀 어려울 것 같다.


![스크린샷 2023-05-04 001156](https://user-images.githubusercontent.com/95357946/235966832-e697c1ee-64cc-49b0-be35-a0c36f80e607.png)

일단 속도 측면에서 압도적으로 밀린다. 일단 잎에서 이야기 했듯, 기능이 정말 많아서 이걸로 적용해야지, 시간적인 측면을 따지면, albumentation을 이길게 없을 것 같다.

![스크린샷 2023-05-04 002407](https://user-images.githubusercontent.com/95357946/235966890-08416d96-0d70-424c-bf2c-2a5d80d04a75.png)


imagenet 데이터로 학습했을때, 실제로 이렇게 보면 성능이 향상되고 있는 것을 알 수 있다.

 

## text

![스크린샷 2023-05-04 002538](https://user-images.githubusercontent.com/95357946/235966965-04115fef-2bd1-45e9-a976-243838e583a7.png)


근데 일단 속도는 역시 밀리는 모습을 볼 수 있다. 그리고 지원하는 모델 갯수도 한번 보자.


![스크린샷 2023-05-04 002701](https://user-images.githubusercontent.com/95357946/235967000-62c50651-c009-4dc8-a1af-b1eae8e09c49.png)

지원하는 모델 갯수도 밀린다. 

## video

![스크린샷 2023-05-04 002838](https://user-images.githubusercontent.com/95357946/235967078-5a3a8119-4d69-4add-befe-f7798b9cbece.png)


이미지나 영상은 지원하는 증강 방식이 다른 라이브러리보다 많은게 확실히 느껴진다.

![스크린샷 2023-05-04 002947](https://user-images.githubusercontent.com/95357946/235967113-14158dec-4752-49a2-9074-7a954e2fca79.png)


증강에 걸리는 시간적 이점은 다른 것과 마찬가지로 의미가 없다.

# 결과

솔직히 text나 audio에서 사용하는 건 비추라고 생각된다. 왜냐하면 일단 지원하는 방법론도 너무 작고 속도도 더 떨어진다. 하지만 image, video에서는 비록 속도는 좀 떨어지더라도 너무 압도적으로 지원하는 방법론이 많아서 해볼만 하다고 생각이 든다. 개인적으로 이모지나 페이스북 페이지 증강이 가장 신기했다.

# 출처

[https://arxiv.org/abs/2201.06494](https://arxiv.org/abs/2201.06494)