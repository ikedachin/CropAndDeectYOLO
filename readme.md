# CropAndDetectYOLO

## 説明
大きなサイズの画像を所定のサイズでクロップした学習データを作ります。
labelmeのアノテーションデータを使い、YOLO形式のファイルを作ります。

### 例： 以下の設定で画像を切り取ります。
|設定値|ピクセル数|
|----|----|
|元画像サイズ|6000*4000pix|
|クロップサイズ|640*640pix|
|オーバラップ|64pix|

### 元画像のピクセル位置をクロップ位置
これに合わせて、labelmeのアノテーション情報をYOLO形式に変換します。
x2のxは「576~1216」をクロップしていますが、  
640　−　64　= 576
576　+　640　=　1216  
の部分を切り取ります。

|----|x1|x2|x3|x4|---|
|----|----|----|----|----|---|
|y1|x: 0 ~ 640 </br>y: 0 ~ 640|x: 576 ~ 1216</br>y: 0 ~ 640|x: 1152 ~ 1792</br>y: 0 ~ 640|x: 1728 ~ 2368</br>y: 0 ~ 640|x: ...</br>y: ...|
|y2|x: 0 ~ 640 </br>y: 576 ~ 1216|x: 576 ~ 1216</br>y: 576 ~ 1216|x: 1152 ~ 1792</br>y: 576 ~ 1216|x: 1728 ~ 2368</br>y: 576 ~ 1216|x: ...</br>y: ...|
|y3|x: 0 ~ 640 </br>y: 1152 ~ 1792|x: 576 ~ 1216</br>y: 1152 ~ 1792|x: 1152 ~ 1792</br>y: 1152 ~ 1792|x: 1728 ~ 2368</br>y: 1152 ~ 1792|x: ...</br>y: ...|
|y4|x: 0 ~ 640 </br>y: 0 ~ 640|x: 576 ~ 1216</br>y: 0 ~ 640|x: 1152 ~ 1792</br>y: 0 ~ 640|x: 1728 ~ 2368</br>y: 0 ~ 640|x: ...</br>y: ...|
|y.|x: ... </br>y:...|x: ...</br>y: ...|x: ...</br>y: ...|x: ...</br>y: ...|---|


### ライブラリのバージョン（参考:私が実行したときのバージョン）
python:3.10.8  
numpy:1.25.1  
pandas:2.0.1  
pillow:10.010  
matplotlib:317.2  
opencv-python:418.0.741  

### ファイル構成

CropAndDetectYOLO/  
　├ croped_data/  
　|　  ├ check_croping  
　|　  └ imagss     # folder to save croped images  
　|　  └ labels     # folder to save YOLO text files for croped images  
　|　  
　├ data/   
　|　  ├ *.jpg      # big size image  
　|　  └ *.json     # json file create from labelme  
　|　  ├ *.jpg      # big size image  
　|　  └ *.json     # json file create from labelme  
　|　  ├ *.jpg      # big size image  
　|　  └ *.json     # json file create from labelme  
　|　  
　├ readme.md  
　├ crop_and_detect_YOLO.ipynb

