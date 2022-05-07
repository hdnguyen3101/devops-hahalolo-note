# 1. Cài đặt môi trường Nvidia, CUDA, CuDNN cho Linux

## 1.1. Cài đặt Nvida driver

### 1.1.1. Cài đặt Nvida-tool-kit

`apt install nvidia-cuda-toolkit`

### 1.1.2. Check version CUDA

`nvcc --version`

### 1.1.3. Verify that your GPU is CUDA-capable

`lspci | grep -i nvidia`

### 1.1.4. Verify Supported Version of Linux

`uname -m && cat /etc/*release`

### 1.1.5. Verify the System Has gcc Installed

`gcc --version`

### 1.1.6. Verify the System has the Correct Kernel Headers and Development Packages Installed

`uname -r`

#### 1.1.6.1. if not run this comamand (Ubuntu)

`sudo apt-get install linux-headers-$(uname -r)`

##### 1.1.6.1.1. Use the following command to uninstall a Toolkit runfile installation

`sudo /usr/local/cuda-X.Y/bin/cuda-uninstaller` _[thay cuda-X.Y thành version cuda tương ứng]_

##### 1.1.6.1.2. Use the following command to uninstall a Driver runfile installation

`sudo /usr/bin/nvidia-uninstall`

### 1.1.7. Cài đặt CUDA cho Linux Ubuntu 20.04 x86_64

#### 1.1.7.1. Download Installer CUDA for Linux Ubuntu 20.04 x86_64

```Linux Kernel Module
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin

sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.6.2/local_installers/cuda-repo-ubuntu2004-11-6-local_11.6.2-510.47.03-1_amd64.deb

sudo dpkg -i cuda-repo-ubuntu2004-11-6-local_11.6.2-510.47.03-1_amd64.deb

sudo apt-key add /var/cuda-repo-ubuntu2004-11-6-local/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda
```

### 1.1.8. Cài đặt CuDNN cho Linux Ubuntu 20.04 x86_64

#### 1.1.8.1. Download file cudnn-local-repo-ubuntu2004-8.3.3.40_1.0-1_amd64.deb về

#### 1.1.8.2. Enable the local repository

`sudo dpkg -i cudnn-local-repo-ubuntu2004-8.3.3.40_1.0-1_amd64.deb` _[Lưu ý thay đổi version cho phù hợp CUDA và CuDNN]_

#### 1.1.8.3. Import the CUDA GPG key

`sudo apt-key add /var/cudnn-local-repo-*/7fa2af80.pub`

#### 1.1.8.4. Refresh the repository metadata

`sudo apt-get update`

#### 1.1.8.5. Install the runtime library

`sudo apt-get install libcudnn8=8.8.3.3.40-1+cuda11.5`

#### 1.1.8.6. Install the developer library

`sudo apt-get install libcudnn8-dev=8.8.3.3.40-1+cuda11.5`

#### 1.1.8.7. Install the code samples and the cuDNN library documentation

`sudo apt-get install libcudnn8-samples=8.8.3.3.40-1+cuda11.5`

## 1.2. Option-network-install

### 1.2.1. Ubuntu Network Installation

These are the installation instructions for Ubuntu 18.04 and 20.04 users.
Procedure

#### 1.2.1.1. Enable the repository. The following commands enable the repository containing information about the appropriate cuDNN libraries online for Ubuntu 18.04 and 20.04

<Lưu ý thay đổi version và OS cho phù hợp CUDA và CuDNN>

```shell
wget https://developer.download.nvidia.com/compute/cuda/repos/${OS}/x86_64/cuda-${OS}.pin 

sudo mv cuda-${OS}.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/${OS}/x86_64/7fa2af80.pub
sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/${OS}/x86_64/ /"
sudo apt-get update
```

#### 1.2.1.2. Install the cuDNN library

```shell
sudo apt-get install libcudnn8=${cudnn_version}-1+${cuda_version}
sudo apt-get install libcudnn8-dev=${cudnn_version}-1+${cuda_version}
```

Where:

```shell
${cudnn_version} is 8.4.0.*
${cuda_version} is cuda10.2 or cuda11.6
```
