To check if a virtual network has been started and if autostart has been enabled, use
```shell
sudo virsh net-list --all
```
  
  The result should be something like 
 ```fallback
 Name      State      Autostart   Persistent
----------------------------------------------
 default   active       yes          yes
``` 

If the network requires enabling, disabling or setting to start automatically upon boot, see [[Enabling a default virtual network]]

---
**created:**  13 February 2024 at  10:13 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
