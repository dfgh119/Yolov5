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





