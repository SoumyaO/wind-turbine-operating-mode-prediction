# Wind turbine operating mode prediciton
[Code](https://github.com/SoumyaO/wind-turbine-operating-mode-prediction/blob/main/OgotiSoumyaSMM768.ipynb) | [Data](https://github.com/SoumyaO/wind-turbine-operating-mode-prediction/tree/main/data)

## Description
This project involved predicting the operating mode of a wind turbine based on the time series data from two sensor readings. 

The dataset consisted of sensor readings and corresponding operating mode from 4,000 turbine runs. Each observation contained 5,000 sensor readings each from two sensors, one measuring pitch angle and the other generator torque, of a turbine over time. The operating modes were healthy, generator torque is faulty, pitch angle is faulty and both are faulty.

### Sequence Prediction
A sequence to vector prediction approach was used for this project as the output operating mode of the turbine is a scalar of fixed length. Multinomial logistic regression was used to establish a baseline. Several deep neural networks were evaluated and compared for sequence prediction.

- A simple dense network with two dense layers
- A network with Conv1D layers and MaxPooling
- A recurrent neural nework with Simple RNN layers
- A recurrent neural network with GRU layers
- A network with Conv1D and GRU layers

Further, the timeseries data was converted to images and 2D CNNs were applied on the images. This was done by implementing the paper "Convolutional neural network fault classification based on time series analysis for benchmark wind turbine machine", Rahimilarki R., Gao Z., Jin N., and Zhang A., Renewable Energy 2022. was implemented as part of this project.

This model was further improved by adding more CNN layers to capture the non-linearity better. The KerasTuner library was used to tune the hyperparameters. Batch Normalization and Dropout were added to prevent overfitting and a learning rate scheduler was also added.

A pre-trained MobileNetV2 trained on Imagenet weights, VGG-19 trained on Imagenet weights, were used for comparison.

Of these methods the model from the paper with additional CNN layers, fine tuning, batch normalization, dropout and learning rate scheduling performed the best with an accuracy of 87.3%. On the test dataset this model gave an accuracy of 87.1%.
