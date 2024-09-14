#!/bin/bash

# Get the current external IP from a reliable service
ext_ip=$(curl -s https://api.ipify.org)

# Log the external IP for debugging
echo "External IP: $ext_ip"

# Get the current WOPI allow list from Nextcloud
current_wopi_list=$(docker exec nextcloud bash -c "occ config:app:get richdocuments wopi_allowlist")

# Check if the external IP is blank (no internet connection)
if [ "$ext_ip" = "" ]; then
    echo "No internet connection. Unable to update IP."

# If the current WOPI allow list matches the external IP, no need to update
elif [[ "$current_wopi_list" == *"$ext_ip"* ]]; then
    echo "IP is up to date: $ext_ip"

# If the current WOPI allow list does not match the external IP, update it
else
    echo "DynDNS is not up to date, updating IP: New IP = $ext_ip"
    
    # Use bash -c to ensure proper command execution
    docker exec nextcloud bash -c "occ config:app:set richdocuments wopi_allowlist --value=\"$ext_ip\""
    
    # Check if the IP was successfully set
    if [ $? -eq 0 ]; then
        echo "WOPI allow list updated successfully."
    else
        echo "Failed to update WOPI allow list."
    fi
fi
