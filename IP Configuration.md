Configuring IP settings is a crucial part of managing network interfaces on a system. Proper IP configuration ensures that a device can communicate over a network effectively. This process typically involves setting an IP address, subnet mask, default gateway, and DNS servers.

Here's a detailed guide on configuring IP settings on Linux, commonly using the `ip` command and configuration files.

# Configuring IP Addresses on Linux

## Using the `ip` Command

The `ip` command is part of the `iproute2` package and offers powerful ways to configure and display networking details.

### View Current Configuration

Display current network interfaces and their configurations:

```bash
ip addr show
```

### Assign a Static IP Address

1. **Bring the interface down** (Replace `<interface>` with the interface name, e.g., `eth0`):

   ```bash
   sudo ip link set <interface> down
   ```

2. **Assign the IP address** (Replace `192.168.1.10/24` with your desired IP address and subnet):

   ```bash
   sudo ip addr add 192.168.1.10/24 dev <interface>
   ```

3. **Bring the interface up**:

   ```bash
   sudo ip link set <interface> up
   ```

### Set the Default Gateway

You can set the default gateway using the `ip route` command:

```bash
sudo ip route add default via 192.168.1.1
```

### Remove an Assigned IP

If you need to remove an IP address:

```bash
sudo ip addr del 192.168.1.10/24 dev <interface>
```

### View Routing Table

To inspect the routing table:

```bash
ip route show
```

## Using Network Configuration Files

### Static IP Configuration

For persistent network configurations, edit your network interface configuration files. These files vary based on the Linux distribution.

#### Debian/Ubuntu

Edit `/etc/network/interfaces`:

```plaintext
auto <interface>
iface <interface> inet static
    address 192.168.1.10
    netmask 255.255.255.0
    gateway 192.168.1.1
```

Apply changes with:

```bash
sudo systemctl restart networking
```

#### RHEL/CentOS

Edit the configuration file in `/etc/sysconfig/network-scripts/`, typically `ifcfg-<interface>`:

```plaintext
DEVICE=<interface>
BOOTPROTO=none
ONBOOT=yes
PREFIX=24
IPADDR=192.168.1.10
GATEWAY=192.168.1.1
DNS1=8.8.8.8
```

Restart the network service:

```bash
sudo systemctl restart network
```

### Dynamic IP Configuration (DHCP)

To configure a network interface to obtain an IP address via DHCP, modify the configuration file as follows:

#### Debian/Ubuntu

```plaintext
auto <interface>
iface <interface> inet dhcp
```

Apply changes:

```bash
sudo systemctl restart networking
```

#### RHEL/CentOS

```plaintext
BOOTPROTO=dhcp
ONBOOT=yes
```

Restart the service:

```bash
sudo systemctl restart network
```

## DNS Configuration

DNS settings are typically configured in `/etc/resolv.conf`. Here’s an example of setting custom DNS servers:

```plaintext
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Be aware these settings may be overwritten by network managers (like NetworkManager). For persistent DNS settings, use your network interface configuration files or NetworkManager tools.

## Using NetworkManager (GUI and Command-line)

For systems using NetworkManager:

- **GUI**: Most desktop environments provide a NetworkManager GUI for setting up network configurations.

- **Command-line with `nmcli`**: 

  View current connection:

  ```bash
  nmcli connection show
  ```

  Modify a connection's IP settings:

  ```bash
  nmcli connection modify <connection_name> ipv4.addresses 192.168.1.10/24 ipv4.gateway 192.168.1.1 ipv4.dns 8.8.8.8
  ```

  Bring up the connection:

  ```bash
  nmcli connection up <connection_name>
  ```

## Conclusion

Configuring IP settings on Linux involves various methods, from command-line utilities like `ip` and `nmcli` to editing persistent configuration files. Understanding these tools is essential for ensuring effective network communication and management.

Key points:
- `ip` command is powerful for temporary and immediate changes.
- Configuration files ensure persistent settings across reboots.
- NetworkManager offers a unified interface for network configurations, especially in desktop environments.

Experiment with these configurations in a controlled environment to master network management tasks effectively!