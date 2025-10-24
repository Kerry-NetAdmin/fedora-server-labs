# Lab 1 – Network Configuration

Objective: Set a static IP address on Fedora Server and verify network connectivity.

## Network Details Used
- IP Address: 192.168.56.10
- Gateway: 192.168.56.1
- DNS Resolver: 8.8.8.8

Commands Used
nmcli connection show
ip addr show
nmcli connection add con-name "StaticConnection" ifname enp0s3 type ethernet ip4 192.168.56.10/24 gw4 192.168.56.1
nmcli connection modify "StaticConnection" ipv4.dns "8.8.8.8"
nmcli connection up "StaticConnection"
ip addr show
ping 8.8.8.8

In this lab I configured a static IP using `nmcli` instead of DHCP. After applying the config, I confirmed the network was working.
