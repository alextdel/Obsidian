For a VM that will act a web or ftp server, the default network type is not sufficient and enabling a bridged virtual network is required.

In this example a bridged virtual network will be created with the name *br10* using the settings in an XML file called *br10.xml*
## Create the settings for the bridge network.

1. Set up a config XML file *\<network-name\>.xml*
```shell
sudo nano br10.xml
```
 
2. Enter the following configuration.
```xml
<network>
  <name>br10</name>
  <forward mode='nat'>
    <nat>
      <port start='1024' end='65535'/>
    </nat>
  </forward>
  <bridge name='br10' stp='on' delay='0'/>
  <ip address='192.168.30.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.30.50' end='192.168.30.200'/>
    </dhcp>
  </ip>
</network>
```

3. **Save the file in a convenient place.** The XML configuration file can be saved in any location on your system. However, it's common to save these files in a directory dedicated to libvirt configurations. A typical location for such files could be `/etc/libvirt/qemu/networks/`. This can be done by using `sudo mv <filename>` after the file has been saved or by setting up the file using `sudo nano /etc/libvirt/qemu/networks/br10.xml` prior to typing the XML code shown above.
	   ***check the file permissions are correct for the xml file.***
	   
## Define the Network

After saving the XML file, you need to define the network using the `virsh net-define` command. 
```bash
sudo virsh net-define /path/to/br10.xml
```
   
   Replace `/path/to/br10.xml` with the actual path where you saved the `br10.xml` file.

## Enabling a bridge network
This is similar to enabling a default network

Once you've defined the network, you can start it using:
```bash
sudo virsh net-start br10
```
This command will start the network defined in the XML configuration file.
### Notes
1. If `sudo virsh net-start br10` returns a message indicating the network has not started, it may be necessary to restart the libvirtd service. Use ... 
```shell
sudo systemctl restart libvirtd
```
2. If the VM is not a server, the default virtual network can be used. See [[Enabling a default virtual network]] for how to start a default network
3. Both the default and bridged network can be run at the same time.
---
**created:**  13 February 2024 at  10:00 hours.
**source file: [[QEMU and KVM setup]]
**See also::** 
**tags::** 

---
