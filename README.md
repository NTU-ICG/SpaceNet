# SpaceDet
SpaceDet: A Large-scale Realistic Space-based Image Dataset and RSO Detection for Space Situational Awareness

> ❗ When using SpaceDet in your research, it is vital to cite both the SpaceDet dataset and the individual works that have contributed to your research. Accurate citation acknowledges the efforts and contributions of all researchers involved. For example, if your work involves a specific benchmark within SpaceDet, please include a citation for that benchmark apart from SpaceDet.

## Repository Overview

This repository provides the SpaceDet dataset, designed to advance research in Space Situational Awareness (SSA). SpaceDet offers realistic space-based images generated with accurate space orbit dynamics and a physical camera model, suitable for developing advanced SSA techniques. The dataset is split into three subsets: SpaceDet-100, SpaceDet-5000, and SpaceDet-full, catering to various image processing applications. This codebase is still under construction. Comments, issues, contributions, and collaborations are all welcomed!

## Data

SpaceDet provides a comprehensive and realistic space-based image dataset designed to advance research in Space Situational Awareness (SSA). The dataset includes high-resolution images of resident space objects (RSOs) captured from various orbits. Below are the available datasets and their respective download links:

**Access to the dataset is granted upon reasonable request.**  
To obtain download permission, please first submit an access application through the following form:  
👉 [(https://docs.google.com/forms/d/e/1FAIpQLSdR2FtSR2Xv3rbfTQZQuyKDcUdB9zfpiPJt0rtZywIeZkJxXg/viewform?usp=publish-editor)]

- **SpaceDet-100** [OneDrive](https://entuedu-my.sharepoint.com/:f:/g/personal/rangya001_e_ntu_edu_sg/IgA0Lbvbp-H_Q4nV-B5IhPzoAVzRg1cn425aDgHQrAtuJAk?e=oLg68Y): A subset containing 100 high-resolution images for quick experimentation and algorithm testing (dataset for only one camera).
- **SpaceDet-100-Rotated** [OneDrive](https://entuedu-my.sharepoint.com/:u:/g/personal/rangya001_e_ntu_edu_sg/IQDazo0P0FjxRqU5uKMgzfd-AQa55gNKTesCY63paXN7nw0?e=CHDHH6): The entire SpaceDet-100 dataset with all images randomly rotated by -30° to 30°, designed to test algorithm performance under rotational variations.
- **SpaceDet-5000** [OneDrive](https://entuedu-my.sharepoint.com/:u:/g/personal/rangya001_e_ntu_edu_sg/IQACa7YU-jBZTqLEtWXsHf6FAdWP7FxXET4Bju4Xg6263xg?e=CnKMxE): A larger subset with 5000 images providing a more extensive dataset for detailed analysis and model training (dataset for only one camera).
- **SpaceDet-full** [OneDrive](https://entuedu-my.sharepoint.com/:f:/g/personal/rangya001_e_ntu_edu_sg/IgAzWCyPGITOTqSyfLrxDSJ_AQxJEn1MlDvhbk642pTMYxk?e=tz9eso): The complete dataset including 781.5GB of images and 25.9MB of ground truth labels, designed for in-depth research and development of advanced SSA techniques (dataset for four cameras).

![image](https://github.com/NTU-ICG/SpaceDet/assets/19664995/3cfd91f1-f8cb-4ec8-9578-13d3638bee8a)
_Figure 1. Comparison of our SpaceDet images with [SPARK](https://cvi2.uni.lu/spark-2022-dataset/) images and real-life observed images. (a) SpaceDet images at timestamp 0 (four cameras from left top to right bottom), which show the realistic exposure with noise distribution; (b) A simulated spacecraft image from SPARK; (c) The real-life space observation image from the telescope and sensor network ([EGTN](https://exoanalytic.com/space-domain-awareness)). This demonstrates the realistic images in our SpaceDet dataset._


Our codebase accesses the datasets from ./data/ and benchmark codes from ./codes/ by default.

```plaintext
├── ...
├── assets                           
├── data
│   ├── SpaceDet-100                 # SpaceDet-100 demo dataset
│   │   ├── images                   # tiff image data
│   │   │   ├── *.tiff               # tiff format image files
│   │   │   └── *.csv                # csv format data files
│   │   ├── labels                   # class and bounding box information
│   │   │   └── *.txt                # txt files containing class and bounding box information
│   ├── SpaceDet-5000                # SpaceDet-5000 demo dataset
│   │   ├── images                   # tiff image data
│   │   │   ├── *.tiff               # tiff format image files
│   │   │   └── *.csv                # csv format data files
│   │   ├── labels                   # class and bounding box information
│   │   │   └── *.txt                # txt files containing class and bounding box information
│   ├── SpaceDet-full                # SpaceDet-full demo dataset
│   │   ├── images                   # tiff image data
│   │   │   ├── *.tiff               # tiff format image files
│   │   │   └── *.csv                # csv format data files
│   │   ├── labels                   # class and bounding box information
│   │   │   └── *.txt                # txt files containing class and bounding box information
├── codes
│   ├── scripts                      # data preprocessing and benchmark implementation code
│   │   └── *.py                     # Python script files
│   ├── ultralytics                  # modified YOLOv8 code (integrated with YOLOv10)
│   │   └── *.py                     # Python script files
├── croissant.json                   # croissant format metadata description
├── requirement.txt                  # Python libraries required to run the program
├── README.md                        # project introduction and usage instructions
├── ...

```

## Training and evaluation scripts

We provide training and evaluation scripts for all the methods we support in [scripts folder](./codes/scripts).

## Supported Object Detection Benchmarks

We compare the detection results of three object detection models: YOLOv5, YOLOv8, and YOLOv10. Each model is evaluated with five parameter sizes: n, s, m, l, and x.

- **YOLOv5** [GitHub](https://github.com/ultralytics/yolov5): YOLOv5, developed by Ultralytics, is a highly popular and efficient object detection model known for its speed and accuracy. It supports various tasks including object detection, instance segmentation, and more.

- **YOLOv8** [GitHub](https://github.com/ultralytics/ultralytics): YOLOv8 is an advanced version of YOLOv5, offering improved performance and new features. It continues to build on the strengths of its predecessor with enhanced detection capabilities and flexibility for different applications.

- **YOLOv10** [GitHub](https://github.com/THU-MIG/yolov10): YOLOv10, the latest in the YOLO series, introduces significant architectural improvements and optimizations. It is designed to deliver superior detection results with higher efficiency and accuracy compared to earlier versions.

## Supported Object Tracking Benchmarks
Two methods were tested: Bytetrack and BoT-SORT. These methods were adapted to improve their performance for space-based applications. For similarity calculations, Intersection over Union (IoU) and Euclidean distance were used. Additionally, BoT-SORT variants incorporated different global motion compensation algorithms and feature-based similarity calculations.

- **Bytetrack** [GitHub](https://github.com/ifzhang/ByteTrack): Bytetrack is a multiple object tracking method that can use either IoU similarity calculations or Euclidean distance similarity calculations for tracking accuracy.

- **BoT-SORT** [GitHub](https://github.com/NirAharon/BoT-SORT): BoT-SORT is a versatile multiple object tracking method that supports several similarity calculation options:
  - **IoU Similarity Calculation**
  - **Euclidean Distance Similarity Calculation**
  - **Feature Similarity Calculation**: This can be done using features from YOLO, HOG, or SIFT.

  Additionally, BoT-SORT can incorporate various global motion compensation (GMC) methods, including:
  - ECC (Enhanced Correlation Coefficient)
  - ORB (Oriented FAST and Rotated BRIEF)
  - SIFT (Scale-Invariant Feature Transform)
  - Sparse Optical Flow
 
## Get Started

### Installation

To install the SpaceDet project, you need to clone the repository and install the required dependencies manually. Follow the steps below:

1. **Clone the repository:**
    ```bash
    git clone https://github.com/NTU-ICG/SpaceDet.git
    cd SpaceDet
    ```
2. **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    
### Experimental Environment
Our experiments were conducted in the following environment:
- **Operating System:** Ubuntu 22.04
- **Conda Version:** 23.7.4
- **PyTorch Version:** 2.1.2
- **Python Version:** 3.11.7
All the required libraries are included in the `requirements.txt` file.

### Implementation
#### Setting Up the Environment
First, ensure that the `ultralytics` directory is added to the `PYTHONPATH`. This can be done by running the following command in your terminal:
```bash
export PYTHONPATH=$PYTHONPATH:/path/to/SpaceDet/codes/ultralytics
```
Replace `/path/to/SpaceDet/codes/ultralytics` with the actual path to the `ultralytics` directory.

#### Running the Code
To run the code, simply execute the following command:
```bash
python ./codes/scripts/main.py
```
All parameters are specified in `./ultralytics/cfg/default.yaml` and `./ultralytics/cfg/botsort.yaml`, including all adjustable benchmark methods and corresponding comments.
Ensure to update all path configurations in the default.yaml file to match your environment.

## License
Creative Commons Attribution 4.0 International

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.11609935.svg)](https://doi.org/10.5281/zenodo.11609935)

```
@software{zhang_2024_11609935,
  author       = {Zhang, Rangya and
                  Xiao, Jiaping and
                  Zhang, Yuhang and
                  Jia, Qianlei and
                  Bai, Lu and
                  Feroskhan, Mir},
  title        = {SpaceDet: A Large-scale Realistic Space-based 
                   Image Dataset for Space Situational Awareness},
  month        = jun,
  year         = 2024,
  publisher    = {Zenodo},
  version      = {1.0},
  doi          = {10.5281/zenodo.11609935},
  url          = {https://doi.org/10.5281/zenodo.11609935}
}
```






