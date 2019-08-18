# Lec 5

# Logistic Regression
- 데이터를 구분하기 위해 사용(classification)
- 적용 가능한 데이터들의 특징: binary classification이 가능한 데이터
- Linear Regression과의 차이
    - Linear Regression: 데이터들이 연속적이다(Numeric)
    - Logistic Regression: 데이터가 흩어져있고 구분이 가능하다(One hot)
- 데이터를 Logistic Function으로 나타낸 후 decision boundary를 적용해 classification 실행
- Neural Network의 하나의 component

# Sigmoid Function
- g function
- linear regression을 통해 얻은 값을 sigmoid function을 통해 0, 1로 변환한다
- decision boundary: 데이터 구분을 위한 경계
    - linear / non-linear function 관계없이 설정 가능

![Sigmoid Function](https://user-images.githubusercontent.com/23356503/58540631-bb12ea00-8234-11e9-82f5-dd5db7bd21ca.png)

# Cost Function
- 초기의 random한 W값을 fitting하기 위함
- Sigmoid Function의 값 - binary classification한 값이므로 그래프의 형태가 구부러진 형태가 된다
![Cost Function](https://user-images.githubusercontent.com/23356503/58540707-e4337a80-8234-11e9-8e42-deb17108b3c3.png)
- 형태
    - 예측값이 1이면: cost(h(x), y) = -log(h(x))
    - 예측값이 0이면: cost(h(x), y) = -log(1 - h(x))
- Optimization: cost function 값을 최소화하는 작업
    - Gradient Descent를 통해 최적화
