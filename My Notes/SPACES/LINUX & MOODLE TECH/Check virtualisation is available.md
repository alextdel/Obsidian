Most modern CPUs and kernels include virtualisation. To check the virtualisation is available and that BIOS settings have enabled the virtualisation on a CPU do the following:

1. Make sure virtualisation is available. The result should be > 0
```shell
# for endeavouros use
grep -E -c '(vmx|svm)' /proc/cpuinfo
# older version was
# egrep -c '(vmx|svm)' /proc/cpuinfo
# this may be seen in some guides
```
If the output = 0, go to bios settings and enable VT-x (Virtualization Technology Extension) for Intel processor (AMD-V for AMD processors).

---
**created:**  13 February 2024 at  08:07 hours.
**source file: [[QEMU and KVM setup]]
**See also::** {...}
**tags::** 
