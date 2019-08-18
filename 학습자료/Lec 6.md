# Lec 6

# Multinomial Classification
- binary classification을 여러번 수행하는 방식
- 각각의 classifier를 만드는 대신 softmax를 활용해 한번에 처리 가능

# Softmax
- 예측 결과가 여러 label에 대해 각각의 label에 속할 확률로 나타남(결과값 합 = 1)
    - one hot encoding 적용하면 가장 큰 확률만 1로 나타나고 나머지는 0으로 나타남

# Cost function
- cross entropy: softmax 결과 예측한 값과 실제 label 값의 차이를 구하기 위해 사용
![cost function](https://user-images.githubusercontent.com/23356503/58613512-e8bd6900-82f0-11e9-934d-6ebed277232d.png)
    - y: 실제 label 값
    - p: softmax를 통해 예측한 값
    - y와 p의 각각의 element를 곱한 후 모든 element의 값을 합하는 방식
    - 예측이 맞았을 경우
    ![correct](https://user-images.githubusercontent.com/23356503/58613727-7731ea80-82f1-11e9-991d-aee9cb09a214.png)
    - 예측이 틀렸을 경우
    ![incorrect](https://user-images.githubusercontent.com/23356503/58613873-ced05600-82f1-11e9-819b-b06164cb6e70.png)
    - 예측이 맞으면 0, 틀리면 매우 큰 값이 된다
- gradient descent를 통해 cost를 최소화한다
