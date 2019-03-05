 ## Docker Installation
 
 A quick script of Docker installation for Ubuntu-16.04 [Reference](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
 
 ```
    sudo apt-get update
    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common -y
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install docker-ce -y
    docker -v
    sudo docker run hello-world
    
```
