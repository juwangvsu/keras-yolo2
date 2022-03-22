
3/21/22:
pyenv shell 2.7.17
pip install ...
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
