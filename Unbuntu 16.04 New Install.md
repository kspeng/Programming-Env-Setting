## Brief
A note of new Ubuntu 16.04 LTS installaton

## Steps
1. Ubuntu ISO preparation
    - Official [Download](http://releases.ubuntu.com/16.04/)
    - Use [Rufus](https://rufus.akeo.ie/) to build a bootable U-disk

2. [Installation](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop-1604#0)    
    
3. Basic Office Requirements
    ```
    sudo apt-get update
    ```
    - GNOME Control Center
        ```
        sudo apt install gnome-control-center gnome-online-accounts
        ```
    - GNOME Shell
        ```    
        sudo apt install gnome gnome-shell
        ```
    - macbuntu
        ```
        udo add-apt-repository ppa:noobslab/macbuntu
        sudo apt-get update
        sudo apt-get install macbuntu-os-icons-lts-v7
        sudo apt-get install macbuntu-os-ithemes-lts-v7        
        ```        
    - Git
        ```
        sudo apt install git
        ```
    - IME: iBus Chewing # Traditional Chinese Input
        ```
        sudo apt-get install ibus-chewing
        ```        
    - Snipping tool: shutter
        ```
        sudo apt-get install shutter
        ```
    - Browser: [Chrome](https://www.google.com/intl/en-US/chrome/browser/)
    - PDF Reader: FoxitReader
        ```
        wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/2.x/2.1/en_us/FoxitReader2.1.0805_Server_x64_enu_Setup.run.tar.gz
        tar xzvf FoxitReader*.tar.gz
        sudo chmod a+x FoxitReader*.run
        sudo ./FoxitReader.*.run
        ```    
    - Image viewer: XnView
        ```    
        sudo apt-get install gdebi
        wget http://download.xnview.com/XnViewMP-linux-x64.deb
        sudo gdebi XnViewMP-linux-x64.deb
        ```        
    - Text editor: Sublime
        ```
        sudo rm /var/lib/apt/lists/lock
        sudo rm /var/cache/apt/archives/lock
        wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
        echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
        sudo apt-get update        
        sudo apt-get install sublime-text
        cp /usr/share/applications/sublime_text.desktop ~/.local/share/applications/sublime_text.desktop
        sudo sed -i 's/gedit/sublime_text/g' /etc/gnome/defaults.list
        ```        
    - Remote Client: [Teamviewer](https://community.teamviewer.com/t5/Knowledge-Base/How-to-install-TeamViewer-on-Ubuntu/ta-p/45)         
    - Cloud Drive: dropbox
        ```
        cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
        ~/.dropbox-dist/dropboxd
        ```        
    - Cloud Drive: refer to [Google Drive](https://www.omgubuntu.co.uk/2016/08/use-google-drive-ubuntu-16-04-linux-desktops)
    - Server terminal: putty
        ```        
        sudo apt install putty
        ```        
    - Package maintainer: yum
        ```        
        sudo apt-get install yum
        ```        
    - Install exFAT support
        ```         
        sudo apt install exfat-fuse exfat-utils
        ```        
    - Install Filezilla
        ```
        sudo apt install filezilla
        ```
    - Install [Mendeley](https://www.mendeley.com/repositories/ubuntu/stable/amd64/mendeleydesktop-latest)
        ```    
        sudo dpkg -i <path-to-downloaded-package>
        ```
    - Fix Windows Partition Mount Problem
        ```    
        sudo ntfsfix /dev/targetdisk
        ```    

