# Building a Project from Scratch on NVIDIA Jetson Nano 2GB Kit

This guide walks you through the process of building a project from scratch on a NVIDIA Jetson Nano 2GB Developer Kit. We will be setting up the environment, training models for CT-Scan and X-ray image analysis, and testing the trained models.

## Prerequisites

Before starting, ensure you have the NVIDIA Jetson Nano 2GB Developer Kit and all necessary accessories.

## Setup Steps

### 1. Gathering Accessories

- Acquire all necessary accessories from local sources.

### 2. Preparing for Setup

- Connect an SD card to your PC/Laptop.
- Download the [SD card Image](https://developer.nvidia.com/jetson-nano-2gb-sd-card-image) for the 2GB kit.
- Download and install the [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/SDCardFormatterv5_WinEN.zip).
- Perform a quick format of the SD card.
- Download, install, and launch [ETCHER](https://www.balena.io/etcher/).
- Flash the downloaded image to the SD card using ETCHER.

### 3. Setting up the Kit

- Insert the flashed SD card into the Jetson Nano kit.
- Attach all necessary accessories.
- Power on the kit and complete the initial setup steps as prompted.

### 4. Downloading Jetson Inference with Docker Container

- Open a terminal and clone the Jetson Inference repo: `git clone --recursive https://github.com/dusty-nv/jetson-inference`.
- Change to the `jetson-inference` directory: `cd jetson-inference`.
- Run the Docker container setup: `docker/run.sh`.

## Model Training

### 5. Downloading Datasets

- Download the CT-Scan dataset from [Kaggle](https://www.kaggle.com/mohamedhanyyy/chest-ctscan-images/download).
- Download the X-ray dataset from [Kaggle](https://www.kaggle.com/jtiptj/chest-xray-pneumoniacovid19tuberculosis/download).

### 6. Preparing Datasets

- Extract the datasets to `jetson-inference/python/training/classification/data/`, using appropriate subdirectories for each dataset.
- Create a `labels.txt` file in each dataset directory, listing the classes to be detected.

### 7. Training the Model

- Train the CT-Scan dataset model: `python3 train.py --model-dir=models/ct-scan --batch-size=4 --workers=1 --epochs=35 data/ct-scan`.
- Expect the training to take several hours.
- Export the trained model to ONNX format: `python3 onnx_export.py --model-dir=models/ct-scan`.
- Repeat the training and export process for the X-ray dataset.

## Testing the Models

### 8. Testing

- Test the CT-Scan model: `imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt (input location) (output location)`.
- For webcam-based detection: `imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt /dev/video0`.
- Repeat testing for the X-ray model.

### 9. Model Accuracy

- Review the model accuracy results and consider retraining for improvements.

## Resources

- Replace the `data` folder in `jetson-inference/python/training/classification/data` with the project's `data` folder.
- Replace the `models` folder in `jetson-inference/python/training/classification/models` with the project's `models` folder.

For additional assistance, contact namani.neeraj@gmail.com
