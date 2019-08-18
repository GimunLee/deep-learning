

```python
import tensorflow as tf
tf.enable_eager_execution()
```

H(x) = Wx + b


```python
x_data = [1, 2, 3, 4, 5]
y_data = [1, 2, 3, 4, 5]

W = tf.Variable(2.9)
b = tf.Variable(0.5)
```

<hr>

Gradient Descent

- cost를 최소화하는 W, b를 찾는 알고리즘


```python
# learning_rate initialize
learning_rate = 0.01

# Gradient descent
for i in range(101):
    with tf.GradientTape() as tape:
        hypothesis = W * x_data + b
        cost = tf.reduce_mean(tf.square(hypothesis - y_data))

    # gradient(): cost 함수에 대해 W, b에 대한 개별 미분값을 구해 리턴
    W_grad, b_grad = tape.gradient(cost, [W, b])

    W.assign_sub(learning_rate * W_grad)
    b.assign_sub(learning_rate * b_grad)
    
    if i % 10 == 0:
        print("{:5}|{:10.4f}|{:10.4}|{:10.6f}".format(i, W.numpy(), b.numpy(), cost))
```

        0|    2.4520|     0.376| 45.660004
       10|    1.1036|  0.003398|  0.206336
       20|    1.0128|  -0.02091|  0.001026
       30|    1.0065|  -0.02184|  0.000093
       40|    1.0059|  -0.02123|  0.000083
       50|    1.0057|  -0.02053|  0.000077
       60|    1.0055|  -0.01984|  0.000072
       70|    1.0053|  -0.01918|  0.000067
       80|    1.0051|  -0.01854|  0.000063
       90|    1.0050|  -0.01793|  0.000059
      100|    1.0048|  -0.01733|  0.000055


점차 cost가 낮아지며 정확한 방정식을 찾고 있다.


```python
print(W * 5 + b)
print(W * 2.5 + b)
```

    tf.Tensor(5.00667, shape=(), dtype=float32)
    tf.Tensor(2.4946702, shape=(), dtype=float32)


W, b 값을 조정한 후 예측한 결과
