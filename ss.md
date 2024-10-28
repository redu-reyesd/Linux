# Working with `ss` in Ubuntu

## Overview

`ss` (Socket Statistics) is a command-line tool used to display socket information, including open connections, listening ports, and other details about network activity. It is a faster and more modern alternative to `netstat` and is included by default in many Linux distributions.

<iframe width="720" height="425" src="https://www.youtube.com/embed/phY8Q7Woxsw"></iframe>

<iframe width="720" height="425" src="https://www.youtube.com/embed/MflyDveS3Ps"></iframe>

## Common Use Cases
- View all active connections and listening ports.
- Display detailed information about TCP and UDP sockets.
- Filter results to show connections by protocol (e.g., TCP, UDP).
- Check for specific ports or connections.

## Command Options

| Command                         | Description                                              |
|---------------------------------|----------------------------------------------------------|
| `ss -a`                         | Display all sockets (both listening and non-listening).  |
| `ss -t`                         | Show only TCP sockets.                                   |
| `ss -u`                         | Show only UDP sockets.                                   |
| `ss -n`                         | Show numerical addresses instead of resolving hostnames. |
| `ss -l`                         | Display only listening sockets.                          |
| `ss -p`                         | Display the process ID (PID) and name for each socket.   |
| `ss -r`                         | Display routing table information.                       |
| `ss -i`                         | Display detailed information about each connection.      |
| `ss -s`                         | Display summary statistics for network sockets.          |

### Example Usage

Here are some practical ways to use the `ss` command to manage and monitor network sockets.

1. **Display All Sockets**:
   ```bash
   ss -a
   ```
   This command shows all sockets, including those that are listening and established, across all protocols (TCP, UDP, etc.).

2. **Show Only TCP Connections**:
   ```bash
   ss -t
   ```
   Lists only the TCP sockets, which can help focus on reliable, connection-based protocols.

3. **Show Only UDP Connections**:
   ```bash
   ss -u
   ```
   Lists only UDP sockets, useful for applications using UDP for connectionless communication.

4. **View Listening Sockets Only**:
   ```bash
   ss -l
   ```
   Filters results to display only listening sockets, showing which services are actively waiting for connections.

5. **Display Process Information with Sockets**:
   ```bash
   sudo ss -tp
   ```
   Adds process ID (PID) and program names to the output, showing which processes are managing each socket. Requires `sudo` for detailed information.

6. **Show Sockets in Numerical Format**:
   ```bash
   ss -tn
   ```
   Displays addresses and ports in numerical format without resolving hostnames, which can be faster and useful for scripting.

### Output Details

The `ss` command output provides key socket details, such as protocol, addresses, and connection status. Here’s an example with explanations:

```plaintext
State    Recv-Q Send-Q      Local Address:Port          Peer Address:Port
LISTEN   0      128         127.0.0.53%lo:53            0.0.0.0:*
ESTAB    0      0           192.168.1.100:22            192.168.1.5:54628
```

- **State**: Indicates the connection state (e.g., `LISTEN`, `ESTAB` for established).
- **Recv-Q**: Bytes in the receive queue (data received but not yet read).
- **Send-Q**: Bytes in the send queue (data written but not yet sent).
- **Local Address:Port**: The address and port on the local machine.
- **Peer Address:Port**: The address and port of the remote machine.

### Advanced Filtering Example

Use multiple options together to filter results:
```bash
ss -tulnp
```

- **-t**: Show only TCP sockets.
- **-u**: Show only UDP sockets.
- **-l**: Show only listening sockets.
- **-n**: Show numerical addresses instead of resolving hostnames.
- **-p**: Display process information for each socket.

### Example Output

```plaintext
State   Recv-Q Send-Q  Local Address:Port      Peer Address:Port
LISTEN  0      100     0.0.0.0:22              0.0.0.0:*          users:(("sshd",pid=596,fd=3))
LISTEN  0      128     127.0.0.53%lo:53        0.0.0.0:*          users:(("systemd-resolve",pid=479,fd=13))
```

## Practice Exercises
1. List all listening sockets on the system.
2. Display only established TCP connections and identify their local and remote addresses.
3. Show all sockets with their process IDs and names.
4. Check active UDP connections using `ss` and find out which applications are using them.

## Additional Resources

- [Video: use Socket statistics to investigate your Linux network. Alternative to Netstat](https://www.youtube.com/watch?v=92-RCkdoKDw&ab_channel=dolastackdevops)
- [Linux tools: How to use the ss command
](https://www.redhat.com/en/blog/ss-command)

## Relevance to Nagios
Nagios can integrate `ss` to check whether critical services are listening on the correct ports, and alert administrators if a service is down.

# References

- Dolastack DevOps. (2022, September 10). *Use socket statistics to investigate your Linux network: Alternative to netstat* [Video]. YouTube. https://www.youtube.com/watch?v=92-RCkdoKDw

- Macchi, R. (2021, August 10). *Linux tools: How to use the ss command*. Red Hat. https://www.redhat.com/en/blog/ss-command 

- Dolastack DevOps. (2022, September 14). *Socket statistics command for Linux network monitoring* [Video]. YouTube. https://www.youtube.com/watch?v=phY8Q7Woxsw

- Dolastack DevOps. (2022, October 5). *Advanced Linux network monitoring with ss* [Video]. YouTube. https://www.youtube.com/embed/MflyDveS3Ps

- Ken Hess. (2020, January 13). Linux tools: How to use the ss command. https://www.redhat.com/en/blog/ss-command

- Paras Nath Chaudhary. (2019, October 19). Learn to use ss — utility to investigate sockets | by Paras Nath Chaudhary | Medium. https://medium.com/@opnchaudhary/learn-to-use-ss-utility-to-investigate-sockets-281630f7a334

