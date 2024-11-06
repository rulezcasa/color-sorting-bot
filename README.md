
# A YOLO - HSV based color sorting algorithm

## Overview
This codebase implements a YOLOV8 architecture to accurately identify and sort objects based on their RGB values and HSV parameters. This project explores the development, implementation, and performance evaluation of the color
sorting system, demonstrating its potential to streamline production workflows, improve quality control, and enhance overall manufacturing efficiency. The final model was deployed and simulated in the webot environment for real-time analysis.


<img width="424" alt="Screenshot 2024-11-06 at 10 18 00 AM" src="https://github.com/user-attachments/assets/a041e3bc-22c5-45dd-9cf8-5e30a2008b0d">






# Directory Structure

```
project_root/
├── Dataset/cube-images
│   ├── test/   
│   ├── train/     
|   ├── data.yaml       
│   ├── README.dataset.txt   
│   └── README.roboflow.txt 
|     
├── Model weights/
│   └── best.pt
|
├── Notebook/
│   └── Colort-sorting.ipynb
│
└── Report/
    └── Report.pdf
```




## Dataset

The dataset comprises of 500 images of colored cubes sourced from https://universe.roboflow.com/jakub-slof/red-green-blue-cube-detection/dataset/2



| Split       | Percentage | Number of Images |
|-------------|------------|------------------|
| **Train Set** | 88%        | 438 images       |
| **Validation Set** | 8%      | 42 images       |
| **Test Set**  | 4%         | 19 images       |


The following preprocessing steps were applied to prepare the images for training:

- **Auto-Orient**: Corrected the orientation of all images based on EXIF data.
- **Resize**: Resized images to 640x640 pixels, stretching to fit the dimensions as needed.

Each training example undergoes several augmentations to improve model robustness. The output per training example is multiplied by a factor of 3 to enhance variability in the dataset.

| Augmentation | Description                                     |
|--------------|-------------------------------------------------|
| **Flip**     | Horizontal flipping applied to images           |
| **Blur**     | Gaussian blur with up to 2.5px                  |
| **Noise**    | Random noise applied to up to 5% of pixels      |
| **Cutout**   | Three random cutout boxes, each covering 10% of the image |

## Results

```
| Class       | Images | Instances | Box Precision | Recall | mAP@50  | mAP  |
|-------------|--------|-----------|---------------|--------|--------|-------|
| all         | 42     | 98        | 0.938         | 0.993  | 0.989  | 0.929 |
| blue cube   | 42     | 23        | 0.845         | 1.0    | 0.978  | 0.924 |
| green cube  | 42     | 37        | 0.968         | 1.0    | 0.995  | 0.943 |
| red cube    | 42     | 38        | 1.0           | 0.978  | 0.995  | 0.919 |
```

### Metric Descriptions

- **Images**: Number of images containing instances of each class.
- **Instances**: Total count of object instances per class across images.
- **Box Precision**: The accuracy of bounding boxes for each class.
- **Recall**: The model's ability to correctly detect instances of each class.
- **mAP@50**: Mean Average Precision at IoU threshold of 0.50, indicating detection quality.
- **mAP**: Mean Average Precision across multiple IoU thresholds, reflecting overall detection performance.
## Acknowledgements

**Funding:** H. Thangaraj contributed to this work while undertaking a project with the Department of Computer Science, Vellore Institute of Technology under Professor Rajarajeshwari for the Machine Learning coursework.

**Data Access Statement:** This study involves secondary analyses of an existing dataset, ackwowledged in the work.

