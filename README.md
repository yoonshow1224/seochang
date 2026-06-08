# 휠체어 사용자를 위한 AI 기반 회전문 감속 및 안전 장치 시스템

### 목적
자동 회전문이 회전할 때 휠체어가 이동하기에 위험할 수 있기 때문에 AI기반 자동 감속 시스템을 제시했다.

### 사용 기술 및 개발 도구
* yolov8
* Ubuntu
* 웹캠
* 회전문

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
  yolo detect predict \
  model=runs/detect/train/weights/best.pt \
  source=valid/images
```
