* To avoid pci device error
- use UEFI installation
- under install menu, press e.
- find line starting with linux and add 'pci=nomsi/' after quiet splash.
- press ctrl-x to resume install

* 1st boot window freeze issue
- press SHIFT when booting to enter grub boot menu mode
- select ubunut and press e
- find the line starting with linux then add 'modprobe.blacklist=nouveau' after quiet splash
- continue to boot
- install third-party nVidia driver

* avoid PCI nVidia error
- sudo nano /etc/default/grub
- update: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
- sudo update-grub
