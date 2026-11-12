# Face Mask Detection using CNN

## Project Overview

This project implements a Convolutional Neural Network (CNN) to classify facial images into two categories:

- **With Mask:** Images of people wearing face masks.
- **Without Mask:** Images of people not wearing face masks.

The project explores CNN-based image classification and improves model performance through additional training and callback techniques.

## Dataset

**Source:** [Face Mask Dataset - Kaggle](https://www.kaggle.com/datasets/omkargurav/face-mask-dataset)

The dataset contains 7,553 images across two categories.

| Category | Number of Images |
|---|---:|
| With Mask | 3,725 |
| Without Mask | 3,828 |
| **Total** | **7,553** |

### Data Preprocessing

- Converted images into RGB format.
- Resized all images to 128 × 128 pixels.
- Converted images into NumPy arrays.
- Assigned numerical labels:
  - 0: Without Mask
  - 1: With Mask
- Normalized pixel values to the range of 0 to 1.

### Dataset Split

| Dataset | Images | Percentage |
|---|---:|---:|
| Training | 5,437 | 72% |
| Validation | 605 | 8% |
| Testing | 1,511 | 20% |

Stratified splitting was used to maintain class proportions across the datasets.

## Model Architecture

A CNN was developed using TensorFlow and Keras.

The architecture consists of:

1. Conv2D (32 filters, ReLU)
2. MaxPooling2D
3. Conv2D (64 filters, ReLU)
4. MaxPooling2D
5. GlobalAveragePooling2D
6. Dense (128 neurons, ReLU)
7. Dropout (0.5)
8. Dense (2 neurons, Softmax)

**Total Trainable Parameters:** 27,970

## Model Training and Improvement

Two training stages were performed:

- **Baseline CNN:** Trained for 10 epochs.
- **Improved CNN:** Continued training for 20 additional epochs using the existing model weights.

The improved training stage used:

- EarlyStopping
- ReduceLROnPlateau

These callbacks helped monitor validation performance and adjust training when necessary.

## Performance Evaluation

The baseline and improved models were evaluated using the same test dataset.

| Evaluation Metric | Baseline CNN | Improved CNN |
|---|---:|---:|
| Test Accuracy | 79.29% | **88.02%** |
| Test Loss | 0.4699 | **0.2996** |
| Macro Precision | 80% | **88%** |
| Macro Recall | 79% | **88%** |
| Macro F1-score | 79% | **88%** |

The improved CNN achieved an accuracy improvement of approximately **8.74 percentage points** over the baseline model.

### Improved Model: Classification Report

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Without Mask | 0.89 | 0.87 | 0.88 |
| With Mask | 0.87 | 0.89 | 0.88 |

## Custom Image Prediction

A simple predictive system was implemented to classify uploaded images.

Users can upload an image, and the trained model predicts whether the person is wearing a face mask.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Seaborn
- Pillow (PIL)
- OpenCV
- Scikit-learn
- TensorFlow
- Keras
- Google Colab


## Conclusion

This project demonstrates how CNNs can be applied to image classification tasks. By improving the training strategy and using callbacks, the model's test accuracy increased from 79.29% to 88.02%.

The project also provided practical experience with image preprocessing, CNN architecture design, model evaluation, and custom image prediction.
