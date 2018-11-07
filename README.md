[![Build Status](https://travis-ci.org/penny4860/tf-eager-yolo3.svg?branch=master)](https://travis-ci.org/penny4860/tf-eager-yolo3) [![codecov](https://codecov.io/gh/penny4860/tf-eager-yolo3/branch/master/graph/badge.svg)](https://codecov.io/gh/penny4860/tf-eager-yolo3)

# Tensorflow eager implementation of Yolo-v3

I have implemented yolo-v3 detector using tensorflow eager execution.

<img src="imgs/sample_detected.png" height="600">

## Usage for python code

#### 0. Requirement

* python 3.6
* anaconda 5.1.0
* tensorflow 1.9.0
* opencv 3.4.3.18
* imgaug 0.2.6
* tqdm
* Etc.


I recommend that you create and use an anaconda env that is independent of your project. You can create anaconda env for this project by following these simple steps. This process has been verified on Windows 10 and ubuntu 16.04.

```
$ conda create -n yolo3 python=3.6 anaconda=5.1.0
$ activate yolo3 # in linux "source activate yolo3"
(yolo) $ pip install tensorflow==1.9.0
(yolo) $ pip install opencv-python==3.4.3.18
(yolo) $ pip install imgaug==0.2.6
(yolo) $ pip install tqdm
(yolo) $ pip install pytest-cov
(yolo) $ pip install codecov
(yolo) $ pip install -e .
```

### 1. Object detection using original yolo3-weights


* Run object detection through the following command.
	* ```project/root> python pred.py -c configs/predict_coco.json -i tests/samples/sample.jpeg```
	* Running this script will download the [original yolo3-weights file](https://pjreddie.com/media/files/yolov3.weights) and display the object detection results for the input image.
	
* You can see the following results:
	* <img src="imgs/dog_detected.jpeg" height="600"> 

### 2. Training from scratch

This project provides a way to train a detector from scratch. If you follow the command below, you can build a digit detector with just two images. If you follow the instructions, you can train the digit detector as shown below.

* ```project/root> python train_eager.py -c configs/svhn.json```
	* <img src="imgs/svhn.jpg" height="250">

After training, you can evaluate the performance of the detector with the following command. 

* ```project/root> python eval.py -c configs/svhn.json```
	* Running this script will evaluate the annotation dataset specified in ```train_annot_folder```. The evaluation results are output in the following manner.
	* ```{'fscore': 1.0, 'precision': 1.0, 'recall': 1.0}```

Now you can add more images to train a digit detector with good generalization performance.

## Other Results

### 1. Raccoon dataset : https://github.com/experiencor/raccoon_dataset

<img src="imgs/raccoon.jpg" height="300">

* Pretrained weight file is stored at [raccoon](https://drive.google.com/drive/folders/1qCi8ZUkUSWNmd-sSjvu0cK5cIG8-Ogoz)
* Evaluation (200-images)
	* fscore / precision / recall: 0.97, 0.96, 0.98


### 2. SVHN dataset : http://ufldl.stanford.edu/housenumbers/

* Image files : http://ufldl.stanford.edu/housenumbers/
* Annotation files : https://github.com/penny4860/svhn-voc-annotation-format
	* In this project, I use pascal voc format as annotation information to train object detector. An annotation file of this format can be downloaded from [svhn-voc-annotation-format](https://github.com/penny4860/svhn-voc-annotation-format).

<img src="imgs/svhn_1.jpg" height="400">

* Pretrained weight file is stored at [svhn](https://drive.google.com/drive/folders/1c3ikKWNgaMtPHUWQf54taRUgyJhcyX1g)
* Evaluation (1000-images)
	* fscore / precision / recall: 0.93, 0.89, 0.97


### 3. Udacity self-driving-car dataset : https://github.com/udacity/self-driving-car/tree/master/annotations

<img src="imgs/udacity.jpg" height="500">

* Pretrained weight file is stored at [udacity](https://drive.google.com/drive/folders/1aaFmnxWM4UJX5paiKmSaylOBXsuMNqBL)
* Evaluation (9217-images)
	* fscore / precision / recall: 0.72, 0.61, 0.87


### 4. Kitti object detection dataset : http://www.cvlibs.net/datasets/kitti/eval_object.php

<img src="imgs/kitti.jpg" height="400">

* Pretrained weight file is stored at [kitti](https://drive.google.com/drive/folders/1G4uFyk60c0hlH_4PRPRVSFpUnS582Fde)
* Evaluation (7481-images)
	* fscore / precision / recall: 0.93, 0.93, 0.94


## Copyright

* See [LICENSE](LICENSE) for details.

