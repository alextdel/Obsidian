**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #QEMU #VM #KVM #Libvert #Windows10
# QEMU - KVM - Creating a VM

**Created:**  10 February 2024 at  14:24 hours.
___
### Note:
This note shows installing a VM on a previously set up QEMU KVM system.
See [[QEMU and KVM setup]] to set up the system on Arch - tested on EndeavourOS. 

### Using virt-manager

VMs can be set up using the command line but *virt-manager* is the easier option. Look for *Virtual Machine Manager* in the applications menu.

### Using a physical SSD for a Win 10 VM

The installation of a VM can be made to existing partitions, virtual disks (effectively a file on an existing file system) or to a physical device, such as a spare SSD. 
The following shows how to install on a spare SSD.
1. Find the SSD identifier eg. /dev/sdb or /dev/nvme1n1
2. Use a partitioning tool like gnome-disk-utility to delete all existing partitions.
3. Start Virt Manager
4. In Virt Manager select 'New VM'
   ![[Pasted image 20240214170238.png]]
5. Select how you would like to install the operating system. In this case, we are using a Windows 10 ISO image. Click forward and choose the Windows 10 ISO. 

### Installing windows using the ISO

1. When the installation starts, you will select a disk drive as the installation location will be blank.
   ![[Pasted image 20240214164129.png |500]]
	- Select Load driver
	- Click on _Browse_ and expand the _CD Drive that contains the Virtio drivers - previously downloaded and set up as a CDROM source within the Virt-manager settings. Drivers can be downloaded from [here](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)  
	- Expand the __viostor__ folder, then __w10__ and then the CPU architecture (eg. __amd64__).
	- Once done, click _Next_ and it should install the driver.
	- 
	***Note*** - Some guides recommend installing the network drivers and the display drivers as well. This can be done by repeating the same process but select:
		- for the network: the __NetKVM__ folder and
		- for the video drivers: the __qxldod__ folder.

4. Set up a partition on the SSD to use as a passthrough drive for the VM.
   eg. /dev/nvme0n1p2 
2.  make sure the Windows10 iso is available on a fast SSD if possible.
3. 


**See also::**  [[QEMU and KVM setup]]

### Links to this note:
```query
"[[QEMU - KVM - Creating a VM]]"
```

