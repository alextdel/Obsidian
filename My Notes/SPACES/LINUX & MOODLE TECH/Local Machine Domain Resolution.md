**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #DNS #hosts_file #local_domain_resolution #nsswitch_conf #Endeavouros 

# Local Machine Domain Resolution

**Created:**  05 May 2023 at  17:45 hours.

___
### Note:
In the event that a local domain - for example one set up for a 'Local' WordPress installation - fails to resolve
1. Check the /etc/hosts file to make sure the correct entries exist - for example for a learnbricks.local domain where the website is hosted on the local maching
   ```
	127.0.0.1 learnbricks.local localhost learnbricks
   ::1 learnbricks.local localhost learnbricks
   127.0.0.1 www.learnbricks.local localhost learnbricks
   ::1 www.learnbricks.local localhost learnbricks
   ```
   
2. Check the /etc/resolv.conf file as this can control the order of resolution - for example
	```  # Use the loopback address first for local domain name resolution
	nameserver 127.0.0.1
	
	# Use the DNS server provided by your router as a secondary option
	nameserver 192.168.1.1
	
	# Retry failed queries using a different source port
	options single-request-reopen
	
	```


3.  Check the hosts line in the /etc/nsswitch.conf file. This controls the order of querying the various ways of resolving domain names. A correct version is this.
```
hosts: files mymachines mdns_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] myhostname dns"
```

Notice the files entry is early in the list as we want the 'hosts' file to be checked early on for local domains.
 

**See also::** 

### Links to this note:
```query
"[[Local Machine Domain Resolution]]"
```