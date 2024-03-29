# Disease Classification and Detection using Jetson Nano

## Overview
This project demonstrates how to use the NVIDIA Jetson Nano for disease classification and detection from CT scans and X-ray images using a deep learning model, specifically ResNet-152. It's designed to show the power of edge computing in medical diagnostics.

## Getting Started

### Prerequisites
Ensure you have the following hardware and software ready:
- NVIDIA Jetson Nano Developer Kit
    <img width="380" alt="Screenshot 2024-03-28 at 8 54 20 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/5b1104fe-cd6e-4c71-a3a6-f872785eb282">
- MicroSD card (64GB recommended)
    <img width="281" alt="Screenshot 2024-03-28 at 8 55 20 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/fdbc4281-4d44-4499-9a45-68ebef5829fc"> 
- 5V⎓3A power supply
- Monitor, Keyboard, Mouse
- Internet connection for the Jetson Nano
    <img width="269" alt="Screenshot 2024-03-28 at 8 55 44 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/7a4281f6-eb8b-4289-9096-cf6db34cd6f1">


### Hardware Setup
1. **Prepare your MicroSD Card**: Download and flash the Jetson Nano Developer Kit SD Card Image from NVIDIA's official website onto your MicroSD card.
2. **Assemble the Jetson Nano**: Insert the MicroSD card, connect your peripherals, and then connect the power supply to boot up.
    <img width="339" alt="Screenshot 2024-03-28 at 8 56 44 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/86e9c7a8-ffdd-4a75-8ce1-1faecd5d09e1">

3. **Initial Configuration**: Complete the setup wizard on the Jetson Nano to set up your account and internet connection.

### Software and Project Setup
1. **Update and Upgrade Jetson Nano**:
    ```sh
    sudo apt-get update
    sudo apt-get upgrade
    ```
2. **Install Dependencies**:
    ```sh
    sudo apt-get install python3-pip libopenblas-base libopenmpi-dev 
    pip3 install numpy matplotlib
    ```
3. **Install PyTorch and Torchvision**: Visit the PyTorch official website for the latest installation instructions suitable for Jetson Nano.
    <img width="340" alt="Screenshot 2024-03-28 at 8 56 56 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/dc890d2e-4577-4efa-943c-e01731ee6412">

4. **Prepare Your Dataset**: Place your CT scan and X-ray images in the `data` directory.

5. **Train Your Model**:
    ```sh
    python3 train.py --data_dir ./data --batch_size 4 --epochs 50
    ```
    <img width="515" alt="Screenshot 2024-03-28 at 8 58 26 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/79441303-7b17-4348-92a0-0da03b49e885">


### Running Inference
To perform inference with your trained model, use:
```sh
python3 inference.py --model_path ./models/resnet152_best.pth --image_path ./data/test/sample.jpg
```

### Accuracy of the model
As we have used Residual Neural Network (RESNET 152) in this project. The below graph is the accuracy of the model.
<img width="397" alt="Screenshot 2024-03-28 at 9 00 57 PM" src="https://github.com/NeerajNamani/Lung-Classification-and-Detection-Jetson-Nano-/assets/69526166/e743331e-3853-4fa6-8045-4ceaef9f12c0">


Thanks to @dusty-nv's Jetson Inference, 
```source = https://github.com/dusty-nv/jetson-inference```
