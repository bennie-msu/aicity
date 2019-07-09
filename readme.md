# AICity Project Track3

> Description: Through tracking cars, the algorithm can tell which is the anomaly. Anomalies usually refer to stalling cars or running-off-the-road cars. 

The repo includes:
* How to train the model of detecting cars
* Detect cars via videos
* Track cars
* Judge an anomaly

### Prerequisite 


#### install Mask RCNN

```shell
git clone https://github.com/matterport/Mask_RCNN.git
cd Mask_RCNN
pip3 install -r requirements.txt
python3 setup.py install
```

#### add the lost files

__The all required files are stored on the Google Drive__

1. Add videos to aic19-track3-train-data/ or aic19-track3-train-data/ from Lab Server;

2. Train your own car-detection model with images from Lab Server;

3. Add our model mask_rcnn_car_0030.h5 to model/; or train that from scratch.

4. ```
   git clone [Our Project]
   cd codes/car_detection/
   ```

### Train the custom model

```
# please ensure you are under the car_detection directory
python3 Mask_RCNN/car_detection_train.py train --dataset=dataset/ --weights=model/mask_rcnn_car_0030.h5 --logs=model/

# train from a pre-trained model COCO
# python3 Mask_RCNN/car_detection_train.py train --dataset=dataset/ --weights=model/mask_rcnn_coco.h5 --logs=model/
python3 infer_car_in_video.py
python3 sort_track.py
# output results into output_train/ or output_test/ in terms of your setup
# make sure there is at least one sequence file under the output_train/
python3 anomalies_detection.py
```


### Train your own model

```shell
# please ensure you are under the car_detection directory
python3 Mask_RCNN/car_detection_train.py train --dataset=dataset/ --weights=model/mask_rcnn_car_0030.h5 --logs=model/

# train from a pre-trained model COCO
# python3 Mask_RCNN/car_detection_train.py train --dataset=dataset/ --weights=model/mask_rcnn_coco.h5 --logs=model/
```

### Detect cars in the video (it has been integrated to tracking part)

```shell
python3 infer_car_in_video.py
```

### Track cars in the video

```shell
python3 sort_track.py
# output results into output_train/ or output_test/ in terms of your setup
# we uploaded the results to Google Drive so you use it directly.
```

### Find anomalies

```shell
# make sure there is at least one sequence file under the output_train/
python3 anomalies_detection.py
# the output will be under the output_anomalies folder.
```

The files you maybe need is on the Drive https://drive.google.com/drive/folders/1Eee7fgz57J7I4uVtdskzEfGFLv_vkppp?usp=sharing


