# Term-Paper

The algorithm used in MoCo has some key parameters such as batch size, number of epochs, etc., based on which the accuracy of the self-supervised learning model is expected to vary. The encoder convolutional network used for our MoCo model has 2 convolutional layers and 1 fully connected layer. The standard convolutional net for baseline has 2 convolutional layers, 3 fully connected layers.

We study unsupervised training performed in CIFAR-10 dataset.

We vary the following parameters to study their effect on the accuracy of the MoCo model and report the findings, one at a time. The original parameters were TrainingDataSize:TestingDataSize = 1:5, Augmentations = Aug0 (mentioned below), NumberOfEpochs = 20, QueueSize = 4096, VectorDimension = 128 and BatchSize = 100.

## Ratio of sizes of the training and the testing datasets

The CIFAR-10 dataset consisting of 60000 images from 10 different classes is divided into the following ratios: 10:90 (6000 images in the training dataset and 54000 images in the testing dataset), 20:80, 30:70, 40:60, 50:50 in this order. The total size of the dataset used (both training and testing datasets combined) remains constant. We compare the accuracies of the unsupervised model with the corresponding accuracies of the supervised model for each ratio of the sizes of the training and the testing datasets.

We observe the following:
The accuracy of the unsupervised learning model consistently increases with the size of the training dataset and the consequent decrease in the size of the testing dataset.

The accuracy of the supervised learning model also increases with the increase in the size of the training dataset.

The accuracies of the supervised learning model are less than the corresponding accuracies of the unsupervised learning model until the ratio of the sizes of the training and testing datasets is 50:50.

As the size of the testing dataset increases, the gap between the accuracies of the supervised model and the unsupervised model reduces in general. In our experiment, we observe that this is true until the ratio becomes 40:60. We observe that the gap increases for the ratio 50:50 as compared to the ratio 40:60.

Based on the above observations, we infer that the larger the size of the training dataset, the higher the accuracy of the unsupervised model. Furthermore, the unsupervised model performs better than the supervised model to a certain extent. We hypothesize that as the size of the training dataset increases, the supervised model may fare better than the unsupervised model.

## Augmentations

We use different sequences of augmentations. The labels we use for the various augmentations we
use are as follows:

* Aug0: Crop and Resize, Color distort (drop), Color distort (jitter), Rotation
* Aug1: Color distort (jitter), Gaussian blur, Horizontal flip, Color distort (drop)
* Aug2: Crop and Resize, Sobel filtering, Color distort (jitter), Rotate
* Aug3: Crop and Resize, Sobel filtering, Gaussian blur, Color distort (drop)
* Aug4: Horizontal flip, Gaussian blur, Rotate, Color distort (jitter), Crop and Resize
* Aug5: Horizontal flip, Gaussian blur, Rotate, Color distort (jitter), Crop and Resize
* Aug6: Color distort (jitter), Color distort (drop), Horizontal flip, Crop and Resize

