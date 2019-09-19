# Lec 9

# Solving XOR Problem with Neural Network
- Neural Network: layer별로 각각의 weight, bias를 가진다
- Forward Propagation으로 해결 가능
    ![Forward Propagation](https://user-images.githubusercontent.com/23356503/58780188-254fd400-8613-11e9-81cc-e220506eacf7.jpg)
- layer가 늘어나며 W, b의 차원이 증가 => Multinomial Classification처럼 행렬 곱으로 처리
- 구현 형태
    ![Neural Network](https://user-images.githubusercontent.com/23356503/58780404-cccd0680-8613-11e9-80c5-08c4c44f369b.png)

# Backpropagation
- NN의 각각의 layer들을 어떻게 학습시킬 것인가: layer가 늘어나며 gradient descent 과정이 복잡해진다
- 예측값과 출력값을 비교한 후 계산된 cost 값을 뒤에서부터 앞으로 돌려서 미분값과 실제로 조절할 값 계산
- 해결: backpropagation을 활용하여 복잡한 미분 계산
- f = wx + b, g = wx => f = g + b로 정의
    ![Back Propagation](https://user-images.githubusercontent.com/23356503/58781275-744b3880-8616-11e9-88cb-cfa0dbc0ad83.png)
    - chain rule을 활용하여 f에 가장 가까운 layer부터 미분을 진행하며 다음 layer 미분 진행
    - 결과: 최종적으로 x, y가 f에 미치는 영향을 알 수 있다
