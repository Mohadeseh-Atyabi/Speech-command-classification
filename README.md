# Speech-command-classification
This project aims to implement a voice assistant to recognize and classify the command into one of the 12 classes. These titles incude the following: bonds (اوراق), currency (ارز), coin (سکه), bank (بانک), gold (طلا), petroleum (نفت), derivatives (مشتقات), metals (فلزات), stock fund (صندوق سهامی), fixed income fund (صندوق درامد ثابت), mixed fund (صندوق مختلط), tradable fund (صندوق قابل معامله). The commands are recorded and trained in Persian. To do so, we implemented a custom convolutional neural network in Python and trained it to get a high accuracy of 85%.

# Dataset
We have a root folder named 12words, which has a separate folder for each class. There are 40 samples for each class in the related folder. An overview of the directory is shown below:

![image](https://github.com/Mohadeseh-Atyabi/Speech-command-classification/assets/72689599/8a5a120e-b2eb-497f-a79b-99597c4b9216)

So our dataset has 480 samples for train and test which is splitted in the ratio of 80 10 10 for train and test and validation. After loading the data to make a proper dataset, we applied a transformation. We downsapled the waveform for faster processong without lossing too much of the classification power.

# Methodology
In this project, we used a custom CNN to process the raw data. Usually, more advanced transformations are applied to voice data, but CNNs can be used for more accurate processing of raw data. Our particular architecture consists of five layers. Each layer is a combination of a convolutional layer, batch normalization, and max pooling. After the last layer, we have a linear layer outputting the result as a classification. The image below shows the overall architecture of this model with the size of each layer and the total number of parameters.


![image](https://github.com/Mohadeseh-Atyabi/Speech-command-classification/assets/72689599/a830bf9b-ae42-45d1-8c71-648b516e4c53)

The optimizer in this project is Adam having a learning rate of 0.01, and the scheduler function decrease it after 20 epochs to 0.001. We used cross-enthropy as the cost function.

# Results
The model is trained on the training dataset for 60 epochs with a batch size of 6, evaluating the weights using the validation dataset. The diagram of loss in each epoch for training data is shown below.

![download](https://github.com/Mohadeseh-Atyabi/Speech-command-classification/assets/72689599/c2722ca6-81d1-40a8-a493-98a60b3c1aac)

As you can see, the general flow of the loss is decreasing. The decreasing flow of the chart in continuous iterations demonstrates the appropriate functionality of the model. The accuracy for the test dataset is 88% which reports the model's high accuracy encountering new data. Another metric used to evaluate the model is the confusion matrix. In this matrix, the vertical axis shows the true label of the test data, and the horizontal axis showa the predicted label for the same data. The result is reported in the figure below.

![download (1)](https://github.com/Mohadeseh-Atyabi/Speech-command-classification/assets/72689599/c7b8543d-c42c-44fe-91a0-a8a7ca0f382e)

As expected, most of the data is located on the main diameter, which means that most of the labels are correctly recognized and few predictions are incorrect.
