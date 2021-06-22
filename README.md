# ML-Audio-Clustering
Experimented with different audio feature extraction techniques and created a deep Learning-based feature extraction method to cluster the audios based on their features.

Deep neural networks are popular for various image processing or NLP tasks. In recent times, however, research focused on audio tasks using deep learning techniques has seen a surge. Some of the deep learning techniques have been adopted from image processing tasks, however audios are quite different as they are one-dimensional time series signal which is different from two-dimensional images. Deep learning methods with audio as input are important as audio is a very prevalent medium in our daily lives. In this project, the main objective was to train a deep neural network for the purpose of feature extraction, clustering or both. The aim was to use this network to successfully extract feature from audio samples and cluster them into 20 clusters. Clustering could be part of the network or a separate function could be used. For this project, I converted the audio samples into spectrograms and saved them as images. A sample spectogram can be seen below. 

![1](https://user-images.githubusercontent.com/32781544/122900897-e7a96b00-d301-11eb-9957-38fe456c9648.png)

Then I used an autoencoder to compress and reconstruct the images. The autoencoder consists of the encoder and decoder. Following is the model structure.

![pr3diag](https://user-images.githubusercontent.com/32781544/122900734-cb0d3300-d301-11eb-89f1-44a25cef32d2.png)

The encoder and decoder are block based i.e. I split the original image (spectrogram) into equal sized blocks of size (144, 144, 3) and input those to the encoder. The encoder compresses the original block to size (9, 9, 1) which is a compression ratio of 0.0013. Follwing figure shows the image of size (288, 432, 3) being split into 6 equal sized blocks. 

![blocks](https://user-images.githubusercontent.com/32781544/122900873-e37d4d80-d301-11eb-8c22-beab0321402e.png)

Since there were 671 samples, my dataset consisted of 4026 total blocks. I then trained the autoencoder model to compress and reconstruct the spectrograms. I used the encoder to predict the original spectrograms. The output is the compressed version of the samples thereby extracting important features. I used these features to cluster the audio samples using K-Means algorithm into 20 possible clusters.

![image](https://user-images.githubusercontent.com/32781544/122902771-9ef2b180-d303-11eb-925b-14a85d584b51.png)

