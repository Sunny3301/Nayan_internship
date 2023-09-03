# Blocking detection

Link to the [ETP Documentation](https://docs.google.com/document/d/1-od1qLMhCrUvekMuvJncEyzjsY7e7EgJN6wL2lsTYro/edit?usp=sharing)

[DATASET](https://drive.google.com/drive/folders/1P-_-SdnJbhrRAbWJT_s7XjKlaDasQf3f?usp=sharing)

## OBJECTIVES
* Develop and test an image-blocking detection system.
* Evaluate the system's accuracy in identifying blocked images.

## SCOPE
The project will include the following phases:

1. Data Collection and Preprocessing
2. Model Development
3. Model Testing and Validation
4. Performance Evaluation


## TEST PLAN
### Data Collection and Preprocessing:
#### _Objective:_ 
Collect and preprocess data for training and testing the detection model.

#### Data Collection:
Collect images from C3V2 platform and, YouTube dashcam videos.
Ensure the dataset includes a mix of blocked and unblocked images in separate folders.
Link to dataset: [Blocking](https://drive.google.com/drive/folders/1P-_-SdnJbhrRAbWJT_s7XjKlaDasQf3f?usp=sharing)

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/fcacd6e7-4cdb-46ee-91f6-9995823ee2c0)

#### Data Preprocessing:
Using TensorFlow’s Keras preprocessing framework made a data_set object that can access all the image data.
You are then using this object to resize the images to 180x180-sized images.
images pixel values vary in the [0-255] range, which is not ideal for a neural network. So we normalize the values to be in the [0-1] range by using ‘tf.keras.layers.Rescaling’.
Lastly, we split the data into the following: 80% of the dataset for training and 20% for validation.

### Model Development
#### _Objective:_
Develop a model for image-blocking detection.

* We used the most basic classification model [Keras Sequential] which uses ‘Relu’ as its activation function.
* We choose the ‘tf.keras.optimizers.Adam’ optimizer and ‘tf.keras.losses.SparseCategoricalCrossentropy’ loss function. To view training and validation accuracy for each training epoch, pass the metrics argument to ‘Model.compile’.
* You can check the model summary using the following line of code: model.summary()
* Since we didn't have a large enough dataset(only 254 images in total from both classes) we used data augmentation to increase the number of images in our dataset by adding random flips and random rotation, at run time.

    ![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/d7a605c8-8887-4922-ad5d-0c0b6040ec9f)

* Another technique we used alongside data augmentation was dropout regularization to the network. When you apply dropout to a layer, it randomly drops out (by setting the activation to zero) a number of output units from the layer during the training process. Dropout takes a fractional number as its input value, in the form such as 0.1, 0.2, 0.4, etc. This means dropping out 10%, 20%, or 40% of the output units randomly from the applied layer. This is only done to the augmented data.

*This image shows data augmentation.

### Model Testing and Validation
#### _Objective:_ Test and validate the trained model's performance.

To test the model's prediction quality we tested it against 8 test images:

Test1.png

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/26baa0f0-0010-414e-812f-148143254bbb)

Test2.png

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/beeed9b1-0137-4589-8ca3-2a4b5d7b7120)

Test3.png

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/24799c27-e3e9-427b-9abf-ce3dfcdfdbec)

Test5.png

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/dd89c6c1-5752-4e3c-9ff7-fef991029ec5)

Test8.png

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/695e4beb-130d-40f8-b7c7-07d7a5dbbf8c)

### Performance Evaluation
#### _Objective:_ 
Evaluate the performance of the image-blocking detection system.

The performance evaluation is done purely based on the time performance of the model its accuracy and loss results.
#### _Model structure:_

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/784fd302-0553-4bcc-b1d6-491738d61c76)

#### _Layers:_
<keras.engine.sequential.Sequential  <keras.layers.preprocessing.image_preprocessing.Rescaling
<keras.layers.convolutional.conv2d.Conv2D
<keras.layers.pooling.max_pooling2d.MaxPooling2D
<keras.layers.convolutional.conv2d.Conv2D
<keras.layers.pooling.max_pooling2d.MaxPooling2D
<keras.layers.convolutional.conv2d.Conv2D 
<keras.layers.pooling.max_pooling2d.MaxPooling2D
<keras.layers.regularization.dropout.Dropout 
<keras.layers.reshaping.flatten.Flatten 
<keras.layers.core.dense.Dense 
<keras.layers.core.dense.Dense 

##### _Weights:_
 Go through the blocking_detection_final.ipynb file to get the weights
 
## KEY RESULTS
     
![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/934e6253-59d7-474b-94fc-6eb465ac87a2)

The graph above shows training and validation accuracy/loss for our model in 15 epochs
using a Batch size of 32. The accuracy comes up to 89%.

Considering the simplicity of the model it performs 1000 predictions in 65 seconds. With every prediction averaging to 21ms/step.
These results are taken after the data augmentation and dropout technique.

#### _Confusion matrix:_

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/8b02c9fd-f222-4b77-8256-bcd641d097a4)



