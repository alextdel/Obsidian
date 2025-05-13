**up::** [[Accessibility MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #accessibility #pdf #acrobat #links #tags #alt_text

# PDF Accessibility Fixes

**Created:**  27 June 2023 at  14:57 hours.

___
### Note:
The following errors may be addressed as below:

---
## PDF Fixes - for PAC 2021 errors
Use the [PAC 2021 tool](https://pdfua.foundation/en/pdf-accessibility-checker-pac/) to test PDFs

The following are fixes suggested by Shawn Jordison (The Accessibility Guy). Check his [Accessibility Guy YouTube](https://www.youtube.com/channel/UCPO0yzGQJmAa290DjrByhwQ) channel for tutorials.

#### Possible inappropriate use of a "Figure" structure element
We have to set an attribute for each image as it is missing something
- Right click the figure tag > select properties > edit tag > select the first dictionary item (under Tag Element) > select New Item
	- Key = Placement
	- Value = Block
![[PDF Tag Key Addition 1.png]]
#### Non-standard structure type "Artifact" is neither mapped to a standard structure type nor to another non-standard structure type
The “Artifact” tag is not really a tag that can be used and will fail the PAC test. A true artifact does not show up in the tags panel.
When this fault occurs ... 
- expand the 'Artifact' tags that are present in the tags menu - so each of the tag's contents are seen and ready for being multiselected
- Click on the first Artifact contents (image or path etc) then Ctrl + click on each to multiselect
- Right click on one object and select *Change Tag to Artifact*
![[PDF Tag Artifact Correction 1.png]]
#### OCCD (optional content configuration dictionary) contains AS key
This is related to layer settings in the pdf. 
1. Open the Preflight function from the Print Production tool
2. Select the Acrobat Pro DC 2015 Profiles from the dropdown menu
3. Select the wrench button (third button )
4. In the Layers panel select "All objects on currently invisible layers are discarded and all layers, including visible ones are flattened (removed from document)"
5. Click on Fix button - wrench at bottom right
![[PDF Correction OCCD 1.png]]

#### Correct Link Tag structure and Alt text ...
Reference for error ... :
1. **Link annotation is not nested inside a Link structure element** [see here](https://taggedpdf.com/508-pdf-help-center/link-annotation-is-not-nested-inside-a-link-structure-element/) 
2. **Alt text requirements** [see here](https://taggedpdf.com/508-pdf-help-center/actual-text-alt-text-expansion-text-contents-key/)
##### Link Tag Structure
This is an example of a Link where text is found each side of the link.
![[Pasted image 20231002154120.png]]

The tags should look like 
![[Pasted image 20231002154307.png]]
##### Alt text for Link tags
The link should also be given *alt text*
- right click on the `<Link>` tag and enter *alt text* for the link eg. "**Service Level Standards | Opens in browser window**"
	- Another example is where the actual url is given eg. www.theurl.etc.gov



**See also::** 

### Links to this note:
```query
"[[PDF Accessibility Fixes]]"
```

