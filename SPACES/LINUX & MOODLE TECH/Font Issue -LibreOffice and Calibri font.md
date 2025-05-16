**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #font #calibri #libre-office #bitmap

# Font Issue -LibreOffice and Calibri font

**Created:**  21 February 2023 at  13:30 hours.

___
### Note:
**Situation**: 
	- OS - Endeavour OS
	- DE - XFCE
	- Software - LibreOffice
	- Fonts - ttf-ms fonts installed including calibri, arial, times new roman etc.

**Process** - either open a document (docx or odt file) containing calibri font where size is less than 15pt or create a new document and type some text set as calibri and with font size less than 15 points.

**Symptoms** - In LibreOffice Writer, Calibri font will not show most characters if they are under 15pt size.

**Problem** - due to bitmap substitution that automatically occurs. 
See similar issue with same solution [here](https://forum.endeavouros.com/t/terrible-font-rendering-for-gmails-in-evolution-and-geary/24710)
See solution for Arch based distros [here](https://wiki.archlinux.org/title/Font_configuration#Disable_scaling_of_bitmap_fonts) 

**Solution** - disable bitmap substitution which occurs for smaller sizes of fonts. This can be done for all fonts or for select fonts.
 - See here - [disable bitmap fonts](https://wiki.archlinux.org/title/Font_configuration#Disable_bitmap_fonts)

For Arch system ie. Manjaro or Endeavor OS

Bitmap fonts are sometimes used as fallbacks for missing fonts, which may cause text to be rendered pixelated or too large. Use the `70-no-bitmaps.conf` [preset](https://wiki.archlinux.org/title/Font_configuration#Presets) to disable this behavior.

To disable embedded bitmap for all fonts:
create or edit this  file
`~/.config/fontconfig/conf.d/20-no-embedded.conf`

```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "urn:fontconfig:fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="embeddedbitmap" mode="assign">
      <bool>false</bool>
    </edit>
  </match>
</fontconfig>
```

OR ...To disable embedded bitmap fonts for a specific font:

```xml
<match target="font">
	<test qual="any" name="family">
		<string>Monaco</string>
	 </test>
	<edit name="embeddedbitmap">
		<bool>false</bool>
	</edit>
</match>
```

**See also::** 
1. Whole Arch wiki page on font config ... [here](https://wiki.archlinux.org/title/Font_configuration) 
2. Font management - how to manage huge lists of fonts - [here](https://discovery.endeavouros.com/desktop-environments/font-management/2021/03/) 

### Links to this note:
```query
"[[Font Issue -LibreOffice and Calibri font]]"
```

