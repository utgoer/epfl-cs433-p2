# epfl-cs433-p2
Project 2 repository for EPFL CS433 for group Polish_Cow.  

Contact us if you have questions or are having problems replicating our results.

Members:  
Ünsal Öztürk  
EPFL - 320826  
unsal.ozturk@epfl.ch  

Mert Soydinç  
EPFL - 321131  
mert.soydinc@epfl.ch  

Utku Görkem Ertürk  
EPFL - 321977  
utku.erturk@epfl.ch  

# Want to replicate our results? See Important: Instructions to run run.py, Running Notebooks, and Useful Commands below. 
 
## Road Segmentation
### Abstract:
We train several classifiers to segment roads from aerial images and compare their performances on the  aerial images dataset. As a baseline, we train a logistic regressor operating on 16x16x3 mini-patches of the image. As for more advanced models, we start by training a CNN operating on 72x72x3 patches with pixel-wise output. We further extend our classifier toolkit by exploring more recent deconvolutional architectures, based on UNets. We establish the 'vanilla' UNet as a baseline deconvolutional model and expand upon this model by increasing the depth of this neural network. We propose two other architectures, which we call Ш-Net and ШЦ-Net, that resemble UNet architecture in terms of skip connections, encoding and decoding. We perform experiments on multiple augmentations of the initial dataset with all these classifiers, and different loss functions. We conclude that a ШЦ-Net with cross-entropy loss achieves the best results in terms of classification accuracy on the test set, namely 95.0 and has an F1 score of 0.909.
 
For more details regarding our project and its implementation, check the paper, the notebooks and the source code.
 
The code contains utilities to generate the dataset, and the paper outlines how to augment the initial data. If you'd like to get access to the original dataset generated by the authors, do not hesitate to contact us. Note that the "large/best" dataset may not fit into RAM.
 
The authors do not also recommend training the models in the notebooks and urge the usage of the pretrained models, as it takes time and considerable computational power.


## Required libraries
If you are running from Anaconda Powershell, you will most probably have the packages below already installed, aside clint, which we use to download files from our repository to replicate our code if you have not done so. To install, go to Anaconda Powershell and type  

<pre>pip install clint</pre>  

Full requirements are as below:  
clint==0.5.1  
numpy==1.19.2  
scikit_image==0.17.2  
torch==1.7.0  
scipy==1.5.2  
tqdm==4.51.0  
requests==2.24.0  
torchvision==0.8.1  
matplotlib==3.3.2  
Pillow==8.0.1  
scikit_learn==0.23.2  
skimage==0.0  

## Important: Instructions to run run.py

You can call 'python run.py' from the terminal (preferably Anaconda Powershell, from the base virtual environment) and it will automatically download the files that are needed for the replication of our submission if they are not present. It will download the pretrained model along with the test images, and generate a submit.csv file. For dataset generation, the script will automatically download the training images. Note that around 20 GB RAM is needed for dataset generation (all data is stored in memory, and is persisted into a file after generation).

Please do note that __download initiated by run.py may take a long time, and you might be better off directly downloading the model (model_shatznet_god.model) and images directly from the repository__. Please do not forget to create the folder hierarchy if you manually download the model and the images. Specifically, your directory should look like this:

```bash
├───models
├───test_set_images
│   ├───test_1
│   ├───test_10
│   ├───test_11
│   ├───test_12
│   ├───test_13
│   ├───test_14
│   ├───test_15
│   ├───test_16
│   ├───test_17
│   ├───test_18
│   ├───test_19
│   ├───test_2
│   ├───test_20
│   ├───test_21
│   ├───test_22
│   ├───test_23
│   ├───test_24
│   ├───test_25
│   ├───test_26
│   ├───test_27
│   ├───test_28
│   ├───test_29
│   ├───test_3
│   ├───test_30
│   ├───test_31
│   ├───test_32
│   ├───test_33
│   ├───test_34
│   ├───test_35
│   ├───test_36
│   ├───test_37
│   ├───test_38
│   ├───test_39
│   ├───test_4
│   ├───test_40
│   ├───test_41
│   ├───test_42
│   ├───test_43
│   ├───test_44
│   ├───test_45
│   ├───test_46
│   ├───test_47
│   ├───test_48
│   ├───test_49
│   ├───test_5
│   ├───test_50
│   ├───test_6
│   ├───test_7
│   ├───test_8
│   └───test_9
└───training
    ├───groundtruth
    └───images
```
You can get these files from this particular repository. Note that downloads are handled from https://github.com/uensalo/epfl-cs433-p2, which has the same exact files, but is not private to enable downloads.

By default it will give the submission file that we submitted to the AIcrowd. Note that we overfit a model (which is in our repository, called model_shatznet_god.model) to achieve the result.

If you don't want to initiate automatic download, you can do it manually. Just download training and test_set_images folder from the github repository and put the folders to the same folder with run.py.
Run run.py directly('python run.py')

For full usage of the run.py you can call -h flag which is shown below.

GitHub link: https://github.com/CS-433/cs-433-project-2-polish_cow

## Running Notebooks
To run the notebooks, download the model associated with the notebook, and do NOT change the hierarchy of the directory given in our repository. Models should stay under /models/, and notebooks should stay under /notebooks/. To skip certain steps, change the boolean variables we provide in the notebooks. Note that unless you are running the notebooks on a server with large RAM (especially for the dataset for our best submission, the generation of which is given under shanet-best-attempt.ipynb, it is very possible that it won't fit into RAM, and if you'd like to train the model, you're going to need 24GB of VRAM).

## Help
By default, run.py does not need any arguments, given that the model is supplied under model/model_shatznet_god.model, training images under 'training/' and test images under 'test_set_images/test_x', arranged as in this repository

optional arguments:  
<pre>
  -h, --help            show this help message and exit  
  --model_path models/model_shatznet_god.model  
                        full path to model file  
  --train_path training/  
                        full path to training set directory, the directory must contain two subdirectories titled  
                        groundtruth/ and images/, and the image files should be called satImage_00x.png  
  --test_path test_set_images/  
                        full path to test set directory, the directory must contain a subdirectory called test_x for  
                        every test image, and each subdirectory must contain a test_x.png  
  --data_path data/     full path to data file directory, the directory must contain the generated data,  
                        augmented_images_train_best.npy and augmented_labels_train_best.npy  
  --load_img            load training set in memory  
  --no-load_img         does not load training set in memory  
  --load_data           load generated training images in memory  
  --no-load_data        does not load generated training images in memory  
  --load_model          load pretrained model in memory  
  --no-load_model       does not load pretrained model in memory  
  --generate_data       generate data and save  
  --no-generate_data    does not generate data and save  
  --train               perform training  
  --no-train            does not perform training  
  --cuda                use cuda, true recommended  
  --no-cuda             does not use cuda, true recommended  
  --dmodel              download the latest model and save  
  --no-dmodel           does not download the latest model and save  
  </pre>
  
  ## Useful Commands
  Run directly (recommended):  
  <pre> python run.py </pre> 
  
  Generate data:  
  <pre> python run.py --load_img --generate_data </pre> 
  
  Train model from scratch from generated images:  
  <pre> python run.py --train --load_data --no-load_model </pre>  
  
  Train model from a previous model from generated images:  
  <pre> python run.py --train --load_data </pre>
  
  Everything from scratch (takes long and needs resources):    
  <pre> python run.py --train --load_img --generate_data --load_data --no-load_model </pre> 
  
  It is better to first generate the data, then train the model to save some RAM. Doing it this way gives an error after data generation. Ignore it. Run:  
  <pre> python run.py --load_img --generate_data</pre> 
  then run:  
  <pre> python run.py --train --load_data --no-load_model </pre>   
  
  We highly recommend one of our pretrained models.
  
  ## A note on AICrowd Submissions
  AICrowd/Model is not deterministic. Sometimes it produces the exact same result as our best submission, sometimes it outputs accuracy/F1 scores with +-  0.001 values. The best we obtained is 0.909 F1 score and 0.951 accuracy. Check submissions #110036, #110029, #110028, #110027 by uensalo on AICrowd. All of these results were generated from the same run.py. Note that we do set our model to evaluation mode. 
