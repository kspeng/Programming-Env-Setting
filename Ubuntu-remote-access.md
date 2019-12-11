## Host 
* Setting
```
sudo apt-get install openssh-server  
```
* Checkup IP
  - Go to site(https://whatismyipaddress.com).
  - Get "My IP Address Is" of either IPv6 or IPv4.

## Client 
* Connect via terminal
```
ssh host-username@remote-pcs-IPv6
```

## Create Sudo User
* Add username
```
sudo adduser username
```
* Add user to sudo group
```
sudo usermod -aG sudo username
```
* Test sudo access
```
su - username
sudo ls -la /root
```
