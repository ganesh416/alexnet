# alexnet




# structure of Alexnet:
     
     
     
     ![image](https://user-images.githubusercontent.com/83450364/121547999-4598a180-ca2a-11eb-9f44-760862d18c96.png)

AlexNet was the first convolutional network which used GPU to boost performance. 

1.      AlexNet architecture consists of 5 convolutional layers, 3 max-pooling layers, 2 normalization layers, 2 fully connected layers, and 1 softmax layer. 

2.      Each convolutional layer consists of convolutional filters and a nonlinear activation function ReLU. 

3.      The pooling layers are used to perform max pooling. 

4.      Input size is fixed due to the presence of fully connected layers.

5.      The input size is mentioned at most of the places as 224x224x3 but due to some padding which happens it works out to be 227x227x3 

6.      AlexNet overall has 60 million parameters.

Model Details 
The model which won the competition was tuned with specific details-

1. ReLU is an activation function 

2. Used Normalization layers which are not common anymore 

3. Batch size of 128 

4. SGD Momentum as learning algorithm 

5. Heavy Data Augmentation with things like flipping, jittering, cropping, color normalization, etc. 

6. Ensembling of models to get the best results. 

AlexNet was trained on a GTX 580 GPU with only 3 GB of memory which couldn’t fit the entire network. So the network was split across 2 GPUs, with half of the neurons(feature maps) on each GPU. 

This is the reason one can see a split in the architecture diagram. 

Key Features
Overlapping Max Pooling

alexnet
To down-sample an image or a representation, Max Pool is used. It reduces its dimensionality by allowing assumptions to be made about features contained in the sub-regions binned. 

Overlapping Max Pool layers are similar to Max Pool layers except the adjacent windows over which the max is calculated overlaps each other. The authors of AlexNet used pooling windows, sized 3×3 with a stride of 2 between the adjacent windows. Due to this overlapping nature of Max Pool, the top-1 error rate was reduced by 0.4% and top-5 error rate was reduced by 0.3% respectively. If you compare this to using a non-overlapping pooling windows of size 2×2 with a stride of 2, that would give the same output dimensions.

ReLU Nonlinearity 
Using ReLU non-linearity, AlexNet shows us that deep CNN’s can be trained much faster with the help of saturating activation functions such as Tanh or Sigmoid. The figure shown below shows us that with the help of ReLUs(solid curve), AlexNet can achieve a 25% training error rate. This is six times faster than an equivalent network that uses tanh(dotted curve). This was tested on the CIFAR-10 dataset.


Data Augmentation 
When you show a Neural Net different variation of the same image, it helps prevent overfitting. It also forces the Neural Net to memorize the key features and helps in generating additional data. 

Data Augmentation by Mirroring

Let’s say we have an image of a cat in our training set. The mirror image is also a valid image of a cat. This mean that we can double the size of the training datasets by simply flipping the image above the vertical axis.


Source: https://www.learnopencv.com/wp-content/uploads/2018/05/AlexNet-Data-Augmentation-Mirror-Image.jpg
Data Augmentation by Random Crops

Also, cropping the original image randomly will lead to additional data that is just a shifted version of the original data.

The authors of AlexNet extracted random crops sized 227×227 from inside the 256×256 image boundary, and used this as the network’s inputs. Using this method, they increased the size of the data by a factor of 2048.


Source: https://www.learnopencv.com/wp-content/uploads/2018/05/AlexNet-Data-Augmentation-Random-Crops.jpg
Dropout
During dropout, a neuron is dropped from the Neural Network with a probability of 0.5. When a neuron is dropped, it does not contribute to forward propagation or backward propagation. Every input goes through a different Neural Network architecture, as shown in the image below. As a result, the learned weight parameters are more robust and do not get overfitted easily.

