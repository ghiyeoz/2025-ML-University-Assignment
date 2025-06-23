# MNIST Classification & Image Segmentation

## Overview
This project demonstrates two classical computer vision workflows:
- **MNIST Classification**: Handwritten digit classification using Support Vector Machine (SVM)
- **Image Segmentation**: Unsupervised segmentation on Berkeley benchmark images using k-means clustering

## Project Structure
```
MNIST-Segmentation-Task/
├── data/bsds500/          # Berkeley Segmentation Dataset images
│   ├── airplane.jpg       # BSDS airplane image
│   └── tiger_108073.jpg   # BSDS tiger image
├── notebooks/             # Jupyter notebooks
│   ├── mnist_svm.ipynb    # MNIST classification with SVM
│   └── kmeans_segmentation.ipynb  # Image segmentation with k-means
├── outputs/               # Generated visualizations
│   ├── confusion_matrix_svm.png
│   ├── tiger_image_segmentation_with_k=*.png
│   └── airplane_image_segmentation_with_k=*.png
└── requirements.txt       # Python dependencies
```

## Task 1: MNIST Classification with SVM

### Method
- **Dataset**: MNIST handwritten digits (70,000 grayscale images, 28×28 pixels)
- **Preprocessing**: Pixel-wise standardization
- **Model**: SVM with RBF kernel (C=10, gamma='scale')
- **Training/Test**: 10,000 images for training, 2,000 for testing

### Results
- **Accuracy**: 95% on test set
- **Strong Performance**: Digits 1, 0, and 6 (≥96% precision/recall)
- **Common Confusions**: 2↔8, 5↔3, 9↔4 (due to similar stroke shapes)
- See `outputs/confusion_matrix_svm.png` for detailed visualization

## Task 2: Image Segmentation with k-means

### Method
- **Images**: Tiger (108073.jpg) and Airplane (3096.jpg) from Berkeley dataset
- **Color Space**: RGB (uint8, 0-255)
- **Clustering**: k-means with k values of 2, 3, and 5
- **Visualization**: Pixels replaced with their cluster-center colors

### Results

#### Tiger Image
| k | Observation |
|---|-------------|
| 2 | Clear foreground/background separation - tiger + reeds vs. water |
| 3 | Tiger stripes begin forming their own cluster |
| 5 | Water splits into shallow/deep hues; some noise appears |

#### Airplane Image
| k | Observation |
|---|-------------|
| 2 | Plane + clouds vs. sky |
| 3 | Fuselage isolated; clouds distinct from blue sky |
| 5 | Small cloud wisps create extra clusters; slight over-segmentation |

## Conclusion
- **SVM** provides a strong baseline for MNIST classification (95% accuracy)
- **k-means** delivers intuitive image segmentations with increasing detail as k increases
- Higher k values highlight the trade-off between segmentation detail and noise

## Usage
```bash
# Set up environment
pip install -r requirements.txt

# Run notebooks
jupyter notebook notebooks/
```