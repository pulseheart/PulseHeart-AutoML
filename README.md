# PulseHeart-AutoML
video classification for reduced, mid-range and preserved ejection fraction by echocardiography


![graphical-abstract](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/66168713-1fb6-43e9-8796-755d62a89b9c)
## Instructions for interested researchers
### General Flow Chart
![Figure1](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/f8b47c24-d385-455a-ab9b-cf8ac43778b2)
(a) data curation; (b) upload the study managed dataset to Google Cloud Storage; (c) balanced data sets S, M and L, the size of which depends on the minority class (rEF, mEF and npEF respectively); (d): video classifications to test; (e): create a per-model annotation dataset and upload the corresponding CSV files (one for the train and one for the test videos); (f) specify the model to be trained; (g) run the model for training; (h) analyze the test set; (i) human panel reassessment of false positives and false negatives.
#### Getting access to the EcoNet dataset
Open the GitHub link https://echonet.github.io/dynamic/ and there open the link to access the dataset: https://stanfordaimi.azurewebsites.net/datasets/834e1cd1-92f7-4268-9daa-d359198b310af, log in or sign up if you don't have an acccount.
Download the 7.04 GB EchoNet-Dynamic.zip file.
Unzip the file 
Extract the 3064 AVI files of our study dataset using the notebook ...
### Watching individual videos
Refer to the newly created CSV file for searching the desired videos.
#### Three examples of correctly classified video of high quality:
![Figure2](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/90c1dce5-f40a-4d32-a7f1-1535c24b7cf0)
Frames from videos pertaining to the study dataset. End-diastolic frames are shown on the upper part of the slide and end-systolic frames below: (a) 0X2753C50A8B05D7D5.avi, label pEF, EF 58.3% by Simpson method; (b) 0X2F3141F00A232601.avi, label mEF, EF 42.1% by Simpson method; (c) 0X41563E2CC2230C0E.avi, label rEF, EF 21.9% by Simpson method.
#### Three examples of misclassified video of low quality:
![Figure12](https://github.com/pulseheart/PulseHeart-AutoML/assets/29145045/c6f885ca-76c8-4dd9-a148-dcb652f898e4)
Frames from misclassified videos. End-diastolic frames are shown on the upper part of the slide and end-systolic frames below: (a) 0X41ECEC7AAEEFD0E6.avi, label pEF, EF 57.3% by Simpson method, pEF by unanimous panel, misclassified as rEF; (b) 0X7923B6B4614AF456.avi, label mEF, EF 49.1% by Simpson method, mEF for four raters and rEF for one rater,  misclassified as rEF; (c) 0X3503A92D7637451.avi, label rEF, EF 31.8% by Simpson method, rEF by unanimous panel, misclassified as nrEF. 
### Using the original train/split of our nine experimentations:
Use the corresponding 
