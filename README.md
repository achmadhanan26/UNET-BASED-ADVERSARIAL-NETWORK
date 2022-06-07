# Tensorflow-based Deep Learning Implementations for COVID-19 Lung X-Ray Image Analysis + Tkinter GUI Interface

COVID-19 is a virus that causes outbreaks around the world today. The virus attacks the human respiratory tract and is highly contagious. Radiographic  examinations such as X-Ray and computed tomography (CT) have been used to  identify morphological patterns of COVID-19 related lung lesions. Lungs X-Ray images of COVID-19 hold information related to the clinical condition of patient, where there are pathology objects that can be detected in COVID-19 patients. Detection of pathological objects is done manually by radiologists so that their application relies on radiologist observation and is limited to radiological availability. Therefore, a study is currently needed on the automatic lung X-Ray segmentation method based on deep learning by using the Convolutional Neural Network to segment the object of ground glass opacity pathology. The dataset used is an open-source COVID-19 lung X-Ray Dataset available on Github. The processing stage of COVID-19 lung X-Ray imagery begins with a pre-processing stage to normalize pixels, then generalize grey-level imagery, and resizing the size of the image dataset. The next stage is segmentation of ground glass opacity using CNN's adversarial network architecture. The results of this ground glass opacity segmentation model have a Dice Coefficient (DSC) performance of up to 88.6% and a model testing performance with DSC results of 50.1%, recall 0.474, precision 0.532, true positive 0.474, true negative 0.846.

## Table of Contents
* Motivation
* Dataset
* Image Pre-processing
* Generative Adversarial Network
* Result
* Refferences
* Contact Us


## Motivation
Lungs X-Ray images of COVID-19 hold informations that related to the clinical condition of patient, where there are pathology objects that can be detected in COVID-19 patients. Detection of pathological objects is done manually by radiologists so that their application relies on radiologist observation and is limited to radiological availability. Therefore, a study is currently needed on the automatic lung X-Ray segmentation method based on deep learning by using the Convolutional Neural Network to segment the object of ground glass opacity pathology. 

Another motivation in conducting this research is to achieve my bachelor degree in Biomedical Engineering at Sepuluh Nopember Institut of Technology, Surabaya, Indonesia. 

## Dataset 
The X-ray COVID-19 images dataset used in this research origins from Github manage by [Joseph Paul Cohen](https://github.com/ieee8023) which intended for research purposes and obtained by using python programming library from [torchxrayvision](https://github.com/mlmed/torchxrayvision).

#### X-Ray COVID-19 Dataset
 ![dataset_raw1](https://user-images.githubusercontent.com/72918677/172343825-635f6ccf-61be-4cc1-a916-052dfaa064aa.PNG)
 ![dataset_raw2](https://user-images.githubusercontent.com/72918677/172343804-e669b6cc-7e98-450c-8c20-91d5ec7e3554.PNG)
* [Raw X-Ray Lung COVID-19 Open-source Dataset](https://github.com/ieee8023/covid-chestxray-dataset)

#### Ground Truth Segmentation
 ![rawdatasettarget1](https://user-images.githubusercontent.com/72918677/172342834-4567e6a4-e0fc-4eb0-83f0-be39b64589ac.PNG)
 ![rawdatasettarget2](https://user-images.githubusercontent.com/72918677/172342939-720a1ffa-42c7-4720-a506-032fa3f58430.PNG)
* [Ground Glass Opacities Annotation](https://github.com/GeneralBlockchain/covid-19-chest-xray-segmentations-dataset#download-the-dataset)

## Image Pre-Processing
This step is really needed before doing any machine learning processing! the reason is becaused the dataset used is open-source and could be unstandard, therefore it could causes some main problems such as:
* Abnormalities in X-Ray COVID-19 images shown by extreme value of image histogram
 ![tes5 drawio](https://user-images.githubusercontent.com/72918677/172331381-8dbea8ca-3296-42b3-972b-a2571e5890e7.png)

* The annotation segmentation by https://github.com/GeneralBlockchain/covid-19-chest-xray-segmentations-dataset only covers the ground glass opacity object for each images. it cant be use for ground truth segmentation yet.
![tes4 drawio](https://user-images.githubusercontent.com/72918677/172342753-5e26bb24-e987-4592-9159-69448c9337fd.png)

* Different images size and resolution needs to be resizes before the learning.
![prepross](https://user-images.githubusercontent.com/72918677/172329946-cf2c4a66-10d7-4881-9f91-99b5cefd5056.png)

* The amount of image data presented is very small. Therefore, it needs to implement data augmentation algorithm to avoid failure in learning.

## Generative Adversarial Network
GAN network consists of 2 deep learning network that works in opposite way to another, such as: the first network is trained to create or generate the segmentation based on the given ground truth, therefore it is called the "Generator Network". Meanwhile the second network is, called "Discriminator Network", trained to differentiate the output segmentation from the "Generator Network" from the actual ground truth image, it is done by setting up the new learning function with goals to find the differentiations for each pixel. 
* Here is the Generator Network i use :
![arsitektur UNET](https://user-images.githubusercontent.com/72918677/172331559-0c140da1-5c21-4669-9162-869f61b73023.png)

* It consists of a couple of convolutional blocks:
![blok konvolusi](https://user-images.githubusercontent.com/72918677/172331579-6d0e980c-099e-4290-af75-bafc6b8163de.png)

I modified the original code from the tensorflow tutorial from [here](https://www.tensorflow.org/tutorials/generative/pix2pix). 
* And here is how the  Discriminator Network i use for this research: 
![kritik network](https://user-images.githubusercontent.com/72918677/172331628-bf6df294-df14-4e6f-9801-1b9e0aecd36e.png)

* It consists of a couple of residual blocks:
![blok residual](https://user-images.githubusercontent.com/72918677/172331616-b038455f-0b12-4b23-ad35-4bcfb713866e.png)

## Result
The overall learning result is good enough but takes so much time to do a single epoch, so far i managed to learn by using 50 epoch with core i-7 processor PC. For this research, i divided the whole pre-processed data into 90% for training purpose and 10% for testing purpose. Notice that i didnt use any validation algorithm because it would took longer time to complete. 
* And here is how the sceme goes on:
![arsitektur UNET-Page-7 drawio](https://user-images.githubusercontent.com/72918677/172334625-1c27fdaa-45be-46cb-a6eb-802128331cd1.png)

* For the GUI interface, im using Tkinter GUI which looks like this:
![gui note 1](https://user-images.githubusercontent.com/72918677/172374015-44ab6d3c-51e7-49e4-9b9a-3d7a3980fc4a.JPG)

For the hyperparameter tuning, i did some experiment which one goes for the best result. Here is the photo i took while trying to tune the hyperparameter with these set ups:
* Batch size : 17
* Epoch      : 51
* Learning rate : 0.0001
* Lambda     : 5

* Here is the result based on the Dice Coefficient and the corresponding image segmentation:
![Capture](https://user-images.githubusercontent.com/72918677/172372767-44ae94f6-7ffd-4b50-8948-76ad76580dc0.JPG)

* And here is the result graphically:
![Capture2](https://user-images.githubusercontent.com/72918677/172372781-b1e14062-c7c0-4c06-8325-93415eb08946.JPG)

## Refferences
* Josep Paul Cohen paper : https://arxiv.org/abs/2003.11597
* BlockChain Github : https://github.com/GeneralBlockchain/covid-19-chest-xray-segmentations-dataset#download-the-dataset
* pix2pix GAN paper : https://arxiv.org/abs/1611.07004
* U-net paper : https://arxiv.org/abs/1505.04597
* I modified the code from tensorflow tutorial : https://www.tensorflow.org/tutorials/generative/pix2pix

## Contact us
* Email: achmad.hanan26@gmail.com
