# wot-project-part3-SaraDanaKablTalabani
wot-project-part3-SaraDanaKablTalabani created by GitHub Classroom

Deploy the ML algorithm on the STM32 device: deploying the algorithm also includes developing the supporting
functions to receive data over BLE, perform inference, create notifications in case of anomalies and then
transmit them. The anomaly score should also be transmitted to a database (via a protocol of ).
1 npm install -g edge-impulse-cli --force
We trained the model.

We trained an autoencoder to detect anomalies on the ECG5000 dataset. This dataset contains 5,000 Electrocardiograms, each with 140 data points. You will use a simplified version of the dataset, where each example has been labeled either 0 (corresponding to an abnormal rhythm), or 1 (corresponding to a normal rhythm). We are willing to identify the abnormal rhythms.

Note: This is a labeled dataset, so we could consider this as a supervised learning case. The goal of this ML program is to show anomaly detection concepts.

An autoencoder is trained to minimize reconstruction error. You will train an autoencoder on the normal rhythms only, then use it to reconstruct all the data. Our hypothesis is that the abnormal rhythms will have higher reconstruction error. You will then classify a rhythm as an anomaly if the reconstruction error surpasses a fixed threshold.

Then we deploy the on STM32 microcontroller(MC).
Thee by using functions we run inference using that trained model on the STM32 MC.
