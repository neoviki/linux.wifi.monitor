# WiFi Connectivity Monitor and Auto-Restart Script

This is a simple bash script that continuously monitors the WiFi connection on a Linux-based system. If the connection to the gateway IP fails repeatedly, the script will automatically restart the WiFi interface to restore the connection.

## How to Install

1. Clone or download this repository.
2. Navigate to the `src` directory:
   ```bash
   cd src
   ```
3. Run the installation script:
   ```bash
   ./install.sh
   ```
   This will add the WiFi Monitor daemon (`wifi.monitor`) to the startup script, ensuring that it starts and runs on every reboot. The script will be added to `rc.local` to make sure it is executed automatically.


### Background

I wrote this script a while back when my WiFi card was loose, causing frequent connection drops. This script helps mitigate the issue by checking the WiFi connection at regular intervals. If the connection is unstable or lost, it will restart the WiFi interface and attempt to reconnect.

### How it Works

1. The script pings the gateway IP (default is `192.168.0.1`).
2. If the connection fails, it keeps a count of failures.
3. After a certain threshold (15 failed attempts), it restarts the WiFi connection by turning off and on the networking service.
4. It logs the connection failures and restarts in `/tmp/wifi_monitor.log`.

### Usage

1. Clone or download this repository.
2. Make the script executable:
   ```bash
   chmod +x wifi_monitor.sh
   ```
3. Run the script:
   ```bash
   ./wifi_monitor.sh
   ```

The script will keep running indefinitely and monitor the WiFi connection.

