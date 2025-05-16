**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Linux #shell_script #Wacom #Tablet #Gimp #Inkscape

# Wacom Setup Shell Script

**Created:**  03 April 2023 at  20:34 hours.

___
### Note:

This program is a linux shell script to run when rotation is required for a Wacom tablet (Intuos Pro M). It is for use when the usb plug will be on the left and control buttons on the right.

1. Place the following in an appropriate file eg. WacomSet.sh
2. Save in an appropriate home directory eg. ~/My_Scripts.
3. Make the file executable and run when rotation is required for the Wacom tablet (Intuos Pro M) - that is when the usb plug will be on the left and control buttons on the right.


```sh
#!/bin/sh

######################################################################
## This script                                                      ##
## (i). Revolves the stylus and eraser to suite a LH orientation    ##
## (ii). Disables the Finger device which cannot be rotated         ##
## (iii). Maps the Wacon tablet area to the desired (first) monitor ##
######################################################################


###################################################################
#Monitor and Pad Identification
#Automatically uses xrandr to pull the monitor details and finds
#the first monitor identifyer
# --Note: change 'head -n 1' (ie. to 2 or 3 etc) if other monitors
# -- are used for the Wwacom tablet area
####################################################################
MONITOR=$(xrandr | grep -w 'connected' | awk '{print $1}' | head -n 1)
PAD_NAME='Wacom Intuos Pro M Pad pad'

###################################################################
#Wacom Device ID discovery
###################################################################
ID_STYLUS=`xinput | grep "Pen stylus" | cut -f 2 | cut -c 4-`
ID_ERASER=`xinput | grep "Pen eraser" | cut -f 2 | cut -c 4-`
ID_PAD=`xinput | grep "Pad pad" | cut -f 2 | cut -c 4-`
ID_FINGER=`xinput | grep "Finger" | cut -f 2 | cut -c 4-`

fn_map_rotate ()
{
    ##########################################################
    # Discover current state of device 'Rotate' property
    ##########################################################
    STYLUS_ROTATION=`xsetwacom --get "$ID_STYLUS" Rotate`
    ERASER_ROTATION=`xsetwacom --get "$ID_ERASER" Rotate`
    
    ###########################################################
    # Note: 1. FINGER_ROTATION cannot be set  see (ii) above
    #       2. PAD not included as this is the button and
    #          cursor control part of the device
    ##########################################################

    #########################################################
    #Map Wacon tablet area to first monitor
    # - this line maps the active area to one monitor only
    ##########################################################
    xinput map-to-output $ID_STYLUS $MONITOR

    ##########################################################
    #Disable Finger Device see (ii) above
    #The Wacom tablets 'Finger' device cannot be rotated so we disable it
    #This line turns off the finger sensor even if hardware switch = on
    ##########################################################
    xinput disable "$ID_FINGER"


    #########################################################
    #Set Buttons for Wacom device
    #########################################################
    # this is an example of mapping the buttons to an
    # application's controls
    ##########################################################
    # to define buttons use this form of the xsetwacom command
    # erase in krita
    #    xsetwacom --set "$PAD_NAME" Button 2 "key e"
    ##########################################################
    
    ##########################################################
    #undo
    # functions as the undo ctrl+z button combination
    # the -z -ctrl indicate the release key actions 
    xsetwacom --set "$PAD_NAME" Button 1 "key +ctrl +z -z -ctrl" 

    ############################################################
    #Rotate the Stylus and Eraser
    #  Set the Rotations to 'half' if currently 'none'
    ############################################################

    if [[ "$STYLUS_ROTATION" == "none" ]];
    then
        xsetwacom --set "$ID_STYLUS" Rotate half    
    fi

    if [[ "$ERASER_ROTATION" == "none" ]];
    then
        xsetwacom --set "$ID_ERASER" Rotate half    
    fi
}

##########################################################################
## Main program which calls the function if the Wacom tablet is connected
##########################################################################

if lsusb | grep -q "056a:"; then
    fn_map_rotate
else
    notify-send "Wacom Intuos tablet not detected"
fi

exit 0
```

This can also be run when the USB device is plugged  in or as part of running Gimp, Inkscape or any other program where a tablet can be used.



**See also::** 

### Links to this note:
```query
"[[Wacom Setup Shell Script]]"
```

