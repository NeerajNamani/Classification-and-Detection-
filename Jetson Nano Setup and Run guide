# Running a Pre-Built Project on NVIDIA Jetson Nano 2GB Kit

This guide outlines the steps to run a pre-built project on a NVIDIA Jetson Nano 2GB Developer Kit, including setting up the environment, assembling the kit, and executing the project.

## Prerequisites

Ensure you have all necessary components, including the 2GB Developer Kit, and have access to a PC or Laptop for initial setup.

## 1. Prepare the SD Card

1. Insert the SD card into your PC or Laptop.
2. Download the [Jetson Nano 2GB SD Card Image](https://developer.nvidia.com/jetson-nano-2gb-sd-card-image).
3. Download and install the [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/SDCardFormatterv5_WinEN.zip).
4. Perform a quick format of the SD card using the SD Card Formatter.
5. Download, install, and launch [Balena Etcher](https://www.balena.io/etcher/).
6. In Etcher, select the downloaded SD card image, choose the formatted SD card as the target, and start the flashing process. This may take over 10 minutes.

## 2. Assemble the Kit

1. After flashing, insert the SD card into the Jetson Nano kit.
2. Connect the accessories (keyboard, mouse, monitor, etc.) to the appropriate slots on the kit as illustrated in the provided images.
3. Power on the kit and wait for it to boot.
4. Follow the on-screen instructions to complete the initial setup, including accepting the EULA, selecting language, timezone, creating a user, configuring network, and setting up the APP partition and swap file.

## 3. Setting Up the Environment

1. Upon completion of the setup, you'll be greeted with the welcome screen.
2. Open a terminal and clone the Jetson Inference repository using the command:
```sh
git clone --recursive https://github.com/dusty-nv/jetson-inference
```
3. Change to the `jetson-inference` directory:
```sh
cd jetson-inference
```
4. Run the Docker container setup script. This will prompt for your password (input won't be visible) and may take some time during the first run. Follow the prompts to download default models:
```sh
docker/run.sh
```

## Running the Project

1. Download the `Project.rar` file from [Google Drive](https://drive.google.com/file/d/1PgXG13vUNIofIlw480FAM_Y8ybLxdo66/view?usp=sharing) and extract it. You will find `data` & `Models` folders.
2. Replace the `data` and `Models` folders in the `jetson-inference/python/training/classification/` directory with the ones from the extracted project.
3. To test the cancer detection model, use the command:
```sh
imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt data/Project/Test01/Input/mix data/Project/Test01/Output
```
4. For testing the X-ray model, execute:
```sh
imagenet --model=models/xray/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/xray/labels.txt data/Project/Test02/Input/mix data/Project/Test02/Output
```

### Live Detection

For live detection using the camera, replace the input path with `/dev/video0` in the commands for both cancer and X-ray models as shown below.

- Cancer Model:
```sh
imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt /dev/video0
```
- X-Ray Model:
```sh
imagenet --model=models/xray/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/xray/labels.txt /dev/video0
```
