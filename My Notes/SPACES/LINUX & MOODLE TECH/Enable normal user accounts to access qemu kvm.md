The following will prevent a user having to enter sudo each time KVM is used or otherwise prevent permission related restrictions.
### Set up the config file

1. Edit the *libvertd.conf* file

```shell
sudo nano /etc/libvirt/libvirtd.conf
```

2. enter the following
```bash
unix_sock_group = "libvirt"
unix_sock_ro_perms = "0777"
unix_sock_rw_perms = "0770"
```

3. Save and close the file (for *nano* `Ctrl+o`, `Enter`, `Ctrl+x`)
### Add current user to required groups
#### Basic settings for kvm and libvirt groups

```shell
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER
newgrp libvirt
```
> ***Note***
> `newgrp libvirt` switches the primary group of the current shell session to `libvirt` - this gives user access immediately to the permissions granted to the 'libvert' group without needing to log out and back in.

#### Extended settings for kvm, libvirt and other groups required for disk and I/O device passthrough:

```shell
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER
sudo usermod -aG libvirt-qemu $USER
sudo usermod -aG input $USER
sudo usermod -aG disk $USER
newgrp libvirt
```
***Note*** 
To check the groups to which you are belong use the command `groups $USER`
An alternative to $USER is $(whoamI)

---
**created:**  13 February 2024 at  10:14 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
