# Bayesian Cellular Segmentation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/Cell_Segmentation_Bayesian.ipynb)


Segmentation of cells using bayesian neural networks for a certainty metric

In recent years, the segmentation of biomedical images has improved considerably, thanks in particular to deep learning, the availability of frameworks for testing and refining models, and the creation of massive data sets. The most renowned deep learning architecture for biomedical segmentation is Unet, which is becoming a gold standard throughout the computer vision community. However, classical deep learning approaches, whether on a multiclass or binary classification problem, only give a categorical prediction for each pixel without giving additional information on the degree of certainty of these predictions. Bayesian neural networks fill these gaps by providing a measure of uncertainty for each prediction, thus giving additional statistical and visual information to the clinician to make a more informed, rigorous and conservative diagnosis.

This work is on the training and usage of a U-Net based bayesian architecture to segment cells in different backgrounds, with an additional metric of the certainty of the model of each of its predictions, which would help experts know when to rely on the model, and when human intervention is necessary.

### Dataset

We created a custom data set based on the training set of images and labels provided by Kaggle for the 2018 Data Science Bowl. This dataset is composed of images of nuclei (cell nuclei).  The challenge aims to develop an algorithm capable of easily detecting and segmenting cell nuclei in order to count them, identify cancer cells from healthy cells, identify and track their movements in order to observe a patient's response to treatment at the molecular level. The kaggle dataset is therefore composed of cell nuclei acquired by different instruments and under different illumination, magnification and other modalities (fluorescence) The image data are in RGB format while the labels are RGB but with binary behaviour (0, 255).

Examples of images in data :

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/raw_data_images.png" alt="Dataset images" width="600"/>

### Architecture

### Results
