
3/21/22:
pyenv shell 2.7.17
   pip install ...
	pip install tensorflow==1.13.1
	pip install keras==2.0.8 opencv-python==4.2.0.32 imageio==2.6.1
	pip install imgaug tqdm
	
export LD_...=/usr/local/cuda/lib64:$LD...

https://github.com/rodrigo2019/keras_yolo2/releases/tag/pre-trained-weights
	full_yolo_backend.h5
https://drive.google.com/drive/folders/10oym4eL2RxJa0gro26vzXK__TtYOP5Ng
	full_yolo_raccoon.h5

python predict.py -c config.json -w ./full_yolo_raccoon.h5 -i images/cat.jpg
Could not create cudnn handle: CUDNN_STATUS_INTERNAL_ERROR

seems to be GPU memory not enough:
watch -n 0.1 nvidia-smi
8GB all used up @newpcamd

hptitan works.
____________________________________________________________________________________________________
Layer (type)                     Output Shape          Param #     Connected to                     
====================================================================================================
input_1 (InputLayer)             (None, 416, 416, 3)   0                                            
____________________________________________________________________________________________________
model_1 (Model)                  (None, 13, 13, 1024)  50547936    input_1[0][0]                    
____________________________________________________________________________________________________
DetectionLayer (Conv2D)          (None, 13, 13, 30)    30750       model_1[1][0]                    
____________________________________________________________________________________________________
reshape_1 (Reshape)              (None, 13, 13, 5, 6)  0           DetectionLayer[0][0]             
____________________________________________________________________________________________________
input_2 (InputLayer)             (None, 1, 1, 1, 10, 4 0                                            
____________________________________________________________________________________________________
lambda_2 (Lambda)                (None, 13, 13, 5, 6)  0           reshape_1[0][0]                  
                                                                   input_2[0][0]                    
====================================================================================================
Total params: 50,578,686
Trainable params: 50,558,014
Non-trainable params: 20,672

