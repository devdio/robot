# Sensor

### Eye Color

```python
# Red, Orange, Yellow, Green, Sky_blue
eye(color)
eye(left_color, right_color)
left_eye(color)
right_eye(color)
```
```python
albert.eyes(255, 0, 0, 0, 255, 0) # left: red and right: green
wait(500) # 0.5 seconds

albert.eyes(0, 0, 255) # both: blue
wait(500) # 0.5 seconds

albert.eyes("off") # turn off both eyes
```

### Proximity sensor
```python
# 0 ~ 255
left_proximity()
righ_proximity()
```

```python
from roboid import *

albert = AlbertAi()

# wait while the value of the left proximity is less than 30
while albert.left_proximity() < 30:
    wait(10) # 10 msec

# move backward 5 cm with beep sound
albert.sound("beep")
albert.move_backward() 

```

```python
from roboid import *

albert = AlbertAi()

hz = 0
while True:
    proximity = albert.left_proximity()
    if proximity < 10:
        proximity = 0
    hz = (hz * 5 + proximity * 50) / 10.0
    albert.buzzer(hz)

    wait(20) # 20 msec
```


### light sensor
```python
light()

```

### sound
```python
sound(s_id)
sound(s_id, count)
```
s_id : BEEP,  SIREN

```python
from roboid import *

albert = AlbertAi()

# play sound and wait until done
albert.sound_until_done("siren")

# random beep: 3 times
albert.sound_until_done("random beep", 3)

albert.sound_until_done("robot")
```
```python
from roboid import *

albert = AlbertAi()

while True:
    if albert.mic_clicked():
        albert.sound('beep')
    if albert.volume_up_clicked():
        albert.sound('noise')
    if albert.volume_down_clicked():
        albert.sound('siren')
    if albert.play_clicked():
        albert.sound('engine')
    if albert.back_clicked():
        albert.sound('robot')

    wait(10)
```
