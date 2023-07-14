# Breast-Ultrasound_CNN

유방암은 전 세계적으로 여성의 가장 흔한 사망 원인 중 하나입니다. 조기 발견은 조기 사망의 수를 줄이는 데 도움이 됩니다. 데이터는 초음파 스캔을 사용하여 유방암의 의료 이미지를 검토합니다.\
유방 초음파 데이터 세트는 정상, 양성 및 악성 이미지의 세 가지 클래스로 분류됩니다. 유방 초음파 영상은 기계 학습과 결합될 때 유방암의 분류, 감지 및 세분화에 훌륭한 결과를 생성할 수 있습니다.

데이터셋:

베이스라인에서 수집된 데이터에는 25세에서 75세 사이의 여성의 유방 초음파 이미지가 포함됩니다. 이 데이터는 2018년에 수집되었습니다.\
환자 수는 600명의 여성 환자입니다. 데이터 세트는 평균 이미지 크기가 500*500픽셀인 780개의 이미지로 구성됩니다. 이미지는 PNG 형식입니다.\
실측 이미지는 원본 이미지와 함께 제공됩니다. 이미지는 정상, 양성 및 악성의 세 가지 클래스로 분류됩니다.\
*개인적으로 일반인눈으로는 양성과 악성을 구분하기 힘들다고 생각합니다.
(-kaggle dataset-)

모델:

CNN 모델을 사용하였습니다.\
##CNN구조###############################################################################################\
model.add(Conv2D(input_shape=(IMG_WIDTH,IMG_HEIGHT,3), kernel_size=(3,3), filters=32, activation='relu'))\
model.add(Conv2D(kernel_size=(3,3), filters=64, activation='relu'))\
model.add(MaxPooling2D(pool_size=(2,2)))\
model.add(Dropout(0.25))\
model.add(Flatten())\
model.add(Dense(256, activation='relu'))\
model.add(Dropout(0.5))\
model.add(Dense(class_nums, activation='softmax'))\
############################################################################################################\
-전이학습을 이용하여 xception 모델을 사용하였습니다 (Xception(weights='imagenet')\
-(크기가 작은편에 속하여 Xception 모델을 선택)\
-Learning Rate = 2E-5 (fine-tuning)\
-다양성을 확보하기 위하여 데이터를 모두 섞어 주었습니다.\
-데이터 부족으로 인한 데이터증강을 사용하였습니다\
-callbacks 함수로는 checkpoint, earlystopping 을 사용하였습니다.\

결과:

정확도 0.96 이상.\
loss 2.5 (epoch=14)\




PPT:
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/dd2d9600-69e7-4b10-895d-e7f5bea86052)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/eb815dce-c5d0-42e0-8bdd-d8522036ecc9)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/112f45e1-7e73-40c8-8abe-d7cfecdd200e)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/0da9aae6-f699-4f93-8123-8a189e1f88e4)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/450f76c8-a454-4830-981e-461bc231cfde)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/99f2d677-f653-43dd-8789-0ccb5dc33419)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/4d338d0b-abf0-473a-9464-2abe8b131022)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/ca0f178d-b84f-41b3-97a6-0034a5691da6)
![image](https://github.com/limseo12/Breast-Ultrasound_CNN/assets/93918673/7adbb96d-3cf7-4354-a6ec-55d97123c4a7)

