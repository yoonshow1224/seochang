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
(나중에 방법 입력 (김도영))

**가상환경 세팅**
```
# 가상환경 생성
python3 -m venv venv

# 가상환경 활성화
source venv/bin/activate

# YOLOv8 설치
pip install ultralytics

# 학습 실행
yolo detect train model=yolov8n.pt data=data.yaml epochs=100 imgsz=640
```
**라이브러리 설치**

` pip install roboflow ultralytics `
