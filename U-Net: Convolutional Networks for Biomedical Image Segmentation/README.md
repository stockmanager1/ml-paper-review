# 논문요약
현재 존재하는 모든 인공지능 모델의 기본이 되는 cnn 모델이다. gpu 병렬화, dropout, resize, centercrop, randomcrop, horizon flip등 여러 조작을 가했다. imagenet의 크기가 너무 방대한 관계로 모든 imagenet 파일을 학습하지는 못했고, 구조와 흐름만 구현하게 되었다.
# 실험 환경

실험관경은 다음과 같다.
## 논문에서는 다음과 같이 cnn 신경망의 모양을 정의한다. 

![image](https://github.com/stockmanager1/ml-paper-review/assets/95357946/60489433-d0ac-4f18-b597-ead4245ad1de)

![스크린샷 2023-07-16 223244](https://github.com/stockmanager1/ml-paper-review/assets/95357946/f9326dcd-bfc5-4c99-95b7-580e73000e2e)

* The first convolutional layer filters the 224×224×3 input image with 96 kernels of size 11×11×3 with a stride of 4 pixels
* The second convolutional layer takes as input the (response-normalized and pooled) output of the first convolutional layer and filters it with 256 kernels of size 5 × 5 × 48.
* The third, fourth, and fifth convolutional layers are connected to one another without any intervening pooling or normalization layers
* The third convolutional layer has 384 kernels of size 3 × 3 × 256 connected to the (normalized, pooled) outputs of the second convolutional layer
*  The fourth convolutional layer has 384 kernels of size 3 × 3 × 192 , and the fifth convolutional layer has 256 kernels of size 3 × 3 × 192. The fully-connected layers have 4096 neurons each.
*  We use dropout in the first two fully-connected layers 
  
|구조|cnn구조|maxpooling|stride|BatchNormalization|
|---|---|---|---|---|
|first convolutional layer|96개 커널, 11*11 사이즈|2*2|stride=4|사용|
|second convolutional layer|256개 커널, 5*5 사이즈|2*2|내용 8|사용|
|third convolutional layer|384개 커널, 3 * 3 사이즈|없음|없음|없음|
|fourth convolutional layer|384개 커널, 3 * 3 사이즈|없음|없음|없음|
|fifth convolutional layer|256 커널, 3 * 3 사이즈|없음|없음|사용|
|sixth fully-connected layer|4096|없음|없음|dropout 사용|
|seventh fully-connected layer|1000|없음|없음|dropout 사용|


마지막에 softmax 함수를 적용해야 하는데, 정리하면서 보니까 그걸 깜박했다. 
## 손실함수 및 옵티마이저
손실함수로 cross-entropy, 옵티마이저로 sgd를 사용한다.

## batch,dropout,등등
 논문에서 batch_size를 128로 제시했다.

 dropouut은 첫번쨰 완전연결층, 두번째 완전연결층에 적용한다.


# 출처
[https://arxiv.org/abs/1712.03541](https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf)https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf
