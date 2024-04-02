# Circle Detection

Utilizing a Convolutional Neural Network (CNN) model to accurately detect the location of the circle center and radius, achieving an impressive accuracy of **99.85%**.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Dawson-ma/Circle-Detection/)

## Quick Overview

### Model Architecture

- **ResNet18**  
  ![ResNet18 Architecture](./Images/ResNet18_Architecture.png)  
  [Source](https://doi.org/10.1007/s10916-019-1475-2)

- **Custom CNN**  
  ![CNN Architecture](./Images/CNN_Architecture.png)

**Input:**
- ResNet18: 3-dimensional grayscale image
- Custom CNN: 1-dimensional grayscale image

**Output:**
- x: row of the circle center
- y: column of the circle center
- r: radius of the circle

## Getting Started

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Dawson-ma/Circle-Detection/)

### Training

For training purposes, utilize `CircleDetection_train.ipynb`.

### Test

For testing purposes, utilize `CircleDetection_test.ipynb`.

### After Opening Colab

1. In Colab, select the runtime type as Python and GPU.  
   (Colab > Runtime > Change runtime type)
2. Specify the image and model variables in Part 0
3. Run the entire Python code
4. The code will execute...
5. Training and testing results will be displayed at the bottom

#### Troubleshooting

If the model parameter file download fails, please download the model parameter file (e.g., `model_resnet18.pt`) from GitHub and upload it to Colab.  
(Colab left bar > Files > Upload to session storage)

## Analysis

| Model                         | ResNet18 | Custom CNN |
| ----------------------------- | -------- | ---------- |
| Parameters                    | 11M      | 750K       |
| Mean IoU (Noise_LV=0.5)       | 98.79%   | 95.47%     |
| Accuracy (IoU threshold=0.8)  | 99.85%   | 95.55%     |
| Accuracy (IoU threshold=0.9)  | 98.75%   | 86.95%     |
| Accuracy (IoU threshold=0.95) | 94.60%   | 73.60%     |

The ResNet18 model consistently outperforms the Custom CNN across all metrics, demonstrating higher Mean IoU and accuracy. However, ResNet18 comes with a larger number of parameters and longer training and inference times. It is suitable for scenarios requiring precise predictions with high computational resources.

Conversely, the Custom CNN exhibits lower accuracy but with significantly fewer parameters and faster training and inference times. It is suitable for situations where rough predictions suffice and computational resources are limited. For applications demanding higher accuracy, a more complex Custom CNN architecture may be warranted.

In summary, the choice between ResNet18 and Custom CNN depends on the specific requirements of the application, balancing accuracy, computational resources, and inference speed.
