GPU: Cuda8+cudnn6
https://medium.com/codezillas/step-by-step-guide-to-install-tensorflow-gpu-on-ubuntu-18-04-lts-6feceb0df5c0
c

Cudnn6
https://developer.nvidia.com/rdp/cudnn-archive
$ tar zxvf cudnn-8.0-linux-x64-v5.1.tgz
$ cd ~/src/cuda 
$ sudo cp -P include/cudnn.h /usr/local/cuda-8.0/include
$ sudo cp -P lib64/libcudnn* /usr/local/cuda-8.0/lib64
$ sudo chmod a+r /usr/local/cuda-8.0/lib64/libcudnn*		
Check Cuda Version
$ nvcc --version

⇒ CUDA8.0

$ nvidia-smi

Check cuDNN Version
$ cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
#define CUDNN_MAJOR 6 
#define CUDNN_MINOR 0 
#define CUDNN_PATCHLEVEL 21 
-- #define CUDNN_VERSION (CUDNN_MAJOR * 1000 + CUDNN_MINOR * 100 + CUDNN_PATCHLEVEL) 
#include "driver_types.h"
⇒ indicates that CuDNN version 6.0.21 is installed.


# Anaconda Python 3.5 + Tensorflow-gpu 1.4
## Anaconda
  - Doenload [Anaconda 4.2.0](https://repo.continuum.io/archive/Anaconda3-4.2.0-Linux-x86_64.sh) (python3.5.2 default)
  - Install 
    ```
    $ bash Anaconda3-4.2.0-Linux-x86_64.sh
    $ source ~/.bashrc
    ```
## Tensorflow-gpu 1.4    
  - Install tensorflow-gpu
    ```  
    $ easy_install -U pip
    $ pip3 install --upgrade tensorflow-gpu==1.4
    ``` 
  - Install related packages
    ```
    $ pip install keras
    $ sudo apt-get install python-opencv
    ```
## Resolve python3-tk issue
    ```
    $ sudo apt-get install python3-tk
    $ export MPLBACKEND=agg
    ```
##  Check usage
    ```
    $ python
    >>> import tensorflow as tf
    >>> hello = tf.constant('Hello, World!')
    >>> sess = tf.Session()
    >>> print(sess.run(hello))
    ```
