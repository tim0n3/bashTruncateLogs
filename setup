#!/bin/bash

# Install the service and timer unit files
sudo cp ./service/truncate-logs.service /etc/systemd/system/
sudo cp ./service/truncate-logs.timer /etc/systemd/system/

# Replace placeholders with absolute file paths
SCRIPT_PATH=$(realpath ./src/truncate_logs.sh)
SCRIPT_DIRECTORY=$(realpath ./src/)

# Update the service unit file with the actual paths
sudo sed -i "s|/path/to/your/script.sh|$SCRIPT_PATH|g" /etc/systemd/system/truncate-logs.service
sudo sed -i "s|/path/to/your/script/directory|$SCRIPT_DIRECTORY|g" /etc/systemd/system/truncate-logs.service

# Reload systemd and enable the timer
sudo systemctl daemon-reload
sudo systemctl start truncate-logs.timer
sudo systemctl enable truncate-logs.timer

echo "Setup completed. The script will now run once every 5 minutes to truncate log files."