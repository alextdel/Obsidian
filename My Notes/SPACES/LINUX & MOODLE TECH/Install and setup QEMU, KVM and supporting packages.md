Some guides suggest this is sufficient:

<font color="yellow">DONT USE THIS </font>
```shell
sudo pacman -S qemu virt-manager virt-viewer edk2-ovmf dnsmasq bridge-utils libguestfs ebtables vde2 openbsd-netcat 
```

I found that the selection of virtio drivers was not possible unless the qemu-desktop or qemu-full was loaded. Google's Gemini AI suggests that qemu-full is overkill and that the -desktop version of qemu's packages is sufficient.

<font color="yellow">USE THIS :) </font>
```shell
sudo pacman -S qemu-desktop virt-manager libvirt qemu-agent-installer edk2-ovmf dnsmasq vde2 bridge-utils openbsd-netcat iptables-nft
```

>***Note*** - qemu-full = qemu + the other packages listed above + some other packages for other file systems.
>***Note*** - `swtpm` package can be added if Windows 11 is going to be used as it is an emulator of the TPM required by Win11

---
#### Packages included in the above list:
1. `qemu or qemu-desktop`: The QEMU emulator suite, providing a wide range of features and functionalities for virtualization and emulation. qemu-desktop seems optimal from my testing. `qemu-full` seems overkill.
2.  `virt-manager`: A graphical user interface for managing virtual machines, providing tools for creating, configuring, and monitoring VMs.
3. `virt-viewer`: A lightweight interface for interacting with graphical displays of virtual machines, allowing for remote display access.
4.  `edk2-ovmf`: UEFI firmware for QEMU, enabling support for UEFI booting in virtual machines.
5.  `dnsmasq`: A DHCP and DNS server, useful for providing network services to virtual machines.
6. `bridge-utils`: Utilities for configuring Ethernet bridging, facilitating network connectivity for virtual machines.
7. `libguestfs`: Tools for accessing and modifying guest disk images, allowing for manipulation of VM disk images.
8. `ebtables`: A tool for configuring Ethernet frame filtering rules, useful for network traffic control in virtualized environments.    
9. `vde2`: Virtual Distributed Ethernet for creating virtual networks, providing networking capabilities for virtual machines.    
10. `openbsd-netcat`: Netcat networking utility, useful for network communication tasks in virtualized environments.{{content}}

---
**created:**  13 February 2024 at  08:14 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
