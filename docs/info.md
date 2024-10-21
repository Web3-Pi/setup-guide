
This cheat sheet provides a collection of useful information and key details related to the Web3 Pi project and the applications included within it. It serves as a quick reference guide for users, offering practical tips and commands to help you navigate and make the most of the Web3 Pi ecosystem. Whether you're managing clients, configuring settings, or troubleshooting, this document will streamline your workflow.


## Internet connection

To achieve optimal synchronization performance, your internet connection should have a download bandwidth of **at least 160 Mb/s** (20 MB/s). 
The upload requirement, however, is significantly lower.  
The synchronization process with the Ethereum mainnet requires downloading approximately 1.2 TB of data.  
[1.1 TB download, 25 GB upload - October 2024]
So please be cautious if your internet connection is metered.  
A slower internet connection will still function, though the synchronization process will take longer.   
While upload and download speeds are important, they are only one factor in determining the quality of your connection. Ideally, a stable connection with low latency (ping) is recommended.   
For optimal performance, having a static public IP address is beneficial, but it is not strictly necessary.   

## WiFi connection

The default and recommended method for connecting the Raspberry Pi in the Web3 Pi project is via a wired Ethernet connection with automatic DHCP configuration.  
However, you can also connect Raspberry Pi 4/5 to the internet using the built-in WiFi module.  
To do so, in Raspberry Pi Imager, you must provide the SSID and password for your WiFi network.

Although using WiFi is possible, we strongly recommend using a wired connection. Over time, WiFi may lead to issues with connection stability and bandwidth performance.

!!! note "Note"
    If you are using WiFi, do not disconnect the Ethernet cable.


## Default passwords

### SSH

- Username: `ethereum`  
- Password: `ethereum`

You will be required to change the password to your own upon the first login.

### Grafana

- Username: `admin`  
- Password: `admin`

You will be required to change the password to your own upon the first login.

!!! note "Note"
    In Raspberry Pi Imager, when flashing the microSD card, you will need to set the username to `raspberry` and the password to `raspberry`.
    The Web3 Pi installation script uses this `raspberry` user during the installation process and then creates the `ethereum` user, subsequently removing the `raspberry` user.
    Therefore, although you enter `raspberry` during the Raspberry Pi Imager setup, after the installation is complete, you will log in using the `ethereum` user.

## Default ports

### Geth

- 30303 (TCP/UDP) for peer-to-peer (P2P) communication.
- 8545 (TCP) for the JSON-RPC server (HTTP).
- 8546 (TCP) for the WebSocket server.

### Nimbus

- 9000 (TCP/UDP) for peer-to-peer (P2P) communication.

### Lighthouse

- 9000 (TCP/UDP) for peer-to-peer (P2P) communication.
- 5052 (TCP) for the HTTP REST API.

### Grafana

- 3000 (TCP) for the web interface.

### SSH

- 22 (TCP) for remote login.



## InfluxDB

InfluxDB stores device status measurements and serves as the data source for Grafana.

The Influx database is fed by the 'basic-eth2-node-monitor' application, which collects data from Ethereum clients. It also receives input from the 'basic-system-monitor' application, which gathers operating system statistics and serves them as JSON over HTTP

The Web3 Pi image uses InfluxDB version 1.8.10.

To clear the accumulated data from the database, log in to the device via SSH and execute the following commands sequentially:

``` sh
influx
USE ethonrpi
DROP SERIES FROM /.*/
exit
```


## Nimbus

"Its efficiency and low resource consumption allows it to perform well on all kinds of systems: ranging from Raspberry Pi and mobile devices" (source: https://nimbus.guide)


Default Nimbus dir = `/mnt/storage/.nimbus/data/shared_mainnet_0`   

How to clear saved data:   
``` sh
sudo rm -r /mnt/storage/.nimbus/data/shared_mainnet_0
```

Startup script: `/home/ethereum/clients/nimbus/nimbus.sh`

Service name: `w3p_nimbus-beacon.service`


## Geth

Geth (Go Ethereum) is one of the most widely used Ethereum execution clients, written in Go.  Its efficient resource usage makes it a great option for running a full Ethereum node on constrained hardware while still maintaining full network functionality.

Default Geth dir = `/mnt/storage/.ethereum`   

How to clear saved data:   
``` sh
sudo rm -r /mnt/storage/.ethereum
```

Startup script: `/home/ethereum/clients/geth/geth.sh`

Service name: `w3p_geth.service`

## Lighthouse

Lighthouse is one of the most popular consensus clients and can be used as an alternative to Nimbus, the default consensus client in Web3Pi. However, make sure not to run both clients at the same time.

Default Lighthouse dir = `/mnt/storage/.lighthouse`   

How to clear saved data:   
``` sh
sudo rm -r /mnt/storage/.lighthouse
```

Startup script: `/home/ethereum/clients/lighthouse/lighthouse.sh`

Service name: `w3p_lighthouse-beacon.service`

## JWT Secret

The jwt.hex file is generated by the installation script and stored in the directory `/home/ethereum/clients/secrets/jwt.hex`.  
This file is crucial for enabling authenticated communication between the execution and consensus clients, ensuring the integrity and security of Ethereum's client interactions.

## Storage

### PCIe Generation

PCIe Gen 2 vs. PCIe Gen 3 on Raspberry Pi 5

By default, Raspberry Pi 5 uses PCIe Gen 2, and this is the officially supported version. However, it's possible to enable PCIe Gen 3 on Raspberry Pi 5 through a simple configuration tweak. While this is not officially supported, it typically works without issues.

Benefits of PCIe Gen 3:

- **Higher Bandwidth**: PCIe Gen 3 offers double the bandwidth compared to PCIe Gen 2. This means faster data transfer rates, which can be especially beneficial for high-speed storage devices like NVMe SSDs or network cards.
- **Improved Performance**: For applications that are bottlenecked by PCIe bandwidth, enabling Gen 3 can significantly improve performance.

While Raspberry Pi 5 is designed for PCIe Gen 2, upgrading to Gen 3 can unlock more potential in compatible devices.