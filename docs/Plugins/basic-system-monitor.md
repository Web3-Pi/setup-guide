# Basic System Monitor

The Basic System Monitor plugin is responsible for monitoring the health and status of your Web3 Pi.

## Installation

To install the Basic System Monitor plugin, navigate to the "Web3 Pi Updater" section in the Cockpit interface. Search for "Basic System Monitor" and install the plugin. On newer Web3 Pi releases, this plugin might be pre-installed by default.

## Usage

Once installed, the Basic System Monitor plugin will start automatically. You can query the status of your Web3 Pi by calling the HTTP API endpoint on port 7197 (by default).

The output should look similar to this:

```json
{
  "host_name": "eop-1",
  "num_cores": 4,
  "cpu_percent": 30,
  "mem_total": 8323276800,
  "mem_used": 6859583488,
  "mem_free": 386887680,
  "mem_percent": 85.4,
  "swap_total": 17179865088,
  "swap_used": 7224090624,
  "swap_free": 9955774464,
  "swap_percent": 42,
  "disk_used": 1359481831424,
  "cpu_temp": 58.95,
  "net_upload": 510982.969251317,
  "net_download": 702530.988724869
}
```

## Support

For support and further assistance, join the [Web3 Pi Discord](https://discord.gg/aDMw5zeUZ4) community.
