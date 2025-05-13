
A VM requires a virtual network in order to pass or receive traffic to/from other machines, including those on the internet.

For a VM that will act as a workstation, i.e not running a web or ftp server, enabling a default virtual network is sufficient.

To initialise a default network run the following: 
```shell
sudo virsh net-start default
```

To enable a default network to autostart at boot
```shell
sudo virsh net-autostart default
```

Check virtual network status with
```shell
sudo virsh net-list --all
```

The result should be something like 
 ```fallback
 Name      State      Autostart   Persistent
----------------------------------------------
 default   active       yes          yes
``` 

###  Enable Automatic Start (Optional)
If you want the network to start automatically when your system boots, enable *autostart* for the network:
```bash
sudo virsh net-autostart default
```
>***Note***
>Or `sudo virsh net-autostart <<network_name>>` if a different type of network, such as a bridge network, is to be used.

### Notes
1. If `sudo virsh net-start default` returns a message indicating the network has not started, it may be necessary to restart the libvirtd service. Use ... 
```shell
sudo systemctl restart libvirtd
```

2. If the VM is a server, a bridged virtual network will be needed. See [[Creating and enabling a bridge network]] for how to manage a bridged network.
4. Virtual default and bridged networks can be run at the same time.

---
**created:**  13 February 2024 at  10:00 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
