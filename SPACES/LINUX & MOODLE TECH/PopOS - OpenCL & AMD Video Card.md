**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #OpenCL #AMD #PopOS #darktable 
# PopOS - OpenCL & AMD Video Card

**Created:**  18 February 2024 at  16:05 hours.
___
### Note:
I tried a few different ways and the following worked - 
The following version was found [here](https://www.reddit.com/r/pop_os/comments/rjdfbq/my_amdgpupro_success_story_on_pop_os_2110_opencl/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button) . Tested on PopOS based on Ubuntu 22.04 (LTS)

---
A Ubuntu 22.04 version of the process can be found [here](https://support.zivid.com/en/latest/getting-started/software-installation/gpu/install-opencl-drivers-ubuntu.html) - but it is referring to Ubuntu 22.04 rather than the PopOS derivative. The instructions for 'pretending' to be ubuntu when within PopOS can be found in this ([[PopOS - OpenCL & AMD Video Card#Modify OS Identification|section below]])

---
# Setting Up AMDGPU-PRO for OpenCL on Pop!_OS 21.10
## Preparation:
- Ensure you have Pop!_OS 21.10 installed and updated.
- Verify that you have a supported AMD GPU, such as the 6900 XT.
## Download AMDGPU-PRO:
- Go to the official AMD download page and select your GPU series.
- Choose the Ubuntu installer option.
- Download the latest Radeon™ Software for Linux® installer (e.g., version 21.40.1 for Ubuntu 20.04.3). It will be a .deb package.
## Modify OS Identification:
- Open a terminal and run `sudo nano /etc/os-release`.
- Change `ID=pop` to `ID=ubuntu`.
- Save and exit the editor.
## Install AMDGPU-PRO:
- Double-click the downloaded .deb file to install it using Eddy.
- Open a terminal and run:
  ```
  sudo amdgpu-install --usecase=opencl --no-dkms
  ```
## Install Supplemental Packages:
- In the terminal, run:
  ```
  sudo apt install opencl-headers ocl-icd-libopencl1 clinfo
  ```
## Restore OS Identification:
- Open a terminal and run `sudo nano /etc/os-release` again.
- Change `ID=ubuntu` back to `ID=pop`.
- Save and exit the editor.
## Reboot:
- Reboot your system.
## Verify Installation:
- After reboot, open a terminal and run:
  ```
  clinfo | grep -i opencl
  ```
- If you see results, the installation was successful.
## Additional Tips:
- You can dry run the install to see what will happen:
  ```
  sudo amdgpu-install --usecase=opencl --no-dkms --dryrun
  ```
- View all use cases and their descriptions:
  ```
  sudo amdgpu-install --list-usecase
  ```
- The installer adds `amdgpu-uninstall` as well. Remember to change the OS identification before running it.
## Optional Steps:
- Add yourself to the render and video groups as noted in the AMD install guide.
- For more details, refer to the AMD install guide: [AMDGPU-Install Guide](https://amdgpu-install.readthedocs.io/en/latest/install-script.html)
## Note:
- The default options for usecase opencl only work for Vega or newer GPUs. If you have an older GPU, consider appending `--opencl=legacy`, although this may require testing.

These steps should help you set up AMDGPU-PRO for OpenCL on your Pop!_OS 21.10 system effectively.

---

**See also::** 

### Links to this note:
```query
"[[PopOS - OpenCL & AMD Video Card]]"
```

