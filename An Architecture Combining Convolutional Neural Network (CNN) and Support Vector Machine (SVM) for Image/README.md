# 논문요약
기존에 이미지 분류에서 거의 디폴트 값으로 사용되던 crossentropy의 사용에 의문을 가지고, 새로운 손실함수 방법론을 제시한 논문이었다. 바로 cross entropy 대신에 svm_l2를 사용하면 어떨까라는 논문이었다.

# 실험 환경

실험관경은 다음과 같다.
## 논문에서는 다음과 같이 cnn 신경망의 모양을 정의한다. 

![스크린샷 2023-05-03 143222](https://user-images.githubusercontent.com/95357946/235840703-7ea55215-2de0-4377-8f50-32885c188921.png)

## 손실함수 및 옵티마이저
![스크린샷 2023-05-03 143319](https://user-images.githubusercontent.com/95357946/235840851-f834b094-796a-47ca-866d-1920e9118d54.png)

보면 l2-svm와 adam을 사용한다고 했다. l2_svm을 구현하기 위해서 svm 학습에 사용되는 MultiMarginLoss를 사용하고 p값을 2로 바꾸어서 규제를 적용하는 방법을 사용할 예정이다.
그리고 논문에서는 제시하지 않았지만, 혹시나? 하는 생각에 adam에도 weight 값을 부여해서 l2규제를 적용했다.

## batch,dropout,등등
![스크린샷 2023-05-03 145222](https://user-images.githubusercontent.com/95357946/235841149-8c017b85-30dd-4ede-b160-dc5232a65108.png)

지금 보니까 내가 구현한 코드에서 batch를 100으로 설정했는데, 논문에서는 128로 제시했다. 


# 결과
![스크린샷 2023-05-03 145502](https://user-images.githubusercontent.com/95357946/235841415-79a55d76-226d-454a-9492-b550e3e09bd7.png)

음.... 역시 crossentropy가 짱이다. 약간 간소한 차이지만 여전히 cnn-svm의 성능이 약간 떨어진다.

# 출처
https://arxiv.org/abs/1712.03541
