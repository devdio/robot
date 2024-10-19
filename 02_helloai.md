# HelloAI

## 카메라 표시

- 640 x 480
- top left (0, 0)
- bottom right : (640, 480)


```python
from helloai import *

wnd = Window('wnd')

# Using Camera
# 1. 640 x 480
# 2. 960x720
camera = Camera(size=(640, 480))
camera = Camera()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    
    # Display images read from the camera 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

    WARNING:tensorflow:From C:\work\miniconda3\envs\robot\lib\site-packages\keras\src\losses.py:2976: The name tf.losses.sparse_softmax_cross_entropy is deprecated. Please use tf.compat.v1.losses.sparse_softmax_cross_entropy instead.
    
    <HelloAI.Window Object Title:wnd, Size:((640, 480)) ,at memory location: (0x17fdbc8cac0)>
    __key__ esc
    

## 손 검출

<img src="https://camo.githubusercontent.com/cc87e384b553a0f19dcf8a36341b37a7081edc0b21b0d0ac364200b9e3bb98a1/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f68616e645f6c616e646d61726b732e706e67" />


```python
from helloai import *

wnd = Window('wnd')

# Using Camera
camera = Camera(size=(640, 480))

# Create and initialize Object 
detector = HandsDetector()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    # Recognize hand
    img, landmarks = detector.process(img, draw=True)

    # Display information about recognized hand
    # print(landmarks)
    
    # Display images read from the camera 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

### 검지 끝 좌표 표시 


```python
from helloai import *

wnd = Window('wnd')

# Using Camera
camera = Camera(size=(640, 480))

# Create and initialize Object 
detector = HandsDetector()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    # Recognize hand
    img, landmarks = detector.process(img, draw=True)

   if len(landmarks) > 0:
        print(landmarks[8])
    
    # Display images read from the camera 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

### 검지의 위치를 인식해서 카미봇 동작시키기 


```python
from helloai import *
from pyKamipi.pibot import *

# Connect to KamibotPi
kamibot = KamibotPi('COM3', 57600)

wnd = Window('wnd')

# Using Camera
camera = Camera(size=(640, 480))

# Create and initialize Object 
detector = HandsDetector()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    # Recognize hand
    img, landmarks = detector.process(img, draw=True)

   if len(landmarks) > 0:
        print(landmarks[8])

        index = landmarks[8]
        X = index[0]
        if X > 320:
            kamibot.go_dir_speed("f", 10, "f", 10)
        else:
            kamibot.go_dir_speed("b", 10, "b", 10)
   else:
       kamibot.stop()
    
    
    # Display images read from the camera 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

## 포즈 검출

<img src="https://camo.githubusercontent.com/d3afebfc801ee1a094c28604c7a0eb25f8b9c9925f75b0fff4c8c8b4871c0d28/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f706f73655f747261636b696e675f66756c6c5f626f64795f6c616e646d61726b732e706e67" />


```python
from helloai import *

wnd = Window('wnd')
camera = Camera(size=(640, 480))

detector = PoseDetector()

def loop():
    img = camera.read()

    # detect Pose 
    img, landmarks = detector.process(img, draw=True)
 
    if len(landmarks) > 0:
        # x16 = landmarks[16]  # left hand
        # print(x16)
        x15 = landmarks[15]  # right hand
        print(x15)


    # update image 
    wnd.show(img)

# ---------------------------------------
# for HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```
