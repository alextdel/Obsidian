 Check the host is correctly configured to run all libvirt hypervisor drivers
   ```shell
sudo virt-host-validate qemu
```
   All should show PASS.
   
   Likely error messages include:
   1. <font color="red"> QEMU: Checking if IOMMU is enabled by kernel      : WARN (IOMMU appears to be disabled in kernel. Add intel_iommu=on to kernel cmdline arguments)
	</font>
**Meaning**: Your Intel processor only supports the VT-x (vmx) feature and not VT-d. 
VT-d is used to implement a PCIe Pass-through which enables VMs direct access to specific I/O devices such as graphics cards, network adapters, and storage controllers.

 To enable VT-d, open the /etc/default/grub file and add the following
  ```shell
  #### For Intel CPU
  $ sudo nano /etc/default/grub
  ```
	 
then add to the file at the end of the following line ...	  
```bash
...
GRUB_CMDLINE_LINUX="... intel_iommu=on iommu=pt"
...
```
  then regenerate the grub config file 

*eg.* for Arch-based distros use:
```shell
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

<font color="magenta">Now REBOOT</font> 

Check again with the `sudo virt-host-validate qemu` command.
2. <font color="orange">QEMU: Checking for secure guest support       : WARN (Unknown if this platform has Secure Guest support)</font>
**Meaning**: Enable AMD Secure Encrypted Virtualization (SEV) support.
***NOTE-*** If you have an Intel CPU, you can safely ignore this warning. This applies to AMD CPUs.

---
**created:**  13 February 2024 at  09:56 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
