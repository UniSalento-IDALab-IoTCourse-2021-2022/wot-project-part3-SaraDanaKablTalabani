# wot-project-part3-SaraDanaKablTalabani
wot-project-part3-SaraDanaKablTalabani created by GitHub Classroom

Deploy the ML algorithm on the STM32 device: deploying the algorithm also includes developing the supporting
functions to receive data over BLE, perform inference, create notifications in case of anomalies and then
transmit them. The anomaly score should also be transmitted to a database (via a protocol of ).

The X cube AI has been realesed to help us to deploy small ML model which has been trained privoiusly using Keras, Tensorflow and onex on the STM32 MCU. MCU are limited in resoucres and therefor the X Cube AI used to help us to convert the model and fitting it on the our chosen system. From the X cube AI we can use function to run inference using our model.
Inference is the process of running new unseen data through our machine learning model.
We will use the ML model which is avialable in part 2. We trained an autoencoder to detect anomalies on the ECG5000 dataset. This dataset contains 5,000 Electrocardiograms, each with 140 data points. You will use a simplified version of the dataset, where each example has been labeled either 0 (corresponding to an abnormal rhythm), or 1 (corresponding to a normal rhythm). We want to identify the abnormal rhythms.

Note: This is a labeled dataset, therefore we could consider this as a supervised learning case. One of the aim of this work is to show anomaly detection. In future work we will try to apply this to larger datasets, where you do not have labels . For example, if we had many thousands of normal rhythms, and only a small number of abnormal rhythms.

Autoencoder: it is trained to minimize reconstruction error. We trained an autoencoder on the normal rhythms only, then use it to reconstruct all the data. Our hypothesis is that the abnormal rhythms will have higher reconstruction error. You will then classify a rhythm as an anomaly if the reconstruction error surpasses a fixed threshold. 

![image](https://user-images.githubusercontent.com/101463904/186467538-38f21c8e-2c1d-4286-a187-511eaffae21a.png)


The link to the dataset which we used:

http://storage.googleapis.com/download.tensorflow.org/data/ecg.csv

the normal rhythms in the dataset is labled as 1 and the abnormal rhythms as 0. 

Note: the autoencoder is trained utlizing the normal ECGs only, while is tested utlizing the full test set.

We classified an ECG as anomalous if the reconstruction error is greater than one standard deviation from the normal training examples.

Detect anomalies:

Detect anomalies by computing whether the reconstruction loss is greater than a fixed threshold. We computed the mean average error for normal examples from the training set, then classify future examples as anomalous if the reconstruction error is higher than one standard deviation from the training set.

Classify an ECG as an anomaly if the reconstruction error is greater than the threshold.

![image](https://user-images.githubusercontent.com/101463904/186529502-81b679a3-c5a8-4c67-88dc-ddf8a073b0f6.png)
![image](https://user-images.githubusercontent.com/101463904/186530901-f4f4f3ad-1ba5-436b-b373-32fcc1880c07.png)



1 npm install -g edge-impulse-cli --force
We trained the model.

We trained an autoencoder to detect anomalies on the ECG5000 dataset. This dataset contains 5,000 Electrocardiograms, each with 140 data points. You will use a simplified version of the dataset, where each example has been labeled either 0 (corresponding to an abnormal rhythm), or 1 (corresponding to a normal rhythm). We are willing to identify the abnormal rhythms.

Note: This is a labeled dataset, so we could consider this as a supervised learning case. The goal of this ML program is to show anomaly detection concepts.

An autoencoder is trained to minimize reconstruction error. You will train an autoencoder on the normal rhythms only, then use it to reconstruct all the data. Our hypothesis is that the abnormal rhythms will have higher reconstruction error. You will then classify a rhythm as an anomaly if the reconstruction error surpasses a fixed threshold.

Then we deploy the on STM32 microcontroller(MC).
Then by using functions we run inference using that trained model on the STM32 MC.
![image](https://user-images.githubusercontent.com/101463904/184451368-f0c676d0-1019-494b-8246-38243d0ab6c7.png)
![image](https://user-images.githubusercontent.com/101463904/184451968-0189a96a-4da4-4da5-beee-3abb4acad278.png)
![image](https://user-images.githubusercontent.com/101463904/184452475-619767ad-23b0-41b0-bc7d-c298486835ef.png)
![image](https://user-images.githubusercontent.com/101463904/184452555-0da91982-4a07-4cbf-868d-657bfef5e45c.png)
![image](https://user-images.githubusercontent.com/101463904/184453216-5928d356-14ca-45dc-8d3a-efb1faffdd48.png)
Now, our model has been deployed STM32 Dscovery kit. Then we run inference function in our MCU using our model in X cube AI to detect the anomalies in our dataset. Our model is pretrained using colab and we run the inference from there also. We conferted the .h to .tflite file to be be able to imported to the X cube AI. We used STM32 Discovery kit IoT node for STM32L475 MCU.
The follows are the steps to do that: 
1. We istalled the AI pachage on x cube AI.
2. we navigate to the board selector section and we selected our board.
3. Name the project. We named the project as De.
4. We analyed the model which give us some information about its relative complixity such as how much RAM it needs and the number of NCC opertation it requires.
5. We could show the graph of our network model as the following image:


![image](https://user-images.githubusercontent.com/101463904/187089188-a8c1eb17-560c-4656-ba95-1f011494987c.png)

Note: this part of our network model.
6.Validsate on target and it works properly.
7.Validsate on desktop and it works properly.
8. We named our model as network.
9.Generate the code.

Notes:
- It is applicable to load more than one model at the same but we need to have the required space for them.
- in App open network.c this houses the function that we need to use to intiliaze our model and run inference.
- The network_data.c is our nueral network and it is a big raw byte array that our x cube AI LIBRARY know HOw TO INTERPERT it

10. Now we modify the main.c with the following:

First we insert the required libraries such as the c standard inout ouput library and others:

![image](https://user-images.githubusercontent.com/101463904/187090367-79e46f04-2876-46ff-b9bc-586f4406e893.png)

Next in main we declare some variables that help us such as buffere that for our serial output string, error code and a time stamp:

![image](https://user-images.githubusercontent.com/101463904/187090611-c79de36c-e4ad-4a01-bfc4-1a900ab367eb.png)






       

 

References:

http://storage.googleapis.com/download.tensorflow.org/data/ecg.csv

https://youtu.be/crJcDqIUbP4


