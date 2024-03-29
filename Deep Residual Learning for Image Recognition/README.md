# 내용
우선 이 논문을 한 문장으로 요약 하자면, DEGRADATION과 GRADIENT VANISHING을 SHORTCUT이라는 방법으로 해결했다.

# 실험 환경

실험관경은 다음과 같다.
## 논문에서는 다음과 같이 cnn 신경망의 모양을 정의한다. 

![](https://velog.velcdn.com/images/stockmanager1/post/22818887-5e43-4f28-839f-023043e1e896/image.png)


* 이거는 이런 단순하게 레이어를 쌓는 것으로는 구현이 매우 힘들다. 최대 152층까지 만들어야 하는데 따라서 우리는 DEF로 블록과 SHORTCUT을 정의하는 방법으로 구현해야 한다.
  
## 손실함수 및 옵티마이저
손실함수로 cross-entropy, 옵티마이저로 sgd를 사용한다.

 
 # 논문을 읽고 생각해야 하는 점
- 논문의 저자들이 달성하고자 하는 것이 무엇인가?
	--> 깊은 신경망은 높은 정확도를 수반한다는 말은 어느정도 맞지만 DEGRADTION과 GRADIENT VANISHING으로 틀리기도 하다. 따라서 이를 해결하기 위해 잔차를 학습하는 SHORTCUT을 구현해 해결했다.
    
- 접근방법의 가장 중요한 요소는 무엇인가?
--> F(X) + X 잔차함수에 입력값을 더하면서 진행. 이게 얼핏 보기에는 레이어를 건너 뛴다고 생각할 수 있는데, 그런 느낌이 아니라 잔차를 학습하는 것이다.

- 네 자신 스스로 무엇을 활용할 수 있는가?
--> 깊은 신경망 모델을 어떻게 처리할지 한번 다시 고민해보면 좋을 것 같다.

- 이후에 어떤 참고 논문들을 읽고 싶은가?
--> shortcut말고 다른 방법으로 해결한 사례가 DENSENET으로 알고 있다. 따라서 DENSENET을 읽어보면 좋을 것 같다.
