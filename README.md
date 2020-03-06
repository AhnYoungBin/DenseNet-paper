# Densely Connected Convolutional Networks
============================================================================
논문 링크 : <https://arxiv.org/pdf/1608.06993.pdf> 


Dense Connectivity
------------------

입력에 가까운 layer와 출력에 가까운 layer 사이에 shorter connection이 포함되면, 더 깊고 정확하면서 효율적으로 학습할 수 있다. 이 논문에서는 이러한 관찰을 받아들여, feed-forward 방식으로 각 layer를 다른 모든 layer에 연결한 DenseNet을 소개한다. 이전 layer들의 feature map을 계속해서 다음 layer의 입력과 연결하는 방식이며 이러한 방식은 ResNet에서도 사용이 되었습니다.하지만 ResNet은 feature map 끼리 add 를 해주는 방식이었다면 DenseNet은 feature map끼리 Concat을 시키는 것이 가장 큰 차이점입니다. 이러한 구조를 통해 얻을 수 있는 이점은 다음과 같습니다.
* Vanishing Gradient 개선
* Feature Propagation 강화
* Feature Reuse
* Parameter 수 절약

Growth Rate
-----------
<img src="/image/1.JPG" width="80%" height="80%" title="img1" alt="img1"></img>    

각각 feature map끼리 densely 연결이 되는 구조이다 보니 자칫 feature map의 channel 개수가 많은 경우 계속해서 channel-wise로 concat이 되면서 channel이 많아 질 수 있습니다. 그래서 DenseNet에서는 각 layer의 feature map의 channel 개수를 굉장히 작은 값을 사용하며, 이 때 각 layer의 feature map의 channel 개수를 growth rate(k) 이라 부릅니다.  



BottleNeck Layer
----------------
<img src="/image/2.JPG" width="80%" height="80%" title="img1" alt="img1"></img>    

ResNet 과 inception 등에서 사용되는 Bottleneck layer 아이디어도 DenseNet에서 사용하였다. 1x1 Convolution layer에서 dimension을 줄여 Feature map의 갯수를 줄였다가 그 뒤 growth rate 만큼의 feature map을 생성하여 c

