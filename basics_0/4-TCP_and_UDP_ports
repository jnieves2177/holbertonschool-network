#!/bin/bash
# Get a list of listening sockets and their associated PIDs
listening_sockets=$(netstat -tuln | grep LISTEN)

# Print the headers for the output
echo "Protocol  Port  PID   Program"

# Loop through the listening sockets
while read -r line; do
    protocol=$(echo "$line" | awk '{print $1}')
    port=$(echo "$line" | awk '{print $4}' | awk -F: '{print $NF}')
    pid=$(echo "$line" | awk '{print $7}' | awk -F/ '{print $1}')
    program=$(ps -p "$pid" -o comm=)

    # Print the information
    echo "$protocol   $port   $pid   $program"
done <<< "$listening_sockets"
