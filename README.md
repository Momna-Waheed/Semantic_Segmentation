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
![A3-1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/61114dfa-b1f8-4f4a-8ed1-2760ccc92fc0)
![ACC1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/0ec62ba0-957d-47cf-876f-b0b487611cbb)
![iou1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/2df11b65-c572-4e2d-977a-e36ac1d14a6c)
![Loss1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/67b4ce24-777b-41ce-8cab-08f1ae47257c)
![out1](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/898d6aec-c0d9-4acb-817c-1e60cc82aedf)



### MobileNet-based UNet architecture
In the second approach, we used a MobileNet-based UNet architecture for semantic segmentation. The MobileNet backbone was incorporated into the UNet architecture, leveraging its lightweight and efficient design. The model was trained for 10 epochs using the augmented dataset.

The MobileNet-based UNet demonstrated superior performance with an accuracy of 91\% on the test dataset, surpassing the accuracy achieved by the VGGNet-based UNet.

Similar to the first approach, both qualitative and quantitative results are provided to evaluate the segmentation outcomes. Qualitative results visually illustrate the accurate segmentation of various entities. Quantitative metrics, such as IoU and pixel accuracy, provide an objective evaluation of the model's performance.



![rep2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/1cbc4f29-b8d2-4f29-afaf-b1ddf9c8d8b4)
![ACC2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/d512cff5-97d7-4204-8d16-c0f9cb5ecc2e)
![cm2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/d68c388b-784e-4427-b657-81541d8efc5f)
![iou2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/08a60adc-6411-432a-81b1-5b7349d00137)
![Loss2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/3bdcef71-b32a-4051-8c22-bdefa2934745)
![out2](https://github.com/Momna-Waheed/Semantic_Segmentation/assets/59650991/fb782902-0eb2-4688-8dc1-61754927b39d)

# Model Testing and Enviornment setting
Step by step guideline to execute the model has been provided in the attached notebook along with the all the dependancies and required libraries

