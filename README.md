# **Gaussian Mixture Model for Image Data Generation**
## Project Specification
The project is based on the use of Gaussian Mixture Model for Image Data Augmentation by generating new images from the flower image Dataset.

## DataSet
Dataset for this project is taken from [Harvard Dataset](https://dataverse.harvard.edu/file.xhtml?fileId=4105627&version=8.0). Which contains thousands of flowers Images. Around 800 images sample is used from the dataset.

<img src="./assets/Sample%20Images/100080576_f52e8ee070_n.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/5794835_d15905c7c8_n.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/5673728_71b8cb57eb.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/5673551_01d1ea993e_n.jpg" width="200" height="200"/>
<img src="./assets/Sample%20Images/169371301_d9b91a2a42.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/163978992_8128b49d3e_n.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/107592979_aaa9cdfe78_m.jpg" width="200" height="200"/>        <img src="./assets/Sample%20Images/144603918_b9de002f60_m.jpg" width="200" height="200"/>

<br>

# *Methedology*

## **1. Computation Cost Reduction: 'Principal Component Analysis'**
To optimize computation time, grayscale images of size 128x128 pixels are used. Before utilizing a 128x128 figure, it needs to be transformed into a feature vector with a length of 16384.

I have used Principal Component Analysis(PCA) to reduce the number of dimensions of the data. 
<br>
* PCA identifies patterns by analyzing feature correlations and captures high-dimensional data's maximum variance.
* It projects the data onto a lower-dimensional subspace while preserving essential information. 

<p align='center'>
<img  src="./assets/pca.png" width="300" height="200" />
</p>


I considered 99 perent of the variance, hence there will be very little information loss. 
### ***Results***
After applying PCA, the dimentions are tranformed from 16384(128x128) to 588. 

Here PCA recognised 588 features through out the data set. Some of them are shown below.
<p align='center'>
<img  src="./assets/pca_feature.png" width="735" height="270" />
</p>
<br>

## **2. Gaussian Mixture Model: Training and Data Generation**

* Gaussian mixture models (GMMs) assume data points are generated from a mixture of Gaussian distributions, and training them with a dataset helps find suitable parameters.
* By selecting a specific cluster and utilizing its parameters, GMMs can generate samples associated with that cluster.

<p align='center'>
<img  src="./assets/gmm.png" width="300" height="200" />
</p>

**Number of Clusters:**
<br>
The number of clusters for a well-converged GMM model was determined using the 'Akaike Information Criteria' (AIC).
<p align='center'>
<img  src="./assets/ACIs.png" width="300" height="200" />
</p>
The AIC suggested approximately 410 clusters, ensuring significant convergence of the model.

<br>

## **Generated Images**

<img src="./Synthetic%20Data/img_0.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_14.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_4.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_13.jpg" width="200" height="200"/>
<img src="./Synthetic%20Data/img_1.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_7.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_2.jpg" width="200" height="200"/>        <img src="./Synthetic%20Data/img_5.jpg" width="200" height="200"/>

We can see most of the generated Data look plausible flower images.
