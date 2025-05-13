**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #Linux #Endeavouros #Printing #CUPS 

# EndeavourOS CUPS printing - error connecting HP Printer

**Created:**  24 April 2023 at  11:05 hours.

___
### Fault:
When installing a printer on EndeavourOS, the CUPS server gives an error when/after selecting the driver. Reinstalling CUPS didn't fix the problem and the CUPS server is working correctly. This seems to be a network issue because of the computer being on a local home network.
See [here for the fix](https://forum.endeavouros.com/t/solved-cups-server-error/15307) 
#### Fix
edit the */etc/nsswitch.conf* file and add the bold parts
> hosts: … **mdns_minimal [NOTFOUND=return]** resolve [!UNAVAIL=return] dns `

This fix worked first time.

----------------------------------
##### Reasoning
Some of the reasoning for this change (basically has the order in which the computer tries different methods to find a network location changed ie. *mdns_minimal* first then if unsuccessful try the next in the list eg *dns*) are described [here](https://superuser.com/questions/1417190/why-do-i-need-to-change-the-order-of-hosts-in-nsswitch-conf).

**See also::** 

### Links to this note:
```query
"[[EndeavourOS CUPS printing - error connecting HP Printer]]"
```

