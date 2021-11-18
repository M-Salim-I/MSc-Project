# MSc Project - 170050601

## AI-based method for objective clinical assessment and grading of fibrosis in the bone marrow.

Note: Source code as well as others will not run as they are tailored to a certain directory, all directories must be modified and created in order for the code to execute, especially when preprocessing the data i.e. extraction of the patches from the images which requires the user to create 60 image folders with images folder names from img1 to img63 skipping img51, img57, and img60 skipped as they run into an OpenSlide error for the image file being too large.

### Data Sheets & CSV files.
- imgs_info.xlsx - contains the inforamtion about each image along with one of the sheets (imgs_df) used as a dataframe which is the csv file.
- imgs_df.csv - contains the image number and its grade.

### Original images 
The original images are stored in my scratch folder as well as in the USB. Permissions to acces these must be asked to Dr Hasan Rizvi (email: h.rizvi@qmul.ac.uk, hasan.rizvi@nhs.net)

### Files
#### Datasets
##### Segmentation
- 
##### Classification
- X_patches.pickle, y_patches.pickle - are the patches dataset for the classification model.
- X_balanaced_full_da.pickle, y_balanced_full_da.pickle - masks dataset that minimizes the dataset (i.e. Masks (minimized) in the paper).
- X_g1_unbalanced.pickle, y_g1_unbalanced.pickle - masks dataset that minimizes all grades except for grade 1 (i.e. Masks (g1 unbalanced) in the paper).
- X_test.pickle, y_test.pickle - contains the test set for the masks
Note: no tests set for the patches as the the validation data determined it was not needed.
#### Extraction of patches from the images
- extract.py - shows the extraction and filtration of the discriminative patches from the images.
- openslide.qsub - extracts the patches from the images using the Andrena cluster by submitting the job (this may take upto/over 24hrs to run).
#### Other files
-  getting_dataset.ready.py - ensures the patches are ready to be fed
   into the models.
- evaluations.py - the evaluation metrics used in this project (except for accuracy which is already built-in).
- classification_model.py - the classification model used in this project.
- plotting.py -  the plots that are used in this project.
- losses.py  - python file for the metrics and loss functions used by
   the segmentation models.
#### Segmentation models are found in the following python files:
- ar_unet.py - Attention Residual U-Net
- att_unet.py - Attention U-Net
- basic_unets.py - U-Net, VGG16 U-Net
#### Jupyter Notebooks
- train_cnn.ipynb - is the notebook that trains the classification model
- train_s.ipynb - is the notebook that trains the segmentations model
- final_eval.ipynb - is the notebook that evaluates 15% of the patches from each image using the predictions of the classification and segmentation model.
#### Trained Weights for the best models
- unet_try.hdf5 - trained model weights for the U-Net model
- vgg16_unet_try.hdf5 - trained model weights for the VGG16 U-Net model
- att_unet_try.hdf5 - trained model weights for the Attention U-Net model
- att_res_unet_try.hdf5 - trained model weights for the Attention Res U-Net model
- model_triying_dummy.hdf5 - trained model weights for the classification model
