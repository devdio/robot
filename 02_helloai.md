# HelloAI

프로그램을 종료할 경우
1. 카메라 화면이 표시되고 있는 경우는 카메라화면을 한번 클릭한 후, 키보드 `Q` 또는 `q`를 입력하면 된다.
2. 화면이 표시되지 않는 프로그램은 터미널에서 `Control + C` 를 입력한다.
  
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
camera = Camera(flip=1, size=(640, 480))


# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    
    # Display images read from the camera 
    wnd.show(img)

def end():
    # 프로그램이 끝나기 직전에 호출되는 함수
    print('***** END *****')

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```
    

## 손 검출

<img src="https://camo.githubusercontent.com/cc87e384b553a0f19dcf8a36341b37a7081edc0b21b0d0ac364200b9e3bb98a1/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f68616e645f6c616e646d61726b732e706e67" />


```python
from helloai import *

wnd = Window('wnd')

# Using Camera
camera = Camera(flip=1, size=(640, 480))

# Create and initialize Object 
hands = HandsDetector()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    # Recognize hand
    img, landmarks = hands.process(img, draw=True)

    # Display information about recognized hand
    # print(landmarks)
    
    # Display images read from the camera 
    wnd.show(img)

def end():
    # 프로그램이 끝나기 직전에 호출되는 함수
    pass

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

## 포즈 검출

<img src="https://camo.githubusercontent.com/d3afebfc801ee1a094c28604c7a0eb25f8b9c9925f75b0fff4c8c8b4871c0d28/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f706f73655f747261636b696e675f66756c6c5f626f64795f6c616e646d61726b732e706e67" />

위의 그림과 좌우가 반대로 동작한다.

- 15 : right wrist
- 16 : left wrist
  
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

## 얼굴 검출



<img src="https://ai.google.dev/static/edge/mediapipe/images/solutions/examples/face_detector.png?hl=ko" />

- 0 : left eye, 1: right eye, 2: nose, 3: mouth, 4: left ear, 5: right ear

```python
from helloai import *

wnd = Window('wnd')
camera = Camera(flip=0, size=(640, 480))

detector = FaceDetector()

def loop():
    img = camera.read()

    # detect Face 
    img, landmarks = detector.process(img, draw=True)
    
    if len(landmarks) > 0:
        print('Landmarks : ', landmarks[0])
        print('BoundBox : ', landmarks[0]['bound'])
        print('KeyPoints : ', landmarks[0]['keypoints'])


    # update image 
    wnd.show(img)

# ---------------------------------------
# for HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()

```
