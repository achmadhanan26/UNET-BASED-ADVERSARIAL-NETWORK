# Tensorflow-based Deep Learning Implementations for COVID-19 Lung X-Ray Image Analysis

COVID-19 is a virus that causes outbreaks around the world today. The virus attacks the human respiratory tract and is highly contagious. Radiographic  examinations such as X-Ray and computed tomography (CT) have been used to  identify morphological patterns of COVID-19 related lung lesions. Lungs X-Ray images of COVID-19 hold information related to the clinical condition of patient, where there are pathology objects that can be detected in COVID-19 patients. Detection of pathological objects is done manually by radiologists so that their application relies on radiologist observation and is limited to radiological availability. Therefore, a study is currently needed on the automatic lung X-Ray segmentation method based on deep learning by using the Convolutional Neural Network to segment the object of ground glass opacity pathology. The dataset used is an open-source COVID-19 lung X-Ray Dataset available on Github. The processing stage of COVID-19 lung X-Ray imagery begins with a pre-processing stage to normalize pixels, then generalize grey-level imagery, and resizing the size of the image dataset. The next stage is segmentation of ground glass opacity using CNN's adversarial network architecture. The results of this ground glass opacity segmentation model have a Dice Coefficient (DSC) performance of up to 88.6% and a model testing performance with DSC results of 50.1%, recall 0.474, precision 0.532, true positive 0.474, true negative 0.846.

## Table of Contents
* Motivation
* Dataset
* Image Pre-processing
* Generative Adversarial Network
* Refferences
* Contact Us


## Motivation
Lungs X-Ray images of COVID-19 hold informations that related to the clinical condition of patient, where there are pathology objects that can be detected in COVID-19 patients. Detection of pathological objects is done manually by radiologists so that their application relies on radiologist observation and is limited to radiological availability. Therefore, a study is currently needed on the automatic lung X-Ray segmentation method based on deep learning by using the Convolutional Neural Network to segment the object of ground glass opacity pathology. 

Another motivation in conducting this research is to achieve my bachelor degree in Biomedical Engineering at Sepuluh Nopember Institut of Technology, Surabaya 

## Dataset 
The X-ray COVID-19 images dataset used in this research acquired from an open-source Github manage by https://github.com/ieee8023 using python programming library from https://github.com/mlmed/torchxrayvision.

#### X-Ray COVID-19 Dataset
![alt text](https://raw.githubusercontent.com/ieee8023/covid-chestxray-dataset/master/images/000001-1.jpg)
* [Raw X-Ray Lung COVID-19 Open-source Dataset](https://github.com/ieee8023/covid-chestxray-dataset)

#### Ground Truth Segmentation
![alt text](https://user-images.githubusercontent.com/66736646/89189135-60f08000-d5c1-11ea-87cc-bb10b8bb635a.gif)
* [Ground Glass Opacities Annotation](https://github.com/GeneralBlockchain/covid-19-chest-xray-segmentations-dataset#download-the-dataset)

## Image Pre-Processing
![prepross](https://user-images.githubusercontent.com/72918677/172329946-cf2c4a66-10d7-4881-9f91-99b5cefd5056.png)

## Generative Adversarial Network

## Refferences

## Contact us
* Email: achmad.hanan26@gmail.com



