# ReadMe for NetworkScripts

## .env.example
copy this file to .env and edit to match what you want. In the file there are the following variables

| variable | description                                                                                              |
| ---- |----------------------------------------------------------------------------------------------------------|
| eth_ip | Static ip address given to the ethernet interface if DHCP fails. Uses 192.168.0.10/24 notation           |
| eth_gw | Static gateway given to the ethernet interface if DHCP fails                                             |
| wifi_ip | Same as eth_ip but for wifi                                                                              |
| wifi_gw | Same as eth_gw but for wifi                                                                              |
| ssid | SSID to use for the wifi interface                                                                       |
| psk | PSK to match the SSID for the wifi interface                                                             |
| apn | The APN to use for the LTE interface<br/>for telstra this is "telstra.internet"<br/>for optus m2m is this "om2moptus" |
| dns | DNS servers to use for all interfaces                                                                    |

# Typical install usage
Copy all these files somewhere onto the target in a directory called `network_scripts`
In your system installer (either run as root or as a user with sudo permissions)

```bash
nohup bash -c 'network_scripts/install_packages.sh && network_scripts/init_network_profiles.sh' &
```
If you then can't connect to the device, reboot and wait 3 minutes for the emergency_ethernet profile to kick in.

If all works, run `network_scripts/emergency_ethernet.sh uninstall` to remove the emergency_ethernet failsafe

# NetworkScripts Description

## install_packages.sh
This will install ModemManager and NetworkManager on a pi.

It will copy the NetworkManager.conf.default file to /etc/NetworkManager/NetworkManager.conf and will enable and start the services

## init_network_profiles.sh
This will setup all the network profiles for the interfaces. There is a very good chance that the device will lose network connection during this process and it's worth starting it in the background to ensure that it completes
You can do that with

`nohup ./init_network_profiles.sh &`

When run it will default to ethernet enabled with dhcp and failover to static, LTE enabled and WIFI disabled.

It will also install the 'emergency_ethernet' script into cron so that if the connection fails to come up as part of init, if you reboot the device and wait 3 minutes, a simple DHCP ethernet networking profile will be written.

If the emergency_ethernet profile is used, manual processes will be needed to fix it.

## emergency_ethernet.sh
This is not usually meant to be run manually. This script takes a single required parameter which is either

### emergency_ethernet.sh install
Install the emergency ethernet script in the root users cron to run at reboot

### emergency_ethernet.sh run
This is only meant to be run from cron and will wait 3 minutes before wiping all network settings in NetworkManager and setting up a basic DHCP client IPv4 profile on eth0

### emergency_ethernet.sh uninstall
This will remove the emergency_ethernet script from cron and kill any emergency_ethernet processes running.

To be used after an init_network_profiles.sh invocation and networking has been proved to work.

## disable_all_radio.sh
Will disable LTE and WIFI, using 'radio off' in NetworkManager and rfkill for WIFI

## disable_ethernet.sh
Will disable the ethernet connection profiles and set them to not autoconnect

## disable_firewall.sh

Will disable the UFW firewall and reset all rules

## disable_ipv6.sh

Will disable ipv6 at a kernel boot level

## disable_lte.sh

Will disable the LTE connection profile, set to not autoconnect and kill the radio

## disable_wifi.sh

Will disable the Wifi connection profiles, set to not autoconnect and kill the radio

## enable_all_radio.sh

Opposite to disable_all_radio.sh

## enable_ethernet_dhcp.sh

Will enable the ethernet interface as a DHCP client with no static IP failover

## enable_ethernet_failover.sh

Will enable the ethernet interface as a DHCP client with a static IP failover if DHCP doesn't work within a couple of minutes

## enable_ethernet_static.sh

Will enable the ethernet interface with a static IP only

## enable_firewall.sh

Will install and enable UFW firewall with just SSH and HTTPS ports open from the outside

## enable_ipv6.sh

Will enable ipv6 in the kernel

## enable_lte.sh

Will enable the LTE radio and enable the connection profile and autoconnect

## enable_wifi_dhcp.sh

Will enable the Wifi radio and enable the DHCP client only connection profile and autoconnect

## enable_wifi_failover.sh

Will enable the Wifi radio and enable the DHCP client connection profile with failover to static IP and autoconnect (same as enable_ethernet_failover.sh)

## enable_wifi_static.sh

Will enable the Wifi radio and enable the interface with a static IP only

## install_redfin_proxy