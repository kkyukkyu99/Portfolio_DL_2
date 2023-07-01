# Portfolio_DL_2
DeepLearning Project Porfolio

***
<h2>#1. Project - Brain Tumor MRI Image Classification</h2> 

- Background
<p>The diagnosis of blood-based diseases often involves identifying and characterizing patient blood samples.
Automated methods to detect and classify blood cell subtypes have important medical applications.</p>
<p>혈액 기반 질병의 진단은 종종 환자의 혈액 샘플을 식별하고 특성화하는 것을 포함합니다. 혈액 세포의 유형을 감지하고 분류하는 것은 혈액 기반 질병 진단 과정 중  
혈액 세포 하위 유형을 감지하고 분류하는 자동화된 방법은 중요한 의학적 응용 분야를 가지고 있습니다.</p>

- Environment
<p>Google Colaboratory</p> 

- Summary

  <h3>First try</h3>

	1. Data Source
		- https://www.kaggle.com/datasets/paultimothymooney/blood-cells
	
	2. Data Preprocessing
		- ImageDataGenerator
      		- rescale: 1./255
      		- image size: (224, 224)
      		- color mode: rgb
        	- class mode: sparse
	
	3. Model & Algorithms
	  - Transfer Learning(TL)
        - MobileNet(CNN)
	  - Fine Tunning
        - Activate function: softmax
        - optimizer: Adam
        - learning_rate: 1e-5 
    - callbacks
        - EarlyStopping
            - val_loss
            - patience = 5
        - ModelCheckpoint
            - val_loss
            - save_best_only

	4. Report
    - loss: 0.0025, accuracy: 0.9994
		- val_loss: 1.0904, val_accuracy: 0.8528
		- Problems(문제): Overfitting and Low Accuracy(과대적합과 낮은 정확도)
		![First_Training_Result](https://github.com/kkyukkyu99/Portfolio_DL_2/blob/main/First_Training_Result.png)
	
	5. Solution
		- Solve overfitting problem by mixing and redistributing
		- 데이터를 섞은 후 재분배하여 과대적합 문제를 해결한다.

  <h3>Second try</h3>
  
  	6. Report
  	   	- loss: 0.0020, accuracy: 0.9995
  	   	- val_loss: 0.0131, val_accuracy: 0.9960
		![Second_Training_Result](https://github.com/kkyukkyu99/Portfolio_DL_2/blob/main/Second_Training_Result.png)

    7. Testing with Random Eosinophil image from Google
      ![Random Eosinophil image from Google](https://github.com/kkyukkyu99/Portfolio_DL_2/blob/main/Eosinophils_predict_image.jpg)
      - OpenCV
         - Convert Color: BGR to RGB
         - Resize: (224, 224)
         - Normalizaiton: /255
      - Predict result: EOSINOPHIL
       
