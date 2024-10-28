# Working with Services in Ubuntu

## Overview

Managing services in Ubuntu is essential for starting, stopping, enabling, or disabling software applications running in the background, known as services or daemons. Ubuntu uses `systemd` as its service manager, providing tools to manage these services efficiently.

<iframe width="720" height="425" src="https://www.youtube.com/embed/8BCjDMhdDwo"></iframe>

<iframe width="720" height="425" src="https://www.youtube.com/embed/8BCjDMhdDwo"></iframe>

## Common Use Cases
- Start or stop services.
- Enable or disable services on boot.
- Check the status of a service.
- Restart services after configuration changes.

## Commands Overview

Ubuntu's `systemctl` command is the primary tool for managing services on a system that uses `systemd`. Here are some common `systemctl` commands for managing services:

| Command                   | Description                                 |
|---------------------------|---------------------------------------------|
| `systemctl start <service>` | Starts a specific service.                |
| `systemctl stop <service>`  | Stops a specific service.                 |
| `systemctl restart <service>` | Restarts a service.                   |
| `systemctl reload <service>` | Reloads a service configuration without fully stopping and starting it. |
| `systemctl status <service>` | Shows the status of a service, including whether it is active or inactive. |
| `systemctl enable <service>` | Enables a service to start at boot.     |
| `systemctl disable <service>` | Disables a service from starting at boot. |
| `systemctl is-enabled <service>` | Checks if a service is enabled to start at boot. |
| `systemctl list-units --type=service` | Lists all currently loaded services. |

### Example Usage

Let's go through some common commands used to manage services:

1. **Starting a Service**:
   ```bash
   sudo systemctl start apache2
   ```
   This command starts the Apache web server if it is installed. You need to use `sudo` as managing services typically requires root permissions.

2. **Stopping a Service**:
   ```bash
   sudo systemctl stop apache2
   ```
   Stops the Apache web server, ending its process if it’s currently running.

3. **Checking Service Status**:
   ```bash
   systemctl status apache2
   ```
   Displays the current status of the Apache web server, showing whether it's active, inactive, or failed.

4. **Enabling a Service on Boot**:
   ```bash
   sudo systemctl enable apache2
   ```
   Sets the Apache service to start automatically each time the system boots up.

5. **Disabling a Service from Boot**:
   ```bash
   sudo systemctl disable apache2
   ```
   Prevents the Apache service from starting automatically at boot time.

6. **Restarting a Service**:
   ```bash
   sudo systemctl restart apache2
   ```
   Stops and then immediately starts the Apache service, which is often used after configuration changes.

### Output Details

Each command provides feedback in the terminal. For example:

- **`systemctl status`**: Displays detailed information, including the service's status (active, inactive, failed), logs, and the process ID.
- **`systemctl enable`**: If successful, does not output any message but enables the service for future boots.
- **`systemctl is-enabled`**: Outputs `enabled` or `disabled`, indicating the current boot setting for the service.

### Example Status Output

```bash
systemctl status apache2
```

```plaintext
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2024-10-25 14:37:01 UTC; 2h 25min ago
 Main PID: 1104 (apache2)
    Tasks: 55 (limit: 4915)
   Memory: 8.0M
   CGroup: /system.slice/apache2.service
           ├─1104 /usr/sbin/apache2 -k start
           ├─1120 /usr/sbin/apache2 -k start
           └─1121 /usr/sbin/apache2 -k start
```

In this output:
- **Loaded**: Shows where the service file is located and its boot status.
- **Active**: Displays whether the service is running, along with the start time.
- **Main PID**: The main process ID running the service.
- **Tasks**: Number of tasks associated with the service.
- **Memory**: Approximate memory usage.

## Practice Exercises
1. Start and check the status of the `cron` service.
2. Restart the `ssh` service and verify it’s active.
3. Enable the `ufw` (firewall) service on boot and confirm it’s enabled.
4. List all active services on the system and identify any failed services.
5. Disable a service from boot (e.g., `cups`) and check if it’s disabled.

## Additional Resources
- [Video: How to Manage Services in Ubuntu](https://www.youtube.com/watch?v=Kzpm-rGAXos&ab_channel=LearnLinuxTV)
- [Practice Lab: Service Management in Ubuntu](https://www.youtube.com/watch?v=5JVBpXiYMKo&ab_channel=LearnLinuxTV)

## Relevance to System Administration
Proper management of services is fundamental to ensuring that necessary applications run smoothly and consistently. Automating service management for critical applications reduces downtime, and disabling unnecessary services improves security and performance.

# References
- [Managing Systemd Services](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)
- [Systemd Essentials: Working with Services](https://www.linode.com/docs/guides/start-stop-restart-systemd/)