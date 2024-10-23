# HelloAI 그리기 기능

## 윈도우에 도형(선, 원, 사각형) 그리기
```python
from helloai import *

win = Window('helloAI')

def loop():
    win.line((0, 0), (100, 100), Color.RED)
    win.line((100, 100), (200, 400), Color.GREEN, 5)
    win.line((20, 0), (120, 100), (0, 255, 255), 15)
    
    # ellipse(<타원의 중심>, <원의 폭>, <원의 높이>, <윤곽선의 색상>, <칠하기색상>, <윤곽선두께> )
    center = (win.width/2, win.height/2)
    win.ellipse(center, 100, 100, (255,0,0), (0, 255, 0), 3)
    
    # rectangle(<시작좌표>, <끝좌표>, <윤곽선 색상>, <칠하기색상>, <윤곽선 두께>)
    x0 = win.width - 200
    y0 = win.height - 200
    win.rectangle((x0, y0), (win.width, win.height), (255, 0, 0), (255, 255, 0), 5)

    win.show()


if __name__ == '__main__':
    run()

```

## 이미지에 텍스트(글자) 표시하기

```python
import math

wnd = Window('wnd')

# 카메라 객체
camera = Camera()

# 무한 반복 
def loop():
    # 카메라 영상 읽기
    img = camera.read()

    # text(시작좌표, 글자크기, 색상)
    img = img.text((0,0), text='HelloAI', size=40, color=(255,255,255))
    
    # 이미지 표시 
    wnd.show(img)

# ---------------------------------------
# HelloAI를 사용하기 위한 실행 방법 
# ---------------------------------------
if __name__ == '__main__':
    run()
```

## 이미지를 읽어서 표시하기
```python
from helloai import *

wnd = Window('Friend')

# 이미지를 읽어옴 
img = load_image('C:/Temp/friends.png')
 
def loop():
    # 이미지 표시 
    wnd.show(img)


if __name__ == '__main__':
    run()
```

```python
from helloai import *

wnd = Window('Friend')
wnd2 = Window('gray')
wnd3 = Window('rgb')

# 이미지 변수 정의 
img = load_image('C:/Temp/friends.png')
# 이미지 크기를 반으로 줄인다.
img = img.scale(0.5)
 
def loop():
    global img
    
    # 이미지를 Gray로 바꿈
    gray = img.to_gray()
    # 이미지를 RGB로 바꿈 
    rgb = img.to_rgb()

    # 이미지 표시 
    wnd.show(img)
    wnd2.show(gray)
    wnd3.show(rgb)
    

if __name__ == '__main__':
    run()
```

## 10% 확률로 발생하는 이벤트 만들기
```python
from helloai import *

win = Window('helloAI')
x_val = 0
color = (255, 215, 0)

# 무한 반복 코드 
def loop():
    global x_val, color 

    win.background((0, 0, 0))
    num = random(10)
    if num == 0:
        color = (random(256), random(256), random(256))
    
    win.ellipse((x_val, win.height/2), 100, 100, color)
    x_val = x_val + 5

    # 창을 벗어나는지 확인 
    if x_val > win.width :
        x_val = 0
    
    win.show()


if __name__ == '__main__':
    run()
```



