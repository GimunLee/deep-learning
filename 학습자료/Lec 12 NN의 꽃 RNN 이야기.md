### Lec 12: NN의 꽃 RNN 이야기

---

- Sequence data : 현재 state가 다음 state에 영향을 미친다

  ![img](../resources/img/0603/img1.png)

- Recurrent Neural Network

  ![img](../resources/img/0603/img2.png)

- hello 데이터를 받았을 때,

  ![img](../resources/img/0603/img3.png)

- one-hot Encoding으로 벡터화

  ![img](../resources/img/0603/img4.png)

- Softmax를 이용한 결과 추론 

  ![img](../resources/img/0603/img5.png)

-  RNN 활용

  ![img](../resources/img/0603/img6.png)

  - Language Modeling : 연관 검색어
  - Speech Recognition 
  - Maching Translation : 번역 
  - Conversation Modeling/Question Answering : 챗봇
  - Image/Video Captioning 
  - Image/Music/Dance Generation :

- 복잡한 RNN 처리 : LSTM, GRU

---

### Lab 12-0 rnn basics

- keras를 활용한 RNN 구현

  - 1번째 방법

    ```
    cell = layers.SimpleRNNCell(units=hidden_size) rnn = layers.RNN(cell, return_sequences=True, return_state=True)
    outputs, states = rnn(x_data)
    ```

  - 2번째 방법

    ```
    rnn = layers.SimpleRNN(units=hidden_size, return_sequences=True, return_state=True) 
    outputs, states = rnn(x_data)
    ```

  ![img](../resources/img/0603/img7.png)

  - input에서 shape([batch size], [sequance length], [input demension])

---

### Lab 12-1 many to one (word sentiment classification)

- many to one : 자연어 처리에서 많이 씀

  ![img](../resources/img/0603/img8.png)

  ![img](../resources/img/0603/img9.png)

![img](../resources/img/0603/img10.png)

- token을 integer로 맵핑하는 token dictionary
- 각각의 시퀀스의 길이가 다르기 때문에 ['<pad>']라는 헤더를 달아줌
- 딥러닝은 배치단위 연산이 효율적임
- 1 : 긍정, 0 : 부정

![img](../resources/img/0603/img11.png)

- max_sequence에 맞춰 '0'으로 padding 된 것을 확인 할 수 있음

![img](../resources/img/0603/img12.png)

- 전처리 : Embedding
  1. mask_zero : 전처리 단계에서 '0'으로 처리된 부분을 연산에서 제외
  2. trainable : one-hot 벡터를 트레이닝 하지 않음

- SimpleRNN : 기본적으로 시퀀스의 마지막 토큰을 받아, 처리한 결과 리턴
- Dense : RNN을 Dense로 활용하도록 함

![img](../resources/img/0603/img13.png)

- cross_entropy를 이용하여 loss를 계산함

![img](../resources/img/0603/img14.png)

- 성능 확인

  ![img](../resources/img/0603/img15.png)

---

### Lab 12-2 many to one stacking

- Multi-layed RNN, Stacked RNN

  ![img](../resources/img/0603/img16.png)

---

### Lab 12-3 many to many

- 형태소 분석에 쓰임

  ![img](../resources/img/0603/img17.png)

  - Sequence loss를 백프로포게이션(?)으로 학습할 수 있다.

---

### Lab 12-4 many to many bidirectional

- bidirectional : 양방향으로 활용

  ![img](../resources/img/0604/img1.png)
  - forward RNN : hidden state가 가지고 있는 정보가 순차적
  - backward RNN :  forward RNN과 역순

- 활용 과정

  ![img](../resources/img/0604/img2.png)

  - forward와 backward hidden state의 정보를 컨키네이트(?)하는 방식으로 합치고 weight와 bias를 이용하여 값을 추출해낸다.
  - weight와 bias는 모든 데이터에서 동일하게 사용한다.
  - 구현은 12-3과 동일하지만, 함수 호출 중 bidirectional만 추가하면 됨

---

### Seq2Seq (Chat bot에서 활용)

- Seq2Seq : Sequence의 데이터를 받고 Sequence의 데이터를 반환하는 것

  ![img](../resources/img/0604/img3.png)

- Example : Chatbot

  ![img](../resources/img/0604/img4.png)

- 대표적인 활용 사례

  ![img](../resources/img/0604/img5.png)

  - input : 하나의 단어
  - c : RNN의 마지막 Hidden state 데이터 값 (Encoder 요약 값)
  - decoder : 각 스텝의 출력값이 다음 스텝의 입력값에 사용된다.

![img](../resources/img/0604/img6.png)

- 파란색 : Encoder / 초록색 : Decoder

### Chatbot 구현

1. sources를 targets으로 번역하는 dataset

![img](../resources/img/0604/img7.png)

2. Vocab Dict : 각각의 데이터를 integer로 맵핑

   ![img](../resources/img/0604/img8.png)

   - bos : 시작 토큰 / eos : 종료 토큰

3. 전처리 함수

   ![img](../resources/img/0604/img9.png)

   ![img](../resources/img/0604/img10.png)

4. suffle과 batch를 통해서 각 데이터를 설정해준다. 각 데이터는 시퀀스에 맞게 준비가 된다.

   ![img](../resources/img/0604/img11.png)

5. 인코더와 디코더의 기반이 되는 GRU 알고리즘 활용하는 알고리즘

   ![img](../resources/img/0604/img12.png)

   - CuDNNGRU : 랜덤값이 너무 작거나 크게 초기화되는 것을 방지해줌

6. 인코더 구현

   ![img](../resources/img/0604/img13.png)

7. 디코더 구현

   ![img](../resources/img/0604/img14.png)

8. Loss & Optimizer

   ![img](../resources/img/0604/img15.png)

9. Training

   ![img](../resources/img/0604/img16.png)

   - 티처 포싱은 다음장에

   - Training (Teacher Forcing)

     ![img](../resources/img/0604/img18.png)

     - 어렵다... 근데 중요한 듯!!

   ![img](../resources/img/0604/img19.png)

   - 예측

     ![img](../resources/img/0604/img21.png)

---

### Lab12-6: Seq2Seq Attention

- 기존 Seq2Seq의 문제점

  ![img](../resources/img/0605/img1.png)

  - 한개의 벡터값을 활용하는 것은 성능이 떨어진다.

- 모든 정보를 기억하지않고, 핵심 메세지와 문장만으로 이해한다.

  ![img](../resources/img/0605/img2.png)

![img](../resources/img/0605/img3.png)

---













 













