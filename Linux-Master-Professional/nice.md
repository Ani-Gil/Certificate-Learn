Command - nice
===============
프로세스의 우선순위를 변경하는 명령어로 NI 값을 설정할 때 사용한다. 해당 명령어는<br>
일반 사용장의 경우 NI 값을 증가하는 것만 가능하고 root 사용자만이 NI 값을 <br>
감소시켜 우선순위를 높일 수 있다.<br>

1. 명령어 사용 형태<br>
nice [Option] [Process Name]

2. 명령어 옵션

| Option | Document |
|--------|----------|
| -[vaule]     | 프로세스에 설정된 NI 값을 지정한다. 값을 지정하지 않으면 기본적으로<br> 10 만큼 증가된다. |

3. 명령어 사용 예<br>
    - nice --10 bash<br>
    "bash"라는 프로세스의 NI 값을 10만큼 차감시켜 우선 순위를 높인다.
    - nice bash<br>
    "bash"라는 프로세스의 NI 값을 10만큼 증가시켜 우선 순위를 낮춘다.

4. 알아둘 점<br>
    - 명령어가 실행될 시, 특정 값으로 설정되는게 아니라 증감 연산을 통해 NI 값이<br>
    수정된다. 이 즉은, 0이라는 상태에서 '--10'을 진행하게되면 '-10'이라는 값을 가지고,<br>
    여기서 '-3'을 진행하게되면 '-7'이라는 값이 진행된다. 즉 증감 연산으로 작동된다.
    - 명령어가 실행되면 기존 프로세스의 NI 값이 조정되는 것보다 조정된 값으로된<br>
    새로운 프로세스가 생기는 형태이다. 하지만 "renice" 명령어는 기존 프로세스를<br>
    지정한 NI 값으로 바꾸는 형태이다.
    - 해당 nice 명령어는 프로세스 명으로 NI 값을 조정된다는 사실을 기억하고,<br>
    renice 명령어는 프로세스 ID, 즉 PID로 조정되는 것을 기억하자.