# Flood Damage Assessment using Satellite Imagery

## Introduction

Flood damage assessment is a critical element in disaster recovery, especially in regions frequently affected by flooding. Leveraging advances in machine learning and computer vision, this project aims to assess flood damage accurately using satellite imagery. Our architecture includes a dedicated flood damage module that identifies buildings before and after floods, classifies damage levels, calculates affected areas, and generates an Earth Observation System (EOS) index to gauge flood severity. Through deep learning, this module supports timely and accurate flood damage assessments, enhancing the ability of authorities to respond and allocate resources effectively in flood-prone areas.

### Image Masks
![](https://github.com/Sanindu/EOS/blob/main/eosv1.gif)

### NDWI Generation

![](https://github.com/Sanindu/EOS/blob/main/eosv2.gif)

### Building Counting

![](https://github.com/Sanindu/EOS/blob/main/eosv3.gif)


## Background and Motivation

Satellite imagery plays a pivotal role in disaster response and recovery, providing essential data for quick assessment. However, traditional catastrophe mapping methods are often manual, slow, and prone to inaccuracy, especially during large-scale events like floods. Floods are among the most common and damaging natural disasters, impacting lives, infrastructure, and economies worldwide. This project seeks to automate flood damage assessment, reducing manual efforts, improving accuracy, and prioritising heavily impacted areas, thus facilitating more efficient rescue operations and resource distribution.

## Problem Statement

Natural disasters, particularly floods, are becoming increasingly frequent and severe. These events often result in extensive property damage, economic losses, and loss of life. Rapid and accurate damage estimation is essential to minimise impact and guide disaster response. The project addresses this need by using remote sensing data to estimate the extent and severity of flood-induced damages, an approach especially valuable in areas where manual assessment is difficult or dangerous.

## Aim and Objectives

This project aims to:
- Identify and quantify the total number of buildings and the extent of damage in a specific area affected by a flood.
- Determine the overall flooded area.
- Develop an index to assess flood severity based on the number of damaged buildings and the flooded area.

## Proposed Solution

This solution employs a neural network architecture compatible with multiresolution, multisensor, and multitemporal satellite imagery, performing tasks such as building footprint segmentation and damage classification. The system also calculates the flooded area, which, combined with other parameters, contributes to an index for flood severity assessment. This automated approach significantly reduces the time needed to create flood maps, supporting faster response times for disaster management teams.

## Approach

### Special Thanks
Special thanks for the guidance of Dr. Saminda Premaratne and Mr. Kunal Jethuri.

### Data Source and Preprocessing
- **Data**: Sentinel-2 satellite imagery (resolution: 0.5m per pixel) of Houston, Texas, during the 2017 Hurricane Harvey event.
- **Preprocessing**: 
  - Downscaled images to 1024x1024 resolution and resampled using bicubic interpolation.
  - Converted images and masks to a normalised float tensor format (0–1) for processing.
  - Divided images into smaller 512x512 patches for training.

### Model Architecture
- **Model**: U-Net architecture with a ResNet-34 backbone for efficient image segmentation.
- **Optimisation**: 
  - ADAM optimiser with a One Cycle Policy scheduler.
  - Transfer learning with pretrained ResNet encoder weights to enhance feature extraction.

### Flooded Area and Damage Assessment
1. **Building Detection**: Uses object detection algorithms and the Canny edge detection method to identify and count buildings in pre- and post-flood images, calculating a Damaged Building Ratio.
2. **Flooded Area Calculation**: Utilises Normalized Difference Water Index (NDWI) to distinguish between water and land in pre- and post-flood images. The difference in water bodies provides ground truth for flooded areas.
3. **Flood Map Creation**: Based on the ratio of flooded pixels to total pixels, generating an overall assessment of flood extent and severity.

## Summary
The project presents a robust method for assessing flood damage using satellite images and deep learning techniques. By automating flood assessment, this tool enhances disaster response speed and accuracy, aiding authorities in prioritising resources for heavily impacted areas.

## How to Run

1. Clone the repository.
    ```bash
    git clone https://github.com/yourusername/flood-damage-assessment.git
    cd ipynb_files
    ```
2. Open the Jupyter Notebook file.
    ```bash
    Final_Integration.ipynb
    ```
4. Follow the instructions in the notebook cells to:
   - Preprocess satellite images.
   - Train the model on preprocessed data.
   - Generate flood maps and calculate the flood severity index.
   
5. The notebook will display results such as flood maps and the severity index directly in the output cells, allowing you to visualise and interpret the findings step-by-step.


## License
MIT License

---

This project provides a valuable tool for flood disaster response, streamlining flood damage assessment to aid in efficient resource allocation during relief efforts.
