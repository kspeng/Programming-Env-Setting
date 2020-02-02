# CUDA8.0 + cuDNN6.0 [ref](http://www.pradeepadiga.me/blog/2017/03/22/installing-cuda-toolkit-8-0-on-ubuntu-16-04/)
## CUDA8.0
  - Download [Source](https://developer.nvidia.com/cuda-toolkit-archive)
  - Install
    ```   
    sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb
    sudo apt-get update
    sudo apt-get install cuda
    sudo nano /etc/environment
    => PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda-8.0/bin"
    sudo nano ~/.bashrc
    =>export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}$ 
    =>export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    source /etc/environment
    ```   
    * "broken packages" issue solution
    ```       
    sudo apt-get install aptitude
    sudo aptitude install cuda
    ```       
  - Check Cuda Version
    ```   
    nvcc --version
    > nvcc: NVIDIA (R) Cuda compiler driver
    > Copyright (c) 2005-2016 NVIDIA Corporation
    > Built on Tue_Jan_10_13:22:03_CST_2017
    > Cuda compilation tools, release 8.0, V8.0.61    
    ``` 

## Cudnn6 
  - Download [Source](https://developer.nvidia.com/rdp/cudnn-archive)
  - Install
    ```  
    tar zxvf cudnn-8.0-linux-x64-v6.0.tgz
    cd ~/src/cuda 
    sudo cp -P include/cudnn.h /usr/local/cuda-8.0/include
    sudo cp -P lib64/libcudnn* /usr/local/cuda-8.0/lib64
    sudo chmod a+r /usr/local/cuda-8.0/lib64/libcudnn*		
    ```      
  - Check cuDNN Version
    ```      
    cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
    > #define CUDNN_MAJOR 6 
    > #define CUDNN_MINOR 0 
    > #define CUDNN_PATCHLEVEL 21 
    > -- #define CUDNN_VERSION (CUDNN_MAJOR * 1000 + CUDNN_MINOR * 100 + CUDNN_PATCHLEVEL) 
    > #include "driver_types.h"
    ⇒ indicates that CuDNN version 6.0.21 is installed.
    ```      
# Anaconda Python 3.5 + Tensorflow-gpu 1.4
## Anaconda
  - Doenload [Anaconda 4.2.0](https://repo.continuum.io/archive/Anaconda3-4.2.0-Linux-x86_64.sh) (python3.5.2 default)
  - Install 
    ```
    bash Anaconda3-4.2.0-Linux-x86_64.sh
    source ~/.bashrc
    ```
## Add tqdm    
    ```    
    conda install -c conda-forge tqdm
    ```    
## Tensorflow-gpu 1.4    
  - Install tensorflow-gpu
    ```  
    easy_install -U pip
    pip3 install --upgrade tensorflow-gpu==1.4
    export LD_LIBRARY_PATH=LD_LIBRARY_PATH:/usr/local/cuda-8.0/lib64/
    ``` 
  - Install related packages
    ```
    pip install keras
    pip install opencv-python
    ```
## Add Anaconda build into sublime
  - Install Anaconda in sublime: Tools->Command Pallete->install package->Anaconda (enter)
  - Create a new sublime-build: Tools->Build System -> New Build System -> conda.sublime-build
    ```  
    {
      "cmd": ["/home/userid/anaconda3/bin/python3", "-u", "$file"],
      "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
      "selector": "source.python"
    }
    ```
  - Restart sublime
  - Diable sublime Anaconda linting
    Sublime > Preferences > Package Settings > Anaconda > Settings – User: 
    {"anaconda_linting": false}

## Resolve python3-tk issue
    sudo apt-get install python3-tk
    export MPLBACKEND=agg
 
## Resolve Intel MKL FATAL ERROR
    conda install nomkl numpy scipy scikit-learn numexpr
    conda remove mkl mkl-service

##  Check usage
    $ python
    >>> import tensorflow as tf
    >>> hello = tf.constant('Hello, World!')
    >>> sess = tf.Session()
    >>> print(sess.run(hello))
   
## Check installed python modules
    $ pip list

# Tensorflow API preparation
## Install Protoc
  - Download latest protuf [protoc-3.6.1-linux-x86_64.zip](https://github.com/protocolbuffers/protobuf/releases/download/v3.6.1/protoc-3.6.1-linux-x86_64.zip)
    ```
    sudo apt-get install protobuf-compiler 
    unzip protoc-3.6.1-linux-x86_64.zip -d protoc3
    sudo mv protoc3/bin/* /usr/local/bin/
    sudo mv protoc3/include/* /usr/local/include/
    source ~/.bashrc
    ```
### download Tensorflow research git:
    ```
    git clone https://github.com/tensorflow/models.git
    git checkout r1.8.0 # for specific version <= 1.8
    ```
    
    
## export Tensorflow slim
  - Edit ~/.bashrc and add:
    ```
    export PYTHONPATH=$PYTHONPATH:<path_to_tensorflow>/models/research/:<path_to_tensorflow>/models/research/slim
    ```



# Cuda Issue Debugging
## failed call to cuInit: CUDA_ERROR_UNKNOWN
  - Run following instruction
    ```    
    sudo apt-get install nvidia-modprobe
    ```    
  - And then reboot.
