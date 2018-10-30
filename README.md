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
 For a learning rate of value 10^(-9) , the loss is barely changing as shown below: 
 
 ![min](https://user-images.githubusercontent.com/25064257/47723655-a26e3180-dc5d-11e8-92fd-def349f14a3d.png)

 - Max Range of the learning rate
 For a learning rate of value 10^(-2) , the loss explodes as shown below: 
 
![max](https://user-images.githubusercontent.com/25064257/47723676-b44fd480-dc5d-11e8-8372-1a014a1d706e.png)

- Coarse Search
After finding the min and max range of the learning rate, coarse search was run for 100 iterations to fine tune the learning and regularization paramters together. The search was done in the range shown below: 

![range](https://user-images.githubusercontent.com/25064257/47723846-0c86d680-dc5e-11e8-9b00-aa5a0053cee2.png)

- Fine Search
After examining the coarse search results , the range was fixed to be : 

![fine](https://user-images.githubusercontent.com/25064257/47723918-36d89400-dc5e-11e8-9fad-d1cccb4fc859.png)

The best 20 learning paramters that gave the highest validation accuracy are shown below: 

![models](https://user-images.githubusercontent.com/25064257/47723972-5e2f6100-dc5e-11e8-954c-7576cbab766e.png)

**IV. Training with model 0**<br />

Training loss:<br />

![tr_loss](https://user-images.githubusercontent.com/25064257/47725701-ac922f00-dc61-11e8-97fc-f95b5b76b1a7.png)

validation loss:<br />

![valid_loss](https://user-images.githubusercontent.com/25064257/47725729-bd42a500-dc61-11e8-9d35-05baa7e15a9a.png)

The validation loss starts to increase after it was decreasing because the model suffered from overfitting.
![acc](https://user-images.githubusercontent.com/25064257/47728310-bec29c00-dc66-11e8-87cc-3b2ac9b2abb1.png)

The history of the learned paramaters (Weights and biases) were saved and the model with the highest validation accuracy was used to testing giving an accuracy of **37.05%**.<br />
![accr](https://user-images.githubusercontent.com/25064257/47728047-3d6b0980-dc66-11e8-83ea-75628db56531.PNG)

The correct classification rate for the 20 classes are shown below: 

![ccrn](https://user-images.githubusercontent.com/25064257/47728131-6ab7b780-dc66-11e8-92c5-2f873db6e477.PNG)

