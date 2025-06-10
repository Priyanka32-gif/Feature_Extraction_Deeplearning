# 3D CNN Feature Extraction and Similarity Analysis 

This project demonstrates the conversion of a 2D pretrained DenseNet121 model into a 3D CNN for analyzing CT scan volumes of the leg. The primary goal is to extract feature vectors from anatomical regions (Tibia, Femur, and Background) and measure their similarity using cosine distance.

### Methodology

3D Conversion: A custom DenseNet3D class was developed to convert all Conv2d, BatchNorm2d, and Pooling layers into 3D counterparts.
Feature Hooks: Forward hooks were registered on the last, 3rd-last, and 5th-last Conv3D layers to capture intermediate feature maps.
Pooling: Each feature map was compressed using global average pooling to produce N-dimensional vectors.
Similarity Measurement: Cosine similarity was calculated between region pairs at each feature level: Tibia-Femur, Tibia-Background, and Femur-Background.

### Results


#### Tibia-Femur

0.9807 - Last layer

0.9252 - 3rd last layer

0.9464 - 5th last layer

##### Tibia-Background

0.8067 - last layer

0.7433 - 3rd last layer

0.6759 - 5th last layer

#### Femur-Background

0.8304 - last layer

0.7846 - 3rd last layer

0.6318 - 5th last layer

High similarity in Tibia-Femur pairs reflects anatomical proximity.

Background similarity is lower, particularly in shallower layers.

Deep features (last layer) generalize across regions, while shallow layers retain more specific information.

### Conclusion

The pipeline successfully evaluates feature similarity between anatomical regions using a 3D CNN. Such analysis has potential applications in automated bone structure assessment and model interpretability in medical imaging.

### Tools & Libraries

PyTorch, NumPy, Sci-kit Learn, Matplotlib