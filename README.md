# AI-paper-review

인공지능논문을 공부합니다.

# 논문 읽기와 ML/DL 커리어 경력에 대한 조언 by 앤드류 응

1. 논문 리딩습관을 발전시키자 : 한 주에 1개씩 읽는 것으로 시작하자.

2. 효율적으로 논문을 읽자 : 읽을 논문 리스트를 만들고, 취사선택을 하자.

3. 논문을 읽을 때 : title, abstract, figures, introduction, conclusion을 읽는 것으로 시작하자.

4. 알고리즘을 이해하기 위해 : 수식을 직접 쓰면서 이해하고 밑바닥부터 코드로 구현해보자.

5. 지속적으로 공부하자 : ML/DL 컨퍼런스나 온라인을 활용하여 최신 논문들을 확인하자

6. AI분야의 T자 모양 지식 체계를 갖춰나가자.



# 논문 보는 곳들

1. 트위터 :

2. ML subreddit (https://www.reddit.com/r/MachineLearning/)

3. ML/DL 컨퍼런스 : NIPS/ICML/ICLR 

4. 각종 커뮤니티or그룹(우리에겐 텐플코같은 곳이겠죠?)

## 논문을 읽고나면 다음 질문에 답해보세요.

1. 저자가 뭘 해내고 싶어했는가?

2. 이 연구의 접근에서 중요한 요소는 무엇인가?

3. 당신(논문독자)은 스스로 이 논문을 이용할 수 있는가? 

4. 당신이 참고하고 싶은 다른 레퍼런스에는 어떤 것이 있는가?


# 출처

https://media-ai.tistory.com/7

# 논문 목록

## 이미지 classification
이미지를 분류하는 논문 구현 목록입니다.
| 논문 제목 | 내용 | 링크 | 언어 |
|------|------|------|------|
| An Architecture Combining Convolutional Neural Network (CNN) and Support Vector Machine (SVM) for Image | softmax 대신 svm을 사용하면 어떨까? 라는 내용인데 성능이 softmax보다 떨어집니다. | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/An%20Architecture%20Combining%20Convolutional%20Neural%20Network%20(CNN)%20and%20Support%20Vector%20Machine%20(SVM)%20for%20Image) |*pytorch*|
| ImageNet Classification with Deep Convolutional Neural Networks | 인공지능의 가장 기초인 alexnet을 구현한 논문입니다. gpu 병렬화, dropout이 소개되었습니다. | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/ImageNet%20Classification%20with%20Deep%20Convolutional%20Neural%20Networks) |*keras*|
| Deep Residual Learning for Image Recognition | resnet을 구현한 논문입니다. 모델의 깊이에 따른 degradation, gradient vanishing 문제를 해결하기 위해 shortcut과 잔차 학습을 소개합니다.  | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/Deep%20Residual%20Learning%20for%20Image%20Recognition) |*pytorch*|


## 이미지 segmentation 
이미지를 분류하는 논문 구현 목록입니다.
| 논문 제목 | 내용 | 링크 | 언어 |
|------|------|------|------|
| U-Net: Convolutional Networks for Biomedical Image Segmentation | u자 형태의 구조로 downsampling으로 이미지 피처를 축소하고 upsampling으로 이미지를 복원하면서 segmentation을 진행한다. | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/U-Net%3A%20Convolutional%20Networks%20for%20Biomedical%20Image%20Segmentation) |*tensorflow*|

## 시계열  
시계열 모델
| 논문 제목 | 내용 | 링크 | 언어 |
|------|------|------|------|
| Long term 5G network traffic forecasting via modeling non-stationarity with deep learning | smoothing attention을 통해서 데이터를 스케일링해 비정형성 데이터를 stable data로 변경, difference attention으로 각 타임 스탬프 간의 상관관계를 파악해 학습을 진행 | [링크](https://github.com/stockmanager1/Diviner-Nonstationary-time-series-forecasting/tree/main) |*pytorch(저자의 코드를 개조)*|

## 기타
구현보다는 라이브러리 소개나 좀 개념적인 부분을 강조하는 논문입니다.
| 논문 제목 | 내용 | 링크 | 
|------|------|------|
| Data-driven advice for applying machine learning to bioinformatics problems | 데이터마다 다른 모델을 적용해야 함. 절대적인 모델은 없다. 튜닝의 중요성. automl 사용 권고 언급 | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/Data-driven%20advice%20for%20applying%20machine%20learning%20to%20bioinformatics%20problems) |
| AugLy: Data Augmentations for Robustness | 페이스북에서 만든 증강 라이브러리 소개 글이다. 기능이 많기는 한데(이미지, 비디오, 글자 등) 잘 쓰는지는 모르겠다.  | [링크](https://github.com/stockmanager1/ml-paper-review/tree/main/AugLy%3A%20Data%20Augmentations%20for%20Robustness) |
