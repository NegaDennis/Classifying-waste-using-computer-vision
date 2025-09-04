# Classifying-waste-using-computer-vision

## About the project
The project aim to utilize computer vision capabilities in Python to classify waste via image data. In particular, it will experiment with the tensorflow library to create a few neural network-based machine learning model for the task.

One important note is that the project will be done using Google Colab as a platform and will only use its free version without incurring any additional cost. This means that the project will be limited in available processing and computing power.

For this reason, only 3 model architectures were covered in the experiment. The fine tuning process is also very modest due to the same reason. More detail on this matter will be discussed in the develop process section.

## The problem

![waste management](https://github.com/user-attachments/assets/6a123c89-dcb1-4564-9ed5-9994618b85d3)
Photo by <a href="https://unsplash.com/@filmbetrachterin?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Jas Min</a> on <a href="https://unsplash.com/photos/assorted-plastic-bottles-in-black-plastic-bucket-CIItgnBEOgw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
      

Waste management is one of the key tasks in maintaining a modern and civil society. Using traditional methods, handling such task is getting increasing harder and can get overwhelmed by the amount of trash an ever-increasing population produce.

In light of that problem, organization A is looking to employ machine learning and AI to alleviate the workload. Particularly, computer vision comes to mind as a great assistance to waste classification, an important stage in waste management. Instead of having people manually seperating one type of trash from another, an AI would process pictures of waste and determine waste type and eliminate the need for a menial and time/resource-consuming task.

## The dataset
To train and test the model, a dataset consisting of 2,864 real images of 6 different types of wastes (i.e., wastes, namely cardboard, glass, metal, paper, plastic and vegetation) was provisioned.

|Type|Example|
|---|---|
|Glass|![Glass_1](https://github.com/user-attachments/assets/d10edfd0-8773-49ac-9521-0b6abd5e5ede)
|
|Paper| ![Paper_11](https://github.com/user-attachments/assets/dfd93204-5a2a-4bf7-bc98-2ea7d8784c9a)
 |
|Cardboard| ![Cardboard_122](https://github.com/user-attachments/assets/c098c46c-9709-4295-a8b5-b501380d0224)
 |
|Plastic| ![Plastic_148](https://github.com/user-attachments/assets/938d30cd-79d2-48cd-a713-eb66160842b2)
 |
|Vegetation| ![Vegetation_111](https://github.com/user-attachments/assets/65d35a08-45aa-4a14-9d86-4bea73c51b69)
 |
|Metal| ![Metal_109](https://github.com/user-attachments/assets/7b1743f4-56f4-4edf-acaf-829b81037ac8)
 |

## The approach
To tackle the problem and sufficiently make use of the dataset, Python will be the tool of choice. Particularly, Python library, Tensorflow, will be the main character in doing much of the heavy lifting in building a neural network model. Additionally, some standard data analytics libraries will also be employed for background purposes (e.g., dealing with arrays, making dataframes, data visualization).

A list of libraries used in the project can be found below:
 
<img width="665" height="656" alt="libraries" src="https://github.com/user-attachments/assets/2cf09b63-83d2-4880-98eb-89cda1628273" />
 
Since this project aims at experimentation, it will only concerns with documentation and observation of experimented models. The final product would be a comparison table detailing important aspects of performance of the models. (random seed is set so the model is absolutely reproducible using the code file).

## The development process
The general stages in development can be found in the below diagram.
 
<img width="1361" height="321" alt="workflow (project 6)-Waste classification drawio" src="https://github.com/user-attachments/assets/2be5dcc1-726f-46bd-8113-7fdcd7066b5a" />
 
Since the scope is entirely on experimenting with AI computer vision capability, there will be no EDA stage. After some preparation of data and folder arrangement, the modelling process commenced promptly. 3 models with different architectures were defined and tried:

1) Traditional, single flatten layer Artificial Neural Network (ANN):

Model architecture: The first model developed has a traditional ANN architecture. In this instance, the model contains only one flatten layer, one hidden layer, one additional layer, and the output layer. All layers are fully connected.

Model parameters:
  - In the first layer, The models takes in the parameters about the images' resolution (i.e., 50x50), and uses 3 color channels to interpret 2-D images as 1-D vectors (flattened).
  - The second layer is composed of 128 neurons and uses Rectified Linear Unit activation function.
  - The third layer uses 'Dropout' method that randomly sets 20% of input values into 0 to avoid overfitting.
  - The final layer uses the same number of neurons as the number of classes of waste (i.e.,6), and uses softmax as the activation function which shows a probability distribution over possible classifications.

2) Convolutional layers CNN:

Model architecture: In addition to all the layers of the first model, this model uses additional ones with convolution technique to increase the accuracy of predictions. In more detail, the first layer will take in the images' data as input and uses convolutional analysis to intepret the data. The second layer uses MaxPooling method to reduce the spatial dimensions and downsample the input. Another layer of Dropout is added to avoid overfitting and then the layers of the first model are added.

Model parameters:
  - In the first layer, The model uses 2-dimensional convolutional technique to interpret the images' data with a kernel size of 3x3. It still uses Rectified Linear Unit as activation function and the same input shape like the first model. This layer also takes a parameters of 50 filters, having the kernel "slides" across the images in 50 different areas with size 3x3.
  - The second layer, MaxPooling, uses a pool size of 2x2. Tihs means it will condense the feature maps (i.e., the images being divided into pixels) into smaller ones by taking out the maximum value of every block of pixel with size 2x2.
  - The third layer uses Dropout method that randomly sets 25% of input values into 0 to avoid overfitting.
  - The remaining layers are essentially the same as the first model with the only difference being the rate of Dropout being 50% instead.

3) Convolutional layers CNN with different parameters:

Model architecture: This model's architecture is the same as the second model. Only some hyperparameters were tweaked.

Model parameters:
  - The first difference is in the first layer, having the number of filters being 32 instead of 50.
  - The second difference is in the second Dropout layer having a transformation ratio of 0.4 instead of 0.5.

## The result

The experiment goes through the same process for all models. All three models used the same training and testing data, and are evaluated using the same metrics (e.g., recall, precision, f-1 score). Further exploration was also done to explain the level of performance of each model using different methods(e.g.,confusion matrix, eye-balling images, data visualizations).

Model 1 with ANN architecture fell short with no real classification power. The best Convolutional Artificial Neural Network model (CNN), model 3, returned an overall accuracy of 69% on unseen data (the test set). Its best performing class is 'Vegetaion' (88% accuracy) and worst performing class is 'Plastic'(54% accuracy).
