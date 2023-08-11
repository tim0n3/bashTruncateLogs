# bashTruncateLogs
Zero all files in /var/log/ 

# Log Truncation Service

This repository contains a script, systemd service, and systemd timer that work together to periodically truncate log files in the `/var/log` directory.

## Introduction

Logs can accumulate over time and consume disk space. This script automates the process of truncating log files, effectively clearing their content while retaining the file structure. The systemd service and timer ensure that this truncation process occurs regularly, preventing log files from growing excessively.

## Installation

1. **Clone the Repository**

   Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/log-truncation-service.git
   cd log-truncation-service
 
Certainly! Here's a comprehensive README.md template that includes installation instructions for the script, systemd service, and systemd timer setup:

markdown
Copy code
# Log Truncation Service

This repository contains a script, systemd service, and systemd timer that work together to periodically truncate log files in the `/var/log` directory.

## Introduction

Logs can accumulate over time and consume disk space. This script automates the process of truncating log files, effectively clearing their content while retaining the file structure. The systemd service and timer ensure that this truncation process occurs regularly, preventing log files from growing excessively.

## Installation

1. **Clone the Repository**

   Clone this repository to your local machine:

   ```
   git clone https://github.com/your-username/log-truncation-service.git
   cd log-truncation-service
   ```

Create the Service Unit File

Create or modify the systemd service unit file:

```
sudo nano /etc/systemd/system/truncate-logs.service
Add the following content to the file:
```

```
[Unit]
Description=Periodically truncate log files in /var/log
After=network.target

[Service]
Type=simple
ExecStart=/path/to/your/script.sh
WorkingDirectory=/path/to/your/script/directory
StandardOutput=syslog
StandardError=syslog

[Install]
WantedBy=default.target
```
Save and close the file.

Create the Timer Unit File

Create or modify the systemd timer unit file:

```sudo nano /etc/systemd/system/truncate-logs.timer```
Add the following content to the file:

```
[Unit]
Description=Timer for truncating log files

[Timer]
OnCalendar=*:0/5
Persistent=true
Unit=truncate-logs.service

[Install]
WantedBy=timers.target
```
Save and close the file.

Reload systemd and Enable the Timer
```
sudo systemctl daemon-reload ;
sudo systemctl start truncate-logs.timer ;
sudo systemctl enable truncate-logs.timer ;
```
Check the Timer Status

To verify that the timer is running:


```
sudo systemctl status truncate-logs.timer
The script will now run once every 5 minutes to truncate log files in the /var/log directory.
```

##License
This project is licensed under the MIT License.


Replace `your-username`, `/path/to/your/script.sh`, and `/path/to/your/script/directory` with the actual values corresponding to your system setup.
