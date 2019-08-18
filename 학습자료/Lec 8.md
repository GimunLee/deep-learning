# Lec 8

# Activation Function
1. 특정 신호가 들어온다
2. 그 신호에 weight을 곱한 후 전부 더한다
3. 총합에 bias를 더한다
4. 계산 결과가 특정 값 이상일 경우 1, 아니면 0의 신호를 준다

# XOR Problem
- AND, OR의 결과값은 선형 함수로 separate할 수 있다
- XOR의 결과값은 선형 함수로 separate할 수 없다
    - 여러개의 선형 함수로는 가능: MLP(Multi Layer Perceptron) 필요
    - MLP를 어떻게 학습시킬것인가

# Backpropagation
- Multi Layer의 앞에서 구한 error를 토대로 뒤쪽 layer를 training해나가는 방법
- 문제점: layer 수가 늘어나면 제대로 동작하지 않는다 - layer 수가 늘어날수록 성능 감소

# Convolutional Neural Network
- 그림을 한번에 입력시키지 않고 잘라서 각각의 layer에 보낸 후 나중에 합치는 방법
- 문자, 숫자 인식에 주로 사용
- 사진 분류, 사진 설명도 가능
