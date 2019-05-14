This tutorial is based on [Reference](https://www.tutorialkart.com/apache-spark/install-latest-apache-spark-on-ubuntu-16/)

0. Install [anaconda python 3.5 version](https://github.com/kspeng/Programming-Env-Setting/blob/master/Cuda%208.0%2BcuDNN6.0%2BTensorflow-GPU%2BComputer-Vision%2BAnaconda_python3.5.md#anaconda)

1. Prepare Java
  - Download [Java SE 8u212 linux x64](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
  - run following script
  ```
  tar -xvf jdk-8u212-linux-x64.tar.gz
  sudo mkdir /usr/lib/jvm
  sudo mv ./jdk1.8.0_212 /usr/lib/jvm/jdk1.8.0_212
  sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0_212/bin/java" 1
  sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0_212/bin/javac" 1
  sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.8.0_212/bin/javaws" 1
  sudo chmod a+x /usr/bin/java
  sudo chmod a+x /usr/bin/javac
  sudo chmod a+x /usr/bin/javaws
  ```
  
2. Install Spark
  - Download [spark-2.3.3-bin-hadoop2.7.tgz](http://spark.apache.org/downloads.html)
  - Unzip and move spark to /usr/lib/
  ```
  tar xzvf spark-2.3.3-bin-hadoop2.7.tgz
  sudo mv spark-2.3.3-bin-hadoop2.7 spark 
  sudo mv spark/ /usr/lib/
  ```
  - Add Path
  ```
  sudo&nbsp;nano ~/.bashrc
  ```
  And add following lines at the end of ~/.bashrc file.
  ```
  export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_212/jre
  export SPARK_HOME=/usr/lib/spark/bin
  export PATH=$PATH:SPARK_HOME
  ```
  - Verify spark
  Close all terminal and open a new one
  ```
  pyspark
  ```
  ```
  Python 3.5.2 |Anaconda custom (64-bit)| (default, Jul  2 2016, 17:53:06) 
  [GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
  Type "help", "copyright", "credits" or "license" for more information.
  2019-05-13 21:30:39 WARN  Utils:66 - Your hostname, kuo-5520 resolves to a loopback address: 127.0.1.1; using 192.168.0.115 instead (on interface wlp2s0)
  2019-05-13 21:30:39 WARN  Utils:66 - Set SPARK_LOCAL_IP if you need to bind to another address
  2019-05-13 21:30:40 WARN  NativeCodeLoader:62 - Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
  Setting default log level to "WARN".
  To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
  Welcome to
        ____              __
       / __/__  ___ _____/ /__
      _\ \/ _ \/ _ `/ __/  '_/
     /__ / .__/\_,_/_/ /_/\_\   version 2.3.3
        /_/

  Using Python version 3.5.2 (default, Jul  2 2016 17:53:06)
  SparkSession available as 'spark'.
  >>> 
  ```
