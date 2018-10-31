# Cifar100-NN-Classifier

**I. Data Preprocessing**<br />

Firstly , the training data is divided to two sets, validation (10%) and training set (90%).Then , the mean image of the training set is calculated by taking the average value of all pixels as follows: <br />
                                                 `mean_img = Xtr.mean()`<br />
The mean image is then used to zero center all input data to the neural network by subtracting it from the training , validation , and testing sets.
Also, the image values are scaled to values between 0 and 1 by dividing every pixel value by **255.0** to make the input data and output data in the same range. 


**II. Sanity Checks**<br />

Sanity checks were applied to make sure that the neural network implementation is correct. The first check is observing the **inital lost**. Since the cifar 100 contains 20 classes
the loss is expected to be **-ln(1/20)** which was the approximately the same value of the initial loss with the randomly initialized weights as shown below: 

![initial loss](https://user-images.githubusercontent.com/25064257/47723134-8ddd6980-dc5c-11e8-967f-1b6eb968f332.png)

The second sanity check is overfitting. I trained the neural network with small numbers of training examples till the training accuracy reached 100%.

![tr](https://user-images.githubusercontent.com/25064257/47723340-fdebef80-dc5c-11e8-8042-e01599197bf0.png)

**III. Hyperparameter Optimization**<br />

 - Min Range of the learning rate
 For a learning rate of value 10^(-10) , the loss is barely changing as shown below: 
 
![min_alpha](https://user-images.githubusercontent.com/25064257/47790998-4c62c200-dd21-11e8-98b3-380d4a9253a5.PNG)

 - Max Range of the learning rate
 For a learning rate of value 10^(-4) , the loss explodes as shown below: 
 
![alpha_max](https://user-images.githubusercontent.com/25064257/47791003-4d93ef00-dd21-11e8-8ed3-d27ea4954a80.PNG)

- Coarse Search
After finding the min and max range of the learning rate, coarse search was run for 100 iterations to fine tune the learning and regularization paramters together. The search was done in the range shown below: 

![search_range](https://user-images.githubusercontent.com/25064257/47791005-4f5db280-dd21-11e8-91ce-ff3c35a824fb.PNG)

- Fine Search
After examining the coarse search results , the range was fixed to be : 

![fine](https://user-images.githubusercontent.com/25064257/47723918-36d89400-dc5e-11e8-9fad-d1cccb4fc859.png)

The best 20 learning paramters that gave the highest validation accuracy are shown below: 

![fine_search_red](https://user-images.githubusercontent.com/25064257/47796365-dbc1a280-dd2c-11e8-9925-643a219ed692.PNG)

**IV. Training with model 0**<br />

Training loss:<br />

![trainloss](https://user-images.githubusercontent.com/25064257/47808727-ae362280-dd47-11e8-8a3b-a839ac53c33b.PNG)

validation loss:<br />

![valid_loss](https://user-images.githubusercontent.com/25064257/47808771-c7d76a00-dd47-11e8-8a14-4160e064b054.PNG)

The validation loss starts to increase after it was decreasing because the model suffered from overfitting.
![acc](https://user-images.githubusercontent.com/25064257/47808774-cc038780-dd47-11e8-9d23-c25e78ecb141.PNG)

The history of the learned paramaters (Weights and biases) were saved and the model with the highest validation accuracy was used to testing giving an accuracy of **37.05%**.<br />
![accr](https://user-images.githubusercontent.com/25064257/47808776-ce65e180-dd47-11e8-8b2b-46fb91a7d63c.PNG)

The correct classification rate for the 20 classes are shown below: 

![ccrn](https://user-images.githubusercontent.com/25064257/47808780-d0c83b80-dd47-11e8-8e69-dedc9fc6c400.PNG)

