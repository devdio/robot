# Basic
## Move

### move forward
```python
from roboid import *

albert = AlbertAi()

# move_forward()
albert.move_forward()
wait(300)

# move_forward(cm)
albert.move_forward(10)
wait(3000)

# move_forward(cm, velocity 100%)
albert.move_forward(10, 100)
```
### move backward

```python
move_backward()
move_backward(cm)
move_backward(cm, velocity)
```

### move for sec
```python
move_forward_sec(2)
move_forward_sec(2, 50)

move_backward_sec(2)
move_backward_sec(2, 50)
```

### turn

```python
turn_left()
turn_left(degree)
turn_left(degree, velocity)

turn_right()
turn_right(degree)
turn_right(degree, velocity)

```

### pivot 

```python
# Turn around the left wheel
pivot_left(degree)
pivot_right(degree)

pivot_left_sec(sec)
pivot_right_sec(sec)
```

### control wheels

```python
wheels(velocity)
wheels(left_velocity, right_velocity)
stop()
```






