# Multiple Server Inventory Script

This script automates the collection of system information from multiple Linux servers (RHEL and Debian-based).  
The results are stored in `server_info.csv`.

---

## Features

The script collects the following information:

- **OS Details**: Hostname, OS name, version, kernel version  
- **Hypervisor Details**: type, manufacturer, serial number, product name  
- **CPU Details**: model, frequency, number of cores, usage, load average  
- **Memory Details**: total/used, usage percentage  
- **Disk Details**: list of file systems and usage  
- **Network Details**: IP addresses, DNS servers, domain, list of interfaces  
- **Security**: AppArmor / SELinux status  
- **Swap Details**: total, used, usage percentage  
- **Uptime**

---

## Requirements

- `net-tools` package (for `netstat`)  
- Passwordless SSH authentication between servers  
- A common user account across all servers  
- The user must have `sudo` privileges

---

## Installation and Usage

1. Create a user on all servers and set up passwordless SSH:

   ```bash
   ssh-keygen -t ed25519
   ssh-copy-id user@server1
   ssh-copy-id user@server2
   ...
   ```

2. Clone the repository:

   ```bash
   git clone https://github.com/kirillstrelets/MULTIPLE-SERVER-INVENTORY-SHELL-SCRIPT.git
   cd MULTIPLE-SERVER-INVENTORY-SHELL-SCRIPT
   ```

3. Make the script executable:

   ```bash
   chmod +x multiple_server_inventory.sh
   ```

4. Create a `servers_list.txt` file containing a list of servers (one per line).

5. Run the script:

   ```bash
   ./multiple_server_inventory.sh -u <username>
   ```

   Alternatively, set the username directly in the script:

   ```bash
   USER="<username>"
   ```

---

## Example

### Running the script
```bash
./multiple_server_inventory.sh -u admin
```

### Sample output (`server_info.csv`)
```text
################################################################################

                       SERVER INVENTORY OF 192.168.1.202

################################################################################

OS DETAILS
==========
          
HOSTNAME : pc1.test.local
OS_NAME: CentOS Linux
OS_VERSION: x86_64
OS_KERNEL_VERSION: 3.10.0-1062.9.1.el7.x86_64
          
SERVER UPTIME
=============
             
UPTIME :  16:06:32 up 5 days,  3:06,  3 users
             
HYPERVISOR DETAILS
==================
                  
HYPERVISOR :  VMware Virtual Platform
MANUFACTURER : VMware, Inc.
SERIAL NO :VMware-42 32 f4 fc b1 49 29 f6-d4 38 d1 17 78 4a 24 cb
PRODUCT NAME :  VMware Virtual Platform
          
NETWORK DETAILS
==================
                  
DNS_NAME_SERVERS: 192.168.1.1
192.168.1.2
DNS_DOMAIN :test.local
NETWORK-IP :192.168.1.202
TOTAL-NETWORK-INTERFACES :1
NETWORK-INTERFACES LIST :ens192
                          
AppArmor/SELINUX STATUS
=============
             
AppArmor STATE : n/a
SELINUX STATE : disabled
             
CPU DETAILS
==========
          
CPU TYPE :  Intel(R) Xeon(R) Gold 5220R CPU @ 2.20GHz
 Intel(R) Xeon(R) Gold 5220R CPU @ 2.20GHz
 Intel(R) Xeon(R) Gold 5220R CPU @ 2.20GHz
 Intel(R) Xeon(R) Gold 5220R CPU @ 2.20GHz
CPU SPEED IN MHz :  2199.999
 2199.999
 2199.999
 2199.999 
NO OF CORES : 4
CPU USAGE : 2,2 %
LOAD AVERAGE : 1,07, 1,10, 1,07
          
MEMORY DETAILS
==============
              
TOTAL MEMORY : 2,0G
USED MEMORY : 1,3G 
MEMORY USAGE : 64,014 %
          
DISK DETAILS
==============
              
/dev/mapper/centos-root  55%
/dev/sda1                17%
              
SWAP DETAILS
============
            
TOTAL SWAP : 1,6G
USED SWAP : 9,5M
SWAP USAGE : 0,5%

################################################################################

                                      END

################################################################################
```

---

## Authors

- Original Author: [Nithin John George](https://github.com/NITHIN-JOHN-GEORGE)  
- Modified (2025): [Kirill Ovsiannikov](https://github.com/kirillstrelets)
