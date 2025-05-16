**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** 

# Fonts - Pop OS

**Created:**  19 September 2022 at  09:05 hours.

___
### Note:
Following some of the Pop OS help pages doesn't work. As of 19 Sept, this works on Pop OS

To install Microsoft Fonts

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.8_all.deb

sudo apt install ./ttf-mscorefonts-installer_3.8_all.deb

sudo fc-cache -f -v
```

This worked
![[Pasted image 20230129120346.png]]

from [here](https://www.reddit.com/r/pop_os/comments/pu55ey/ms_core_fonts_wont_install/) 

---
Note - ran the above install line and got ..

`Download is performed unsandboxed as root as file '/home/alex/ttf-mscorefonts-installer_3.8_all.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)`

This didn't seem to cause a problem.


**See also::** 

### Links to this note:
```query
"[[Fonts - Pop OS]]"
```

