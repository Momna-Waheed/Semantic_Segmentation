# Semantic Segmentation
This assignment focuses on semantic image segmentation, which involves classifying pixels in an image into predefined classes. Two convolutional neural network (CNN) architectures are used for this task. The first architecture serves as a baseline, utilizing  U-Net with VGG Net as the backbone. The second architecture enhances the baseline by experimenting with a different CNN backbone i.e. MobileNet. The goal is to compare the results of both architectures and determine if the second architecture outperforms the first. This research contributes to improving scene understanding and has applications in object recognition, scene analysis, and autonomous systems.

<!--ts-->
Contents
<!--te-->

<!--ts-->
* [Goal](##Goal)
* [Dataset](##DataSet)
* [Augmentation](##Augmentation)
* [Methodology and Results](##MethodologyandResults)
	* [VGGNet-based UNet architecture](###VGGNetbasedUNetarchitecture)	
	* [MobileNet-based UNet architecture](###MobileNetbasedUNetarchitecture)
* [Model Testing and Enviornment setting](##ModelTestingandEnviornmentsetting)
<!--te-->

## Goal 
The primary objective of this assignment is to compare the results of both architectures, emphasizing the significant impact of image augmentation on segmentation performance. We have made use of data augmentation techniques to generate a diverse and augmented training set since the available labeled datasets for semantic segmentation are not that extensive as pixel level annotations and labeling is an expensive and time taking task. Evaluation metrics include both qualitative assessments, such as visual inspection of segmentation maps, as well as quantitative metrics, including pixel accuracy, mean Intersection over Union (mIoU), and F1 score.

## DataSet 
The dataset used in this assignment is a subset of the Cityspace Dataset, which has been pre-divided into train and test splits. For validation purposes, the Train split can be further divided, with 80\% of the data allocated for training and 20\% for validation.

The dataset used in this assignment is a subset of the Cityspace Dataset, which has been pre-divided into train and test splits. For validation purposes, the Train split can be further divided, with 80% of the data allocated for training and 20% for validation.

The dataset consists of images with pixel-level annotations for the following classes:
1. Sky
2. Building
3. Pole
4. Road
5. Pavement
6. Tree
7. SignSymbol
8. Fence
9. Car
10. Pedestrian
11. Bicyclist

The dataset statistics are as follows:
- Total Train Images: 293
- Total Validation Images: 74
- Total Test Images: 101

## Data Augmentation

In order to enhance the performance of our semantic image segmentation models, we have utilized data augmentation techniques. Data augmentation involves applying various transformations and modifications to the existing dataset to increase its diversity and provide additional training examples.

The following augmentation techniques have been employed using the Albumentations library:

1. HorizontalFlip: This augmentation horizontally flips the images and their corresponding masks. By flipping the images, we introduce variations in object orientations and improve the model's ability to handle objects from different perspectives.

2. Rotate: The Rotate augmentation randomly rotates the images and masks within a specified range. This helps the model learn to segment objects at different angles and orientations, improving its robustness to variations in object rotation.

3. RandomScale: The RandomScale augmentation randomly scales the images and masks by a certain factor. Scaling the images allows the model to handle objects of different sizes and helps in capturing variations in object scales present in the real-world images.

4. GaussNoise: The GaussNoise augmentation adds random Gaussian noise to the images and masks. This helps the model become more resilient to variations in pixel intensity and improves its ability to segment objects in noisy or degraded images.

5. Perspective: The Perspective augmentation applies a random perspective transformation to the images and masks. This transformation simulates changes in viewpoint or camera angles, enabling the model to generalize well to images captured from different perspectives.

By applying these augmentation techniques, we increase the diversity and variability of the training dataset. This augmentation process helps the model generalize better by exposing it to a wider range of variations that it may encounter during inference on unseen data.

After applying the augmentations, the augmented images and masks are resized to a specific width and height. This ensures consistency in input size for the segmentation model. The augmented images and masks are then saved to the designated save path, with each augmented version having a unique filename to indicate the applied augmentation.

The incorporation of data augmentation techniques aids in improving the segmentation model's performance by providing it with more diverse training examples. This augmentation process helps the model learn robust and accurate segmentation boundaries, leading to better segmentation results on unseen images.

### Transformed Dataset Size

After augmentation, the size of the transformed dataset is as follows:

- Train Size: 2055
- Val Size: 514


## Methodology and Results

To achieve mentioned goal, two CNN backbone architectures Vgg and Mobilenet are used with UNet
### VGGNet-based UNet architecture
In the first approach, we utilized a VGGNet-based UNet architecture for semantic segmentation. The UNet architecture is known for its effectiveness in capturing fine-grained details while maintaining spatial information. The VGGNet served as the backbone for feature extraction in the network. The model was trained for 10 epochs using the augmented dataset.

The VGGNet-based UNet achieved an accuracy of 89\% on the test dataset. The accuracy metric provides an assessment of how well the model classifies each pixel into the predefined classes.

Both qualitative and quantitative results are presented to evaluate the segmentation performance. Qualitative results include visualizations of the segmented images, highlighting the model's ability to accurately classify different entities. Quantitative results involve metrics such as intersection over union (IoU) and pixel accuracy, which provide an objective evaluation of the segmentation performance.
![ACC1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/07c0d023-33af-4f88-9f5c-0c4b6a045801)
![rep1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/b2c389dd-3383-4bec-b05a-ae1f1bdb1710)
![cm1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/0bca837c-155e-4c09-9e6d-bfae1f3957e4)
![iou1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/9d52ffd1-3f53-4987-9090-1e7da555a32f)
![Loss1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/7a8b2d3f-01df-44fa-a18d-3bb030cfffa7)
![out1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/345de323-b8c1-4462-abf2-d3c7af4a4b50)


### MobileNet-based UNet architecture
In the second approach, we used a MobileNet-based UNet architecture for semantic segmentation. The MobileNet backbone was incorporated into the UNet architecture, leveraging its lightweight and efficient design. The model was trained for 10 epochs using the augmented dataset.

The MobileNet-based UNet demonstrated superior performance with an accuracy of 91\% on the test dataset, surpassing the accuracy achieved by the VGGNet-based UNet.

Similar to the first approach, both qualitative and quantitative results are provided to evaluate the segmentation outcomes. Qualitative results visually illustrate the accurate segmentation of various entities. Quantitative metrics, such as IoU and pixel accuracy, provide an objective evaluation of the model's performance.
![rep2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/5808e82c-c41f-475a-a9d7-3b441da9531b)
![ACC2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/dc0d3bf2-98bb-4fb1-bf41-d2c450bf275f)
![cm2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/89e2e311-5897-4ac7-958d-6f181d96e012)
![dice2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/979d639f-757b-4d67-9ccc-cc3c2e98cc4d)
![iou2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/d2bb7527-4bac-41c2-af93-45b4cde666e5)
![Loss2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/217f5fa1-30bc-4dff-9449-ec5677535697)
![out2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/eb1d8be1-5340-4a30-96d6-229378c4090f)

# Model Testing and Enviornment setting
Step by step guideline to execute the model has been provided in the attached notebook along with the all the dependancies and required libraries

