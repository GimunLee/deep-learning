# Lec 7

# Learning Rate
- Model을 만들기 위한 hyper-parameter
- gradient descent로 weight를 얼마나 많이 조절할지 결정
- learning rate가 큰 경우
    - gradient descent 폭이 크다
    - overshooting 발생 가능
- learning rate decay: 학습 과정에서 더이상 학습이 진행되지 않는 문제 해결
    - 학습 진행 중 learning rate를 조절하여 학습을 더 진행하는 방식
    - step decay: 특정 epoch마다 learning rate 조절
    - exponential decay
    - 1/t decay

# Data Preprocessing
- Feature Scaling
    - 불필요한 데이터(Noisy data)를 제거하기 위해 사용
    - Standardization
        - (x - 평균) / 표준편차
        - 평균에서부터 얼마나 많이 떨어져 있는가

        ![standardization](https://user-images.githubusercontent.com/23356503/58686879-09ea8c00-83bb-11e9-85be-24788fe93d26.png)
    - Normalization
        - (x - x최소값) / (x최대값 - x최소값)
        - 0과 1 사이의 값으로 나타낼 수 있다

        ![normalization](https://user-images.githubusercontent.com/23356503/58686937-2e466880-83bb-11e9-96a0-a38b1c17121f.png)
    - 예: 자연어 처리, 이미지 처리

# Overfitting
- 학습이 반복될수록 model의 accuracy는 증가하나 학습에 사용하지 않은 새로운 데이터를 사용했을때 정확도가 떨어지는 현상
- underfit
    - high bias: 모델이 과도하게 일반화된 경우
- overfit
    - high variance: 모델이 과도하게 학습 데이터에만 맞춰진 경우
- 해결 방법
    1. Feature Setting
        - 학습 데이터 수를 늘린다: 데이터를 다양화한다 (for overfit)
        - feature 수를 줄인다: 속성 수를 줄여 각각의 속성의 의미를 더욱 명확히 한다 (for overfit)
            - PCA: 차원을 축소하여 남은 속성의 의미를 분명히 한다
        - feature 수를 늘린다: 모델을 더 세분화한다 (for underfit)
    2. Regularization
        - loss function에 특정 값을 추가한다
        - term을 줄인다 (for underfit)
        - term을 늘린다 (for overfit)

        ![regularization](https://user-images.githubusercontent.com/23356503/58686970-40c0a200-83bb-11e9-9464-0ef40a7b0d2d.png)

# Dataset
- 전체 dataset을 학습용, 평가용으로 나눈다
- 주로 학습용 7, 평가용 3으로 나눈다
- Anomaly Detection
    - 정상적인 경우의 데이터만으로 학습시킨다
    - 비정상적인 경우의 데이터를 input으로 주면 비정상임을 감지하는 방식

# Learning
- Online Learning
    - 학습 중 데이터가 변하는 방식
    - 네트워크 연결 필요
    - 데이터가 변함에 따라 모델도 변한다
    - Weight도 동적으로 변화
    - Real time 환경
    - 우선순위: 속도
- Batch Learning
    - 정적인 데이터로 모델을 만드는 방식
    - 네트워크 연결 필요 없음
    - 정적인 모델
    - 정적인 Weight
    - 정적 환경
    - 우선순위: 정확도
- Fine Tuning
    - 새로운 데이터를 학습시켜 기존의 Weight 값을 미세하게 조정하는 방식
- Feature Extraction
    - 기존의 모델에서 새로운 task에 대해서만 새롭게 학습시키는 방식