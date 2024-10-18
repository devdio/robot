# Kamibot

-  [pyKamipi API](https://pypi.org/project/pyKamipi/)


### Forward


```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM11', 57600)

kamibot.go_dir_speed("f", 10, "f", 10)
kamibot.delay(3)
kamibot.stop()

# disconnect to KamibotPi
# kamibot.close()
```

### Backward


```python
# from pyKamipi.pibot import *

# kamibot = KamibotPi('COM11', 57600)

kamibot.go_dir_speed("b", 10, "b", 10)
kamibot.delay(3)
kamibot.stop()

# disconnect to KamibotPi
# kamibot.close()
```

### Turn Left/Right
제자리 돌기


```python
# from pyKamipi.pibot import *
# kamibot = KamibotPi('COM11', 57600)

kamibot.turn_right_speed(90, speed=100)
kamibot.delay(1)
kamibot.stop()

# disconnect to KamibotPi
# kamibot.close()
```


```python
# from pyKamipi.pibot import *
# kamibot = KamibotPi('COM11', 57600)

kamibot.turn_left_speed(90, speed=100)
kamibot.delay(1)
kamibot.stop()

# disconnect to KamibotPi
# kamibot.close()
```

### 정밀 이동
일정 거리 이동 


```python
# from pyKamipi.pibot import *
# kamibot = KamibotPi('COM11', 57600)

kamibot.move_forward_unit(10, "-l") # 10cm
kamibot.delay(1)
kamibot.stop()
```


```python
# from pyKamipi.pibot import *
# kamibot = KamibotPi('COM11', 57600)

kamibot.move_backward_unit(10, "-l") # 10cm
```

### 좌우 바퀴 속도 지정 


```python
kamibot.go_forward_speed(50, 100)
kamibot.delay(1)

kamibot.go_backward_speed(100, 50)
kamibot.delay(1)
kamibot.stop()
```

### LED


```python
kamibot.turn_led(255, 0, 0)
kamibot.delay(1)
kamibot.turn_led(0, 255, 0)
kamibot.delay(1)
kamibot.turn_led(0, 0, 255)
kamibot.delay(1)
```

### Beep


```python
kamibot.beep()
kamibot.beep()
kamibot.beep()
```

### 장애물 감지 센서


```python
left, right = kamibot.get_object_detect()
print(f"left={left}, right={right}")
kamibot.delay(1)
kamibot.get_object_detect(False)
```

    left=0, right=0
    




    (0, 0)



### 탑모터 제어


```python
# ------------------------------------------------
# 탑모터 제어  top_motor_degree
# ------------------------------------------------
kamibot.top_motor_degree("l", 180)  # 왼쪽 방향으로
kamibot.delay(1)

kamibot.top_motor_degree("r", 180)  # 오른쪽 방향으로
kamibot.delay(1)
```

### END


```python

```
