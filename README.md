# Plant-Disease-Classification-using-MobileNetV2
This project aims to classify plant diseases using MobileNetV2 model. With an ever-growing global population, ensuring a steady supply of crops is crucial. However, diseases can drastically reduce yields. Early and accurate disease detection can lead to better management and healthier crops

# Dataset
The data is sourced from the PlantVillage dataset( https://app.activeloop.ai/activeloop/plantvillage-with-augmentation). It consists of 55000+ images of various plant leaves, each labeled with the specific disease it has or labeled as healthy.the dataset can be online accessed by executing the following command:
import hub
ds = hub.load('hub://activeloop/plantvillage-with-augmentation')

# Number of classes: 39
Image resolution: Originally varying resolutions, but resized to 64x64 for the model.
# Model Architecture
The model is based on the MobileNetV2 architecture with some customizations to better suit the task:

# Base Model:
 MobileNetV2 pre-trained on ImageNet. This provides a robust feature extractor. Performed fine-tuning on this model for our specific dataset.
# Dropout Layer:
 Added to prevent overfitting. It drops out 50% of the neurons during training.
# Global Average Pooling Layer:
 Instead of flattening, used global average pooling. This reduces the spatial dimensions without adding any parameters, and often 
 results in a model that's more robust.
# Prediction Layer:
 A dense layer with 39 units (one for each class) and a softmax activation. This provides class probabilities for each of the diseases (and 
 healthy class).
# Challenges Faced
# Class Imbalance:
 Like many real-world datasets, some diseases had many more samples than others. This can bias the model; had to consider strategies like 
 augmentation or weighting the loss function to handle this.
# Data Augmentation:
 To improve the model's robustness and generalize better, data augmentation strategies were employed. This also helps increase the effective size 
 of the dataset.
# Batch Processing: 
 Due to the varying resolutions of the original images, batch processing was implemented to resize images in chunks and save computational 
 resources.
 Also implemented a gradio app for interfacing the model.

