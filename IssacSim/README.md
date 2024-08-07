# Environment Setup
## 0. Perform Environment
 - Intel(R) Core(TM) i7-9700KF CPU @ 3.60GHz
 - NVIDIA GeForce RTX 2080 Ti
 - RAM 32GB
 - SSD 512GB

 - Ubuntu 22.04

## 1. Setting on Ubuntu
### Install Nvidia Driver
https://www.nvidia.com/download/index.aspx

- 기존 Nvidia Driver와 충돌을 막기위해 Nouveau 비활성화
```
$ sudo apt-get update
$ sudo apt-get remove nvidia* && sudo apt autoremove 
$ sudo apt-get install dkms build-essential linux-headers-generic
$ sudo gedit /etc/modprobe.d/blacklist.conf
```
```
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
```
```
$ sudo update-initramfs -u
$ sudo apt install nvidia-driver-550
$ sudo reboot
$ nvidia-smi
```

### Install Cuda
- run 파일을 다운받아 실행
```
$ wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
$ sudo sh cuda_11.8.0_520.61.05_linux.run
 -> Continue
 -> [ ] Driver
$ gedit ~/.bashrc
 export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
 export PATH=/usr/local/cuda/bin:$PATH
$ source ~/.bashrc
$ nvcc --version
```

### Install Python
- IssacSim required Python3.10
- Using Anaconda
```install python3.10
$ wget https://repo.anaconda.com/archive/Anaconda3-2022.10-Linux-x86_64.sh
$ bash Anaconda3-2022.10-Linux-x86_64.sh
 --> yes
 --> yes
$ source ~/.bashrc
$ conda create -n isaac-sim python=3.10

# activate virtual environment
$ conda activate isaac-sim 

# deactivate virtual environment
$ conda deactivate
```

- python package manage
```
# install python package
$ pip install {package_name}

# remove python package
$ pip uninstall {package_name}
```

### Install VSCode
`$ sudo apt install ./{vscode/deb/file/name}`

### Install ROS
- see the ROS2 Humble install guide
[https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html]

## 2. Install Issacsim  
[https://www.nvidia.com/en-us/omniverse/download/]

![image](https://github.com/user-attachments/assets/04de2514-a3d0-4e5d-8a93-6f5e5d5eed0e)

![image](https://github.com/user-attachments/assets/d1c44564-2c9c-44a5-878b-78622d521b63)

```
$ sudo add-apt-repository universe
$ sudo apt install libfuse2
$ sudo chmod +x omniver~~~~
$ ./omniverse~~~
```

- EXCHANGE -> OMNIVERSE CACHE download
- EXCHANGE -> ISAAC SIM download
- NUCLEUS -> create local necleus service 

## 3. Test Example Code
- install python & python extension pack
- `Ctrl`+`Shift`+`P`를 눌러 `Python: Select Interpreter` 선택
- Anaconda에 있는 python3.10 선택
- isaac-sim-2023.1.1/standalone_examples/api/omni.isaac.franka/pick_place.py 파일을 열고 `F5`로 실행

## REFERENCES
[https://github.com/gist-ailab/AILAB-summer-school]
