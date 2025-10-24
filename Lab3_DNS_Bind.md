Lab 3 – DNS Server (BIND)

Objective: Configure a DNS server using BIND to resolve hostnames inside the local network.

Package Installation
sudo dnf install bind bind-utils -y

Main Configuration File
Location: `/etc/named.conf'
conf
options { 
    listen-on port 53 {192.168.56.10; };
    allow-query { 192.168.56.0/24; };
};
zone "classroom.local" IN {
    type master;
    file "/var/named/classroom.local.zone";
};

Zone File
$TTL 86400
@   IN  SOA ns1.classroom.local. admin.classroom.local. (
        2025100201 ; Serial
        3600       ; Refresh
        1800       ; Retry
        604800     ; Expire
        86400 )    ; Minimum TTL
@    IN  NS   ns1.classroom.local.
@    IN  A    192.168.56.10
www  IN  A    192.168.56.20
mail IN  A    192.168.56.30

Start Service and Open Firewall
sudo systemctl enable --now named
sudo firewall-cmd --add-service=dns --permanent
sudo firewall-cmd --reload

Testing DNS
dig classroom.local
dig www.classroom.local

Short Explanation

In this lab, I created a local DNS zone called classroom.local and pointed it to the server IP 192.168.56.10. After starting the BIND service, I tested name resolution successfully using the dig command.
