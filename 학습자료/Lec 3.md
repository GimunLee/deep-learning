# Lec 3

# Gradient Descent Algorithm
- 경사를 따라 내려가며 최저점을 찾는 알고리즘
- cost를 최소화하는 W, b값을 찾기 위해 사용
- 장점: 변수가 여럿이어도 사용 가능
- 동작 과정
    1. 초기 W, b값 설정(cost function 그래프 상 임의의 한 점)
    2. cost가 줄어드는 방향(기울기 값을 구해서 cost가 최소화될수 있도록)으로 W, b값을 지속적으로 update
    3. cost가 최저점에 도달했다고 판단될때까지 반복
- 어느 지점에서 시작해도 같은 결과가 나온다
- 지점에서 기울기 값이 크면 더 많이 이동한다
- 기울기: 각 지점에서의 미분을 통해 구한다
- learning rate: W를 변화시킬 폭을 결정
    - 크다: W값의 변화폭이 크다
    - 작다: W값의 변화폭이 작다
- local minimum: 주변 점들과 비교했을때 cost 값이 가장 낮은 지점
- 문제점: local minimum과 global minimum이 일치하지 않을 수 있다
    - convex function: local minimum이 1개만 있는 함수 형태(global minimum과 local minimum이 항상 같은 함수)