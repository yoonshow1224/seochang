# 휠체어 사용자를 위한 AI 기반 회전문 감속 및 안전 장치 시스템

### 목적
자동 회전문이 회전할 때 휠체어가 이동하기에 위험할 수 있기 때문에 AI기반 자동 감속 시스템을 제시했다.

### 사용 기술 및 개발 도구
* yolov8
* Ubuntu
* 웹캠
* 회전문

### 처리 과정
1. 라즈베리파이 웹캠으로 카메라 정보를 수집한다.
2. YOLOv8을 통해 휠체어가 감지되었는지 확인한다.
3. 서버를 사용하지 않고 라즈베리파이 자체에서 휠체어가 감지되었는지 확인하고 이에 따라 레이더 센서를 조작한다.
4. 레이더 센서를 통해 휠체어의 이동속도를 감지하고 감지한 속도에 따라 회전문 속도를 변경시킨다.

### 과정
roboflow를 통해 이미지를 학습했다.

Roboflow 데이터셋을 YOLOv8 형식으로 변환
train/images, train/labels, valid/images, valid/labels
구조로 다운로드

Roboflow의 "YOLOv8 데이터셋 내보내기(Export)" 기능, 학습은 YOLOv8에서 직접 진행했다.
**가상환경 세팅**
```
# 가상환경 생성
python3 -m venv venv

# 가상환경 활성화
source venv/bin/activate
cd ~/Downloads/wheelchair.v1i.yolov8

# YOLOv8 설치
pip install ultralytics

cd ~/Downloads/wheelchair.v1i.yolov8
```
**라이브러리 설치**
```
` pip install roboflow ultralytics `
` python3 -m venv yolo `
```
**YOLO8 학습**
```
yolo detect train model=yolov8n.pt data=data.yaml epochs=100 imgsz=640
```

**학습 후 테스트**
```
이미지 판별
  yolo detect predict \
  model=runs/detect/train/weights/best.pt \
  source=valid/images
웹캠으로 보기 
source ~/venv/bin/activate

yolo detect predict \
    model=runs/detect/train/weights/best.pt \
    source=0
```

**테스트 결과**

<img width="320" height="351" alt="image" src="https://github.com/user-attachments/assets/47796a7c-b4e9-4072-987d-36dfe2becb1e" />

<img width="210" height="272" alt="image" src="https://github.com/user-attachments/assets/72ba9268-1719-4335-8532-be9c4cd9b23e" />

<img width="221" height="443" alt="image" src="https://github.com/user-attachments/assets/35c1afd5-ef02-404a-b2f5-829b4bec841d" />

<img width="522" height="448" alt="image" src="https://github.com/user-attachments/assets/73113449-a122-413a-81f9-1ed019b07dcf" />

<img width="189" height="185" alt="image" src="https://github.com/user-attachments/assets/0061f7e2-4604-4939-9e5d-6ccf67d14f4c" />





