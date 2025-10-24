Lab 2 – DHCP Server Setup

Objective: Install and configure a DHCP server to automatically assign IP addresses to clients.

sudo dnf install dhcp-server -y
subnet 192.168.56.0 netmask 255.255.255.0 {
range 192.168.56.20 192.168.56.50;
option subnet-mask 255.255.255.0;
option routers 192.168.56.1;
option domain-name-servers 8.8.8.8, 8.8.4.4;
}

Starting the Service
sudo systemctl enable --now dhcpd

Firewall Allow Rule
sudo firewall-cmd --add-service=dhcp --permanent
sudo firewall-cmd --reload

This configuration allows the Fedora server to issue IP addresses dynamically to devices in the network. The DHCP range is from `192.168.56.20` to `192.168.56.50`.

