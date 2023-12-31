# Object Detection for Football Matches

## Overview
This project is aimed at developing an object detection system to identify and classify various objects in football matches, including players, goalkeepers, balls, and referees. The system will provide bounding boxes around each detected object and assign them the appropriate class name.

## Packages Used
To run this project, you will need the following Python packages:

- `super-gradients==3.2.0`: This package is used to load the YOLO NAS model, which is the backbone for our object detection system.
- `supervision`: This package is used for annotating the images with bounding boxes and class names.
- `onemetric`: This package is used to generate a confusion matrix for evaluating the performance of the object detection model.

You can install these packages using `pip`:

```bash
pip install supervision
pip install onemetric
pip install pytube --upgrade
```
## Dataset
Used a publicly available dataset from Kaggle for training and testing the object detection model. You can download the dataset from the following Kaggle link:

[Download the dataset from Kaggle](https://www.kaggle.com/datasets/nourhannabil/football-dataset-for-object-detection)


## Dataset Split
The original dataset was split into three subsets: training , validation, and testing with total images and labels 12k:

- Training Dataset: 80% of the original dataset.
- Validation Dataset: 10% of the original dataset.
- Test Dataset: 10% of the original dataset.

## Initial Training
initially trained the YOLO NAS model on the training dataset for 10 epochs. However, the results were not promising.


The labels for the objects in the dataset were provided in YOLO format. Here are the original labels:

 **Original Labels**
- Player team left
- Player team right
- Goalkeeper team left
- Goalkeeper team right
- Ball
- Main referee
- Side referee
- Staff members

**Initial Training**
![tested image](/assets/original_dataset.jpg)
![Confusion Matrix](/assets/confusion_matrix_original_dataset.png)

## Labeling Update
To improve the results, the class labels were updated to represent all objects as a single team, treating them as players. We then retrained the model on this modified dataset using YOLO NAS for 10 epochs.

**Updated Labels**
- Player
- Goalkeeper
- Ball
- Main referee
- Side referee
- Staff members

**Updated Training**

![tested image](/assets/updated_dataset.jpg)
![Confusion Matrix](/assets/confusion_matrix_updated_dataset.png)



## Video Inference using YOLO-NAS
YOLO-NAS supports video inference by providing the input video path and output video path with the following line of code:

```python
# Define the paths
INPUT_VIDEO_PATH = 'input_video.mp4'
OUTPUT_VIDEO_PATH = 'output_video.mp4'

# Perform inference on the input video
model.predict(INPUT_VIDEO_PATH).save(OUTPUT_VIDEO_PATH)
```
Tested the object detection system on a football match video, which is available on Google Drive. You can access the tested video using the following link:

[Tested Football Match Videos on Google Drive](https://drive.google.com/drive/folders/1NoufWl60SA1E8TmVQDTSqlcKrJTYT95L?usp=drive_link)





