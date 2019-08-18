# Lec 2

# Regression

- 어떠한 크기의 데이터가 나와도 이 데이터들은 전체 평균으로 회귀하려는 속성이 있다.
- 데이터간 관계를 해석하는것



# Linear Regression

- 목표: 데이터를 가장 잘 나타낼 수 있는 직선형 방정식을 찾는것

- Hypothesis(가설): 데이터를 가장 잘 나타낼 것으로 예측되는 직선 방정식 - H(x) = Wx + b

- Cost: 가설과 실제 데이터간의 차이(loss, error)

![Cost Function](https://user-images.githubusercontent.com/23356503/58540467-64a5ab80-8234-11e9-8ec3-dee58530cc23.png)

  m: 전체 데이터 수

  cost function: 전체 cost 제곱의 평균

- learning: Cost를 최소화하는 W, b를 찾는것
