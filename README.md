# PulseHeart-AutoML

## Article

![image](https://github.com/pulseheart/PulseHeart-PyTorch/assets/29145045/781bfb36-e2f5-46c6-9ded-9b776e0ca508)

https://www.mdpi.com/2075-4418/14/13/1439

![graphical-abstract](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/66168713-1fb6-43e9-8796-755d62a89b9c)
## Instructions for interested researchers
### General Flow Chart
![Figure1](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/f8b47c24-d385-455a-ab9b-cf8ac43778b2)
(a) data curation; (b) upload the study managed dataset to Google Cloud Storage; (c) balanced data sets S, M and L, the size of which depends on the minority class (rEF, mEF and npEF respectively); (d): video classifications to test; (e): create a per-model annotation dataset and upload the corresponding CSV files (one for the train and one for the test videos); (f) specify the model to be trained; (g) run the model for training; (h) analyze the test set; (i) human panel reassessment of false positives and false negatives.
### Get access to the EchoNet dataset
- Make a fork of the GitHub directory
- Download locally the forked directory
- Open the GitHub link [echonet-dynamic](https://echonet.github.io/dynamic/) and there open the link to access the dataset at [Standford AIMI](https://stanfordaimi.azurewebsites.net/datasets/834e1cd1-92f7-4268-9daa-d359198b310af) (log in or sign up if you don't have an acccount).
- Download the 7.04 GB EchoNet-Dynamic.zip file.
- Unzip the file in your local directory
- Create a folder "curated" 
- Extract the 3064 AVI files of our study dataset in "curated" using the notebook [transfer-from-source.ipynb](https://github.com/pulseheart/PulseHeart-AutoML/blob/main/transfer-from-source.ipynb)
### Watch individual videos
The [all-data cvs file](https://github.com/pulseheart/PulseHeart-AutoML/blob/main/all-data.csv) describes the 3064 videos used  in this study.
#### Three examples of correctly classified video of high quality:
![Figure2](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/90c1dce5-f40a-4d32-a7f1-1535c24b7cf0)
Frames from videos pertaining to the study dataset. End-diastolic frames are shown on the upper part of the slide and end-systolic frames below: (a) 0X2753C50A8B05D7D5.avi, label pEF, EF 58.3% by Simpson method; (b) 0X2F3141F00A232601.avi, label mEF, EF 42.1% by Simpson method; (c) 0X41563E2CC2230C0E.avi, label rEF, EF 21.9% by Simpson method.
#### Three examples of misclassified video of low quality
![Figure12](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/c6f885ca-76c8-4dd9-a148-dcb652f898e4)
Frames from misclassified videos. End-diastolic frames are shown on the upper part of the slide and end-systolic frames below: (a) 0X41ECEC7AAEEFD0E6.avi, label pEF, EF 57.3% by Simpson method, pEF by unanimous panel, misclassified as rEF; (b) 0X7923B6B4614AF456.avi, label mEF, EF 49.1% by Simpson method, mEF for four raters and rEF for one rater,  misclassified as rEF; (c) 0X3503A92D7637451.avi, label rEF, EF 31.8% by Simpson method, rEF by unanimous panel, misclassified as nrEF. 
### Use the original train/split of our nine experimentations
Use the corresponding annotation dataset CSV files.

These files include our bucket name in the video file paths to be changed to your's, (for instance by a Replace_All operation in Excel or a modification using Python code).

### Launch experimentations, either replicating those of this research or training your own

Create a storage bucket and upload there the "curated" folder of study video files 

Refer to the following section of this [tutorial](https://cloud.google.com/vertex-ai/docs/tutorials/video-classification-automl).

#### Setting up your project
Chose an appropriate name, like "echocg-video-classification"

#### Creating a video classification dataset and importing videos

At the step 2a: choose the name your Dataset in relation with the train and test annotation datasets that you will use: for example L-3-classes 

At step 3: 
- Select "Upload import files from your computer"
- Choose Data split "Manual"
- Upload the training csv file (example: training_L_3_classes) specifying "training"
- Clicking ADD ANOTHER FILE
- Upload the testing csv file (example: test_L_3_classes) specifying "testing"
- Indicate your video file path, for instance: gs://*bucket name*/curated
- Click Continue
  
#### Training a video classification model
- Review the experiment videos
- Click TRAIN NEW MODEL
- Choose a training method (AutoML in this example)
- Click "Define your model"
- Make sure that data split is manual 75/25
- Edit Model Name if necessary (for example: ternary_classification_large_set)
- Click "START TRAINING"
