**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #Azure #davros #servers
# Azure - Davros

**Created:**  16 May 2024 at  19:51 hours.
___
### Note:
1. Admin user: davrosadmin 
   - use SSH to gain access (*ssh azure_davosadmin*) then use 'davos' (*su davos*) - see SSH below.
2. Server Admin: davros
   - See 1. above then `su davos` 
   - Password is *T1ddalik@*
3. DNS:
   - name: davros.australiaeast.cloudapp.azure.com
   - IP4: 20.167.50.15

## SSH
SSH into the Azure instance (davros)
Public IP: *20.167.50.15*
Port: *22*

**user:** *davrosadmin* (has sudo permissions)
**ssh key:** *davros_key.pem* (in ~/.ssh)

### How to log in to server - SSH
To log into davros as *davrosadmin* using SSH from Windows.
1. Open Terminal or WSL etc.
2. CD to ~/.ssd
3. Run `ssh -i ~/.ssd/davros_key.pem davrosadmin@20.167.50.15`
   OR
4. Run `ssh azure_davrosadmin` (this pulls setup from the *~/.ssh/config* file)

This will give a login to the davros server and the prompt <span style="font-weight: bold; color: limegreen;">davrosadmin@davros:~S</span>

## VMs on Davros
The Azure Davros server runs Webmin with several Virtualmin VMs
1. **tiddalik.com.au** which has sub vms of: 
	- *staging.learn.tiddalik.com.au* 
	- *learn.tiddalik.com.au*
2. **tiddalikservices.com.au** which has a sub VM of:
	- *staging.tiddalikservices.com.au*
3. **tiddalikservices.com.au**

## Maria Databases for tiddalik.com.au VMs
See here for notes on the Maria Database situation on davros - [[Mariadb for tiddalik.com.au]]
Particularly the log in process.

**See also::** 

### Links to this note:
```query
"[[Azure - Davros]]"
```

