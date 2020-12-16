# epfl-cs433-p2
 Project 2 repository for EPFL CS433 for group Polish_Cow.
 
 ## Road Segmentation
 ### Abstract:
We train several classifiers to segment roads from aerial images and compare their performances on the  aerial images dataset. As a baseline, we train a logistic regressor operating on 16x16x3 mini-patches of the image. As for more advanced models, we start by training a CNN operating on 72x72x3 patches with pixel-wise output. We further extend our classifier toolkit by exploring more recent deconvolutional architectures, based on UNets. We establish the 'vanilla' UNet as a baseline deconvolutional model and expand upon this model by increasing the depth of this neural network. We propose two other architectures, which we call Ш-Net and ШЦ-Net, that resemble UNet architecture in terms of skip connections, encoding and decoding. We perform experiments on multiple augmentations of the initial dataset with all these classifiers, and different loss functions. We conclude that a ШЦ-Net with cross-entropy loss achieves the best results in terms of classification accuracy on the test set, namely 95.0 and has an F1 score of 0.909.
 
 For more details regarding our project and its implementation, check the paper, the notebooks and the source code.
 
 The code contains utilities to generate the dataset, and the paper outlines how to augment the initial data. If you'd like to get access to the original dataset generated by the authors, do not hesitate to contact us. Note that the "large/best" dataset may not fit into RAM.
 
 The authors do not also recommend training the models in the notebooks and urge the usage of the pretrained models, as it takes time and considerable computational power.
