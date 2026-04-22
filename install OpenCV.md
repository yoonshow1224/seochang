# 우분투 OpenCV 설치

  - **0. swap파일 삭제 및 설치**
    - 1. 기존 swap 끄기   
     ```sudo swapoff -a```
    - 2. 기존 swap 파일 삭제  
    ```sudo rm /swapfile```
    - 3. 새로 2GB swap 생성  
      ```
      sudo fallocate -l 2G /swapfile
      sudo chmod 600 /swapfile
      sudo mkswap /swapfile
      sudo swapon /swapfile
      ```
- **1. 필요한 패키지 설치**

```
sudo apt install build-essential cmake git pkg-config \
libjpeg-dev libpng-dev libtiff-dev \
libavcodec-dev libavformat-dev libswscale-dev \
libv4l-dev libxvidcore-dev libx264-dev \
python3-dev python3-numpy
```

- **2.OpenCV 다운로드**
```
cd ~
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git
```

- **3. 빌드**
```
cd ~/opencv
mkdir build
cd build

cmake -D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
-D BUILD_EXAMPLES=ON ..
```

- **4. 컴파일**
```
make -j$(nproc)
sudo make install
sudo ldconfig
```
