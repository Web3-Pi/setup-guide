## Systemd Services

All clients use Systemd services for running. Systemd takes care of the processes and automatically restarts them in case something goes wrong. It can enable a service to automatically start it on boot as well.

Systemd command systemctl manages all operations related to the services. The available options are as follows:

- **Enable** - Activate the service to start on boot
- **Disable** - Remove the service from boot start
- **Start** - Start the client process
- **Stop** - Stop the client process
- **Restart** - Restart the clients process

The general syntax is:

``` sh
sudo systemctl enable|disable|start|stop|restart service_name.service
```

To check service output use **journalctl**

``` sh
journalctl -u serviceName.service -b
```
or continuously print new entries as they are appended to the journal
``` sh
journalctl -xefu serviceName.service
```

Example:
``` sh
journalctl -xefu w3p_nimbus-beacon.service
```

## List of services

<!-- - w3p_geth.service
- w3p_lighthouse-beacon.service
- w3p_w3p_nimbus-beacon.service
- w3p_bsm.service
- w3p_bnm.service
- grafana.service
- influxDB.service -->

### w3p_geth.service

Geth - Ethereum execution client

The w3p_geth.service file is a configuration file used to define a systemd service for running the Geth (Go Ethereum) client as a background service on Linux systems. Using w3p_geth.service, you can ensure that Geth starts automatically on boot, restarts on failure, and runs with specified parameters.

This service runs script located: **/home/ethereum/clients/geth/geth.sh**

``` sh
#!/bin/bash
geth --authrpc.port=8551 --http --http.port 8545 --http.addr 0.0.0.0 --http.vhosts '*' --ws --ws.port 8546 --ws.addr 0.0.0.0 --ws.origins '*' --authrpc.jwtsecret /home/ethereum/clients/secrets/jwt.hex --state.scheme=path --discovery.port 30303 --port 30303
```

If you need to change geth startup parameters edit this file and then restart service.

### w3p_lighthouse-beacon.service

Lighthouse - Ethereum consensus client

### w3p_w3p_nimbus-beacon.service

Nimbus - Ethereum light weight consensus client

### w3p_bsm.service

Basic System Monitor

Simplistic system monitor based on `psutils` with a dedicated http endpoint.


### w3p_bnm.service

Basic Node Monitor

A simple tool to monitor ETH2 nodes based on Web 3 Pi project. Monitor pushes data to the InfluxDB instance that, in turn, may be queried by Grafana to produce a visual representation of the node state. It works in parallel with basic system monitor and allows monitoring of multiple nodes (both single and dual-device setups).

### grafana.service

Grafana monitoring service


### influxDB.service

InfluxDB service
