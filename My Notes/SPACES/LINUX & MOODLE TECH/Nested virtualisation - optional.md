***Generally this is not required***

>***Note*** - nested virtualization might not be supported on all hardware configurations, and enabling it could impact performance.

a. **Enable nested virtualisation -** 

```shell
sudo modprobe -r kvm_intel
sudo modprobe kvm_intel nested=1
echo "options kvm-intel nested=1" | sudo tee /etc/modprobe.d/kvm-intel.conf
```

b. **Verify nested virtualisation**

```
systool -m kvm_intel -v | grep nested
cat /sys/module/kvm_intel/parameters/nested
```

---
**created:**  13 February 2024 at  10:15 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
