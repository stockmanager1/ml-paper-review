# 논문요약
요즘 최근 진행한 융함 캡스톤 프로젝트를 시작으로 object detection 분야에 관심을 가지게 되었다. 그러다가 우연히 든 생각이 yolo에서 사용하는 bbox 형식의 분류말고 객체 자체를 누끼 따듯 표시하는 방법은 없을까 찾다가 object segmentation 이라는 이미지 분류 방법론이 있다는 것을 알게 되었다. 따라서 이번에 관련 논문인 u-net에 대해 읽게 되었다, u-net은 적은 데이터 셋으로 segmentation task를 수앻한다. 따라서 논문에서는 여러 데이터 증강이 사용된다. 그리고 약 23개의 layer가 사용되는데, 축소 구간과 확대구간으로 나누어진다.

# 직접 구현 실패
음.... 한 2일정도 이것만 매달렸는데, 결국 upsampling 부분으로 넘어가는 부분에서 차원이 달라 계속 오류를 경험하게 되었다. 일일이 차원 계산을 해도 다 맞던데 왜 아닌지 진짜 모르겠다. 그리고 좀 고쳤다 하면 계속 차원이 하나더 추가되는 현상이 발생한다. 그리고 segmentation은 일반적인 이미지 분류나 객체 인식과 달리 이미지를 전처리 하는 과정이 다르다는 것을 알게되었다. 따라서 이번에는 kaggle opensource를 참고해서 구현했다.


# 실험 환경

실험관경은 다음과 같다.
## 논문에서는 다음과 같이 신경망의 모양을 정의한다. 

![image](https://github.com/stockmanager1/ml-paper-review/assets/95357946/addb67df-056e-4b54-976a-68b2fa3fe09e)


크게 모델은 축소 경로와 확대 경로로 나누어 집니다. 축소 경로의 경우, 각각 3 * 3 conv2d를 각 층마다 2개씩 가지고, maxpooling을 2 * 2로 가지게 됩니다. 그리고 필터가 2,4,8 이런 식으로 증가합니다. 그리고 마지막 층에 dropout을 추가합니다. 축소 경로에 대한 정의가 끝난다면, 다음으로 concatenate 함수를 통해서 축소경로와 확대경로를 연결된다.  확대 경로는 축소 경로와 마찬가지로 2개의 3 * 3 conv2d를 가지게 됩니다. 하지만 upsampling을 해야 하는데, 이걸 Conv2DTranspose를 통해 구현됩니다. 그리고 위에서 아키텍처 그림과 마찬가지로 copy and crop을 concatenate로 구현해서 수축과 확대를 연결합니다.
## 손실함수 및 옵티마이저
손실함수로 cross-entropy, 옵티마이저로 sgd를 사용한다.

## 데이터 증강
적은 데이터 수를 극복하기 위해 overlap-tile strategy 등 여러 데이터 증강 방법을 제시했다. overlap-tile strategy이란 하나의 이미지를 여러개로 쪼개서(여기 논문에는 3 * 3 grid로 분할하고 각 patch에 대해 가우시안 정규 분포를 사용한다) 조작을 가한다. 이걸로 배치 사이즈를 1로 만든다.


# 내가 처음에 구현을 실패한 이유

1. concatenate 함수의 필요성과 이 함수가 정확하게 무엇을 지칭하는지 몰랐다.

2. Conv2DTranspose 이 코드가 upsampling 코드인지 몰랐다.

3. 이런 축소 확대 구조는 각 부분을 함수로 정의하고 구현하는 것이 매우 편리한 것을 몰랐다. 그러니까 중간에 차원에 대한 실수가 있었다.

# 출처
https://arxiv.org/pdf/1505.04597.pdf

https://www.kaggle.com/code/mrsohelranapro/aerial-semantic-segmentation-drone-detection



