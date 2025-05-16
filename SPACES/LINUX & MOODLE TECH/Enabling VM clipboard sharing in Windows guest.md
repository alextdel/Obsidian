1. Start the guest Windows VM.
2. Download and install the spice tools from https://www.spice-space.org/download.html (scroll to Windows binaries section)
3. In the Virt-Manager, add a Channel and set to spicevmc with the com.redhat.spice.0 selection
![[Pasted image 20240214063655.png |400]]
5. Restart the Windows VM - may need to restart Virt Manager if the Channel(spice) entry doesn't appear.
**References**
Basics are here - [[Set up clipboard sharing (enabling the spice user agent)]] -  this covers setp 1. and 2. above. I found the detail of 3. and 4. here - https://unix.stackexchange.com/a/517739.

---
**created:**  14 February 2024 at  06:23 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
