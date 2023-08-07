# Yolov5 학습 프로그램(python, ipynb)
## Google 드라이브를 통해 비디오 업로드후 학습시키는 코드 <br>

### 필요파일 설치
```
!git clone https://github.com/ultralytics/yolov5
%cd yolov5 	
%pip install -qr requirements.txt 
```

### Sample_Data 경로 설정, 필요 폴더 생성
```
import os
import os.path
import zipfile
Data_Path = "/content/yolov5/Sample_Data"
if os.path.isdir(Data_Path) == False:
  os.mkdir(Data_Path) 

zip_file = zipfile.ZipFile("/content/drive/MyDrive/wkit/wk1_data.zip")
zip_file.extractall(Data_Path)
```

### 학습 실행 (라벨링 yarm 파일 필요)
```
!python /content/yolov5/train.py --data "/content/yolov5/Sample_Data/data.yaml" --epochs 1000 #epoch 100회
```

### 학습된 데이터 검증
```
!python /content/yolov5/val.py --data "/content/yolov5/Sample_Data/data.yaml" --weights "/content/yolov5/runs/train/exp2/weights/best.pt"
```

### 예측 데이터 생성
```
!python /content/yolov5/detect.py --weights "/content/yolov5/runs/train/exp2/weights/best.pt" --source "/content/drive/MyDrive/wkit/output_Video/C045103_001.mp4"
```



### 영상에 적용 결과
### epoch 횟수 40
쓰러져 있는 사람이 한명이상일때 정상적으로 swoon 인식 하지만 서있는 사람도 swoon 으로 인식되는 문제 <br>
![epoch40_swoon](https://github.com/dfgh119/Yolov5/assets/102535345/84e970ac-0f4e-41b0-896e-5a0b9b713df5) <br>
![epoch40_swoon2](https://github.com/dfgh119/Yolov5/assets/102535345/40308e5b-b41a-4c08-9e67-a205cb8c5181) <br>
![epoch40_swoon3](https://github.com/dfgh119/Yolov5/assets/102535345/5b787813-dd17-4dde-9e1a-ee565041da98)

### epoch 횟수 1000
서있는 사람이 swooon 으로 인식되는 문제 해결, 하지만 서있을때 사람이 인식되지 않음<br>
![epoch1000_swoon](https://github.com/dfgh119/Yolov5/assets/102535345/ddeb5e60-dfee-4c76-bdb1-54c33b524337) <br>
![epoch1000_swoon2](https://github.com/dfgh119/Yolov5/assets/102535345/f0d1499f-754d-45c1-856a-c6ddf42abd9a) <br>
![epoch1000_swoon3](https://github.com/dfgh119/Yolov5/assets/102535345/20f3b047-a190-4995-acff-58119c58ddc2)


