**up::** [[SERVER AND WEB ADMIN MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #VirtualBox #shared #Linux #VM #Bitnami 

# Access VirtualBox Shared Directory

**Created:**  13 December 2022 at  12:27 hours.

___
### Note:

### Set up a shared directory within VirtualBox for a Linux Bitnami guest VM

1. Add a CDROM to the VM through settings
2. Mount the Guest Additions ISO which is in the `C:\Program files\Oracle\VirtualBox` directory
	1. Alternatively mount the Guest Additions ISO from the Devices menu in the VMs menu bar
3. Follow this set of instructions from ... https://www.virtualbox.org/manual/ch04.html

```
#### 4.2.2.1. Installing the Linux Guest Additions

The Oracle VM VirtualBox Guest Additions for Linux are provided on the same virtual CD-ROM file as the Guest Additions for Windows. See [Section 4.2.1.1, “Installing the Windows Guest Additions”](https://www.virtualbox.org/manual/ch04.html#mountingadditionsiso "4.2.1.1. Installing the Windows Guest Additions"). They also come with an installation program that guides you through the setup process. However, due to the significant differences between Linux distributions, installation may be slightly more complex when compared to Windows.

Installation generally involves the following steps:

1.  Before installing the Guest Additions, you prepare your guest system for building external kernel modules. This works as described in [Section 2.3.2, “The Oracle VM VirtualBox Kernel Modules”](https://www.virtualbox.org/manual/ch02.html#externalkernelmodules "2.3.2. The Oracle VM VirtualBox Kernel Modules"), except that this step must be performed in your Linux _guest_ instead of on a Linux host system.
    
    If you suspect that something has gone wrong, check that your guest is set up correctly and run the following command as root:
    
    rcvboxadd setup
    
2.  Insert the `VBoxGuestAdditions.iso` CD file into your Linux guest's virtual CD-ROM drive, as described for a Windows guest in [Section 4.2.1.1, “Installing the Windows Guest Additions”](https://www.virtualbox.org/manual/ch04.html#mountingadditionsiso "4.2.1.1. Installing the Windows Guest Additions").
    
3.  Change to the directory where your CD-ROM drive is mounted and run the following command as root:
    
    sh ./VBoxLinuxAdditions.run
``

**See also::** 

### Links to this note:
```query
"[[Access VirtualBox Shared Directory]]"
```

4. Reboot the guest server.

###  What to do if the Shared folder is inaccessible due to permissions

follow these instructions ... https://dev.to/rahedmir/virtualbox-cannot-access-shared-folder-items-permission-denied-fixed-59mi



