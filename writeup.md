#**Behavioral Cloning** 

##Writeup
The code I have been using for the Behavioral Cloning Project relies heavily on the code samples presented in the tutorial on the Udacity website. It can be found in the file model.ipynb.
I am using the images provided by udacity as well as the associated steering angle information from the driving_log file. I am reading the test images with opencv and then (as opencv reads images in BGR format) I am transforming them to RGB. By flipping the test images and inverting the steering angle for the corresponding image as well I am generating additional data to train my network. In order to increase memory efficiency I am using a generator function for this whole operation. This means that the set of training images is split into batches and only the currently needed batch is loaded in memory. The same procedure is applied for the validation data
For my network I am using the NVIDIA structure as it was presented in the udacity tutorial. This means that the network has the following layout:

| Layer                      |     Description                              | 
|:--------------------------:|:--------------------------------------------:| 
| Lambda                     | Normalize image pixel values to +/-0.5       | 
| Cropping 2D                | remove upper (not relevant) section of images| 
| 5xConv2D w. relu activ.    | extract features from image                  | 
| Flatten + 5xfully connected| 5 fully connected layers                     | 

The output of the network is then a prediction of the steering angle.

As loss function the mean square error between predicted and recorded steering angle is used. The network is trained with 'Adam' optimizer (for 3 epochs). After this the nework data is saved to the model.h5 file.
When I recorded the video the car was able to stay on track 1. I would certainly like to test the model with track 2 also but did not have the time so far. Sorry for the bad video quality - I had to run the simulation on a quite old laptop as the simulator would not run it on my PC in atonomous mode.

