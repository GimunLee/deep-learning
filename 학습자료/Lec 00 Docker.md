### Lec 00: Docker

---

- Docker란 : Container-based Virtualization System으로, 한 컴퓨터에서 여러 개의 운영체제를 구동하면 성능이 저하되는 것을 막기 위해, 알맹이(Linux Cernel)를 통일하고 어플리케이션 단(Containerized Application)을 가볍게 가상화한 것이다.

- 안내서 : <https://github.com/deeplearningzerotoall/TensorFlow/blob/master/docker_user_guide.md>

- IP : 192.168.99.100 (LGM)

- Docker Command 

  - Container 생성

    ```
    docker run -i -t --name tf -p 8888:8888 -p 6006:6006 deeplearningzerotoall/tensorflow
    ```

  - Container 상태 확인

    ```
    docker ps -a
    ```

  - Container 실행

    ```
    docker start [name]
    ```

  - Container 접속

    ```
    docker attach [name]
    ```

------

#### 