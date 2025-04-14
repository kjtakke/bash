# Bash Networking 

| Command | Description |
|---------|-------------|
| `ip a` | Show all network interfaces and IP addresses. |
| `ip link show` | Display network interfaces and their states. |
| `ip route` | Show routing table. |
| `ifconfig` | Show network interfaces (deprecated, use `ip a`). |
| `ip -c addr show` | Show IP addresses with colour formatting. |
| `ip -c route show` | Show routing table with colour formatting. |
| `nmcli device status` | Show network devices and connection status (NetworkManager). |
| `nmcli connection show` | List saved network connections. |
| `ping -c 4 <host>` | Send 4 ICMP echo requests to a host. |
| `traceroute <host>` | Show the route packets take to a host. |
| `mtr <host>` | Continuous traceroute with statistics. |
| `dig <domain>` | Query DNS records for a domain. |
| `nslookup <domain>` | Query DNS records using `nslookup`. |
| `host <domain>` | Look up DNS records for a domain. |
| `curl -I <URL>` | Fetch HTTP headers from a website. |
| `wget <URL>` | Download a file from a URL. |
| `nc -zv <host> <port>` | Check if a port is open on a host. |
| `telnet <host> <port>` | Open a raw TCP connection to a port. |
| `ssh <user>@<host>` | SSH into a remote machine. |
| `scp <file> <user>@<host>:<path>` | Copy a file to a remote machine via SSH. |
| `rsync -avz <file> <user>@<host>:<path>` | Sync files with compression over SSH. |
| `netstat -tulnp` | Show active listening ports and processes. |
| `ss -tulnp` | Show active sockets (replacement for `netstat`). |
| `iptables -L -v -n` | List firewall rules. |
| `ufw status` | Show firewall rules (Ubuntu's Uncomplicated Firewall). |
| `tcpdump -i eth0 port 80` | Capture packets on eth0 for port 80. |
| `arp -a` | Show ARP table (list of known MAC addresses). |
| `ip neigh` | Show ARP/NDP neighbour cache. |
| `iwconfig` | Show wireless network details. |
| `iwlist scan` | Scan for available Wi-Fi networks. |