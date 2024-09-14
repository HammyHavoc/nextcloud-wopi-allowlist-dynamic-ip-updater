# Nextcloud WOPI Allowlist Dynamic IP Updater

This script automatically updates the WOPI allow list in Nextcloud Office with your current external IP address. It's designed for environments where the external IP is dynamic and frequently changes. I'm using it as a User Script on Unraid, but it will work elsewhere too.

## Features

- **Dynamic IP Detection**: Uses a reliable external IP service to get the current public IP.
- **Automatic Updates**: Updates the WOPI allow list in Nextcloud if the IP changes.

## Prerequisites

- **Nextcloud**: Make sure you have Nextcloud installed and accessible via Docker. This script assumes your Docker container for Nextcloud is called `nextcloud`.
- **Docker**: The script interacts with a Docker container running Nextcloud.
- **curl**: Used for fetching the current IP address.

## Setup

1. **Create a new file**: Save the script as `update_wopi_ip.sh`.

2. **Make the script executable**:
    ```bash
    chmod +x update_wopi_ip.sh
    ```

3. **Set Up Cron Job**:
    To ensure the script runs periodically, add it to your crontab. For example, to run the script every hour, you can add the following line to your crontab:
    ```bash
    0 * * * * /path/to/update_wopi_ip.sh
    ```

4. **Configuration**:
    - Modify the script to suit your environment, especially ensuring that the `docker exec` command matches your container name and Nextcloud configuration.

## Contributions

Feel free to contribute by submitting pull requests or reporting issues.
