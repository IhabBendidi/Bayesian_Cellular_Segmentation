# Bayesian Cellular Segmentation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/Cell_Segmentation_Bayesian.ipynb)


Segmentation of cells using bayesian neural networks for a certainty metric

In recent years, the segmentation of biomedical images has improved considerably, thanks in particular to deep learning, the availability of frameworks for testing and refining models, and the creation of massive data sets. The most renowned deep learning architecture for biomedical segmentation is Unet, which is becoming a gold standard throughout the computer vision community. However, classical deep learning approaches, whether on a multiclass or binary classification problem, only give a categorical prediction for each pixel without giving additional information on the degree of certainty of these predictions. Bayesian neural networks fill these gaps by providing a measure of uncertainty for each prediction, thus giving additional statistical and visual information to the clinician to make a more informed, rigorous and conservative diagnosis.

This work is on the training and usage of a U-Net based bayesian architecture to segment cells in different backgrounds, with an additional metric of the certainty of the model of each of its predictions, which would help experts know when to rely on the model, and when human intervention is necessary.

### Dataset

We created a custom data set based on the training set of images and labels provided by Kaggle for the 2018 Data Science Bowl. This dataset is composed of images of nuclei (cell nuclei).  The challenge aims to develop an algorithm capable of easily detecting and segmenting cell nuclei in order to count them, identify cancer cells from healthy cells, identify and track their movements in order to observe a patient's response to treatment at the molecular level. The kaggle dataset is therefore composed of cell nuclei acquired by different instruments and under different illumination, magnification and other modalities (fluorescence) The image data are in RGB format while the labels are RGB but with binary behaviour (0, 255).

Examples of images in data :

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/raw_data_images.png" alt="Dataset images" width="600"/>

### Results

We were also able to track the predictions of our Bayesian model over iterations, as shown in the following figure. During the very first iteration, no concrete results can be predicted. But it is remarkable that after 300 iterations, general results show that the model starts to find the cells and to detect them, to finally find them with very minimal errors as early as the 1200th iteration.

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/bayesian_training_progress_1.png" alt="training progress"/>

However, the figure below also shows that the model may "forget" some of the learned characteristics, as it tries to learn the weight distribution that maximizes overall accuracy. The model here is well capable of making accurate predictions on the image as early as the 300th iteration, but it "forgets" its learning at the 2850th iteration, even though its overall accuracy is much higher at this iteration.

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/bayesian_training_progress_2.png" alt="training progress"/>

The results of the model show the relevance of the Bayesian approach. The figure below presents results performed on the test data. In addition to the classical predictions, we can also have the DICE performance measure, which is a quantification of the model's measure of certainty with respect to its prediction. The images below show that the model has a high degree of certainty about its predictions, which are actually correct. The model also predicts the variance of the cells, thus specifically showing the areas of uncertainty, by projecting a heatmap on the image, where the red color shows the most uncertainty, and the blue the least uncertainty.

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/bayesian_good_results.png" alt="test results"/>

At the same time, in the new figure below, the model has difficulty making relevant and accurate predictions. But it also returns a very low measure of certainty, which shows its lack of certainty about its results, which are not accurate in the end. This confirms that the measure of certainty can help the model avoid making wrong decisions, thus requiring expert advice and human intervention as soon as the measure of uncertainty exceeds a threshold.

<img src="https://github.com/IhabBendidi/Bayesian_Cellular_Segmentation/blob/main/images/bayesian_bad_results.png" alt="test results"/>

