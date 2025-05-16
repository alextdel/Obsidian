**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #moodle #staging #Lightsail #LAMP 

# Moodle Staging Server Setup

**Created:**  8 May 2023.

___
### Note:
These notes are for the new staging server **(as at 18 May 2023)** which will be a single server setup with Moodle and Database on the same server.
Once running and tested, the current production server (LAMP web server with separate Data instance server) will be made from a snapshot of this server.

### Instance Details

#### Plan
**2GB** memory, **1CPU**, **60GB** SSD, **1.5TB** transfer
**$10** per month after 3 month of running

#### ID
tdlk-LRN-staging

#### Username
bitnami

#### SSH Keys
available from management dashboard. {See also .ssh subdirectory on PopOS}

#### Tags
STAGING, moodle, web+data
CreationDate 30Mar2023

#### Specs
LAMP using Apache, MariaDB and PHP 8

#### Snapshots
Manual snapshots are available as needed
Automatic snapshots **enabled**
 - created at 12pm GMT +10hrs
 - 7 most recent are retained

---
### Networking Details

***IPv4***
*Internal Lightsail IP (private IP - not visible from www)*:
- 172.26.7.229 

**Attached Lightsail Static IP (public IP)**:
 - *Name*: StaticIp-TDLKLRN_Staging
 - *IP:* 54.66.18.60 *(used for internet DNS and domain registration etc.)*

***IPv6** Public IP only changes when IPv6 is disabled and re-enable IPv6
- 2406:da1c:28e:2e00:c0fd:9be9:81a8:4274

#### Firewall Rules
- SSH: TCP port 22 - any IPv4 (used for Lightsail browser plus SSH/RDP)
- HTTP: TCP port 80
- HTTPS: TCP port 443

*Firewall Rules - IPv6*
As above

---




**See also::** 

### Links to this note:
```query
"[[Moodle Staging Server Setup]]"
```

