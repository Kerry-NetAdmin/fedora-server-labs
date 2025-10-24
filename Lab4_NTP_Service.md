Lab 4 – NTP Service
Objective: Configure NTP on Fedora Server to keep the system clock synchronized.

Package Installation
sudo dnf install ntp -y

 Configuration File
server 0.fedora.pool.ntp.org iburst
server 1.fedora.pool.ntp.org iburst
driftfile /var/lib/ntp/ntp.drift

Starting the NTP Service
sudo systemctl enable --now ntpd

Verifying Synchronization
systemctl status ntpd
ntpq -p

This lab configures the server to sync its time from NTP servers on the internet. This ensures accurate timekeeping, which is important for logs and other network services.
