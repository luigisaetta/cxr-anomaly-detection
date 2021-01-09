## CXR Anomaly Detection
In this project I have developed a model, based on a DNN, to analyze a **Chest X-Ray** and predict if it contains signs of disease or not.

In the project I have used PNG images 1024x1024 coming from **NIH Chest X-Ray-14** dataset

### Dataset
The dataset used is saved in Kaggle: 
https://www.kaggle.com/luigisaetta/cxr-tfrec256-may2020

### Differences with the project contained in the repository cxr-pneumonia
The goal for the model is different. In the Pneumonia project the goal is to identify if a CXR contains signs of Pneumonia.
In this project the goal is to identify if the CXR contains any sign of disease. In other words here a negative is a CXR with No Findings and a positive is a CXR with any sign of disease.

The inspiration for this work has been taken from the article: 

https://www.nature.com/articles/s41746-020-0273-z

The list of images (from NIH-CXR 14 dataset) used for train-validation and test has been taken from the github:

https://github.com/rsummers11/CADLab/tree/master/CXR-Binary-Classifier

### Features:
* Train and Test datasets have been prepared compressing original images (PNG 1024x1024) in JPEG 512x512 and packing all in **TensorFlow TFRecord** files
* Train set is balanced (50% pneumonia), test set has a 25% of pneumonia
* TFRecord files published in **Kaggle Dataset**: https://www.kaggle.com/luigisaetta/nih-cxr-pneu512
* Training on **TPU** (Kaggle)
* Using Google **EfficientNet B2**
* For training, it is adopted **K-fold Cross Validation** (K=5)
* **Learning Rate Scheduler** to control variation of Learning Rate during epochs
* **Ensemble** of K=5 models: predictions are average from prediction from each single model
* Code for controls and inference on **DICOM** files
* Plot of **Images Intensity Profiles** for different diseases
* Compute best threshold, based on **F1-score**
* Model interpretation with **GRAD-Cam**

### Citations:
@article{tang2020automated,
    title={Automated abnormality classification of chest radiographs using deep convolutional neural networks},
    author={Tang, Yu-Xing and Tang, You-Bao and Peng, Yifan and Yan, Ke and Bagheri, Mohammadhadi and Redd, Bernadette A and Brandon, Catherine J and Lu, Zhiyong and Han, Mei and Xiao, Jing and Summers, Ronald M},
    journal= {npj Digital Medicine},
    volume={3},
    number={1},
    pages={1--8},
    year={2020},
    publisher={Nature Publishing Group}
}

@inproceedings{wang2017chestx,
    title={Chestx-ray8: Hospital-scale chest x-ray database and benchmarks on weakly-supervised classification and localization of common thorax diseases},
    author={Wang, Xiaosong and Peng, Yifan and Lu, Le and Lu, Zhiyong and Bagheri, Mohammadhadi and Summers, Ronald M},
    booktitle = {Proceedings of the IEEE conference on computer vision and pattern recognition},
    pages={2097--2106},
    year={2017}
}

