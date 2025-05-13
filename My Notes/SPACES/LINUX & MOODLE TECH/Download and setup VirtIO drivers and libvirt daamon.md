For Windows Guests

```shell
$ wget https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/virtio-win.iso
```

This ISO will contain all the drivers required. It needs to be connected to a CDROM device.
### Enable and start libvirt daemon
The following is for the *modular* option which is more modern. The monolithic version is being removed from some distros.

>**As of 14 Feb 2024** - _EndeavourOS_ seems to use only the *monolithic* libvirt daemon. While this is the case use the commands in ***2.*** below.

***1.*** 
	- for Fedora, Rocky, Arch-based etc.
```shell
for drv in qemu interface network nodedev nwfilter secret storage; do \
    sudo systemctl enable virt${drv}d.service; \
    sudo systemctl enable virt${drv}d{,-ro,-admin}.socket; \
done
```
<font color="magenta">*Now REBOOT*</font>

---
***2.***
-  ***Note*** for the monolithic (older method) the following can be used - both work but the above is more efficient.
```shell
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
```

---
**created:**  13 February 2024 at  08:15 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
