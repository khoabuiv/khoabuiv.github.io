---
layout: post
---
# Network

## Adding a static route
Use:
```
ip route add <ip address> via <ip address>
```

## Create and enforce MAC using SELinux
1. Check SELinux status:
```
sestatus
```
2. Set SELinux mode:
```
setenforce <0|1>
```
To make this persistent, change in **/etc/selinux/config** file and set:
```
SELINUX=enforcing
```
3. 

## Managing SSH
- **sshd_config** is the daemon config file to manage connection to the server
- **ssh_config** file is the ssh client configuration file. The client configuration file only has bearing on when you use the ssh command to connect to another ssh host. 

## How to enable load balancing with nginx
1. Go to /etc/nginx/sites-enabled and edit an available files:
2. Redirect traffic example:
```
server {
        listen 1111 default_server;
        listen [::]:1111 default_server;

        server_name _;

        location / {
                return 200 'app1\n';
        }
}
```
3. Load balancing example:
```
upstream backend {
        # when no load balancing method is specified, Round Robin is used
        server 127.0.0.1:1111;
        server 127.0.0.1:2222;
 }
 server {
        listen 8000 default_server;
        listen [::]:8000 default_server;
        server_name _;
        location / {
                proxy_pass http://backend; # reverse proxy to the requested url
        }
 }
```

## Managing NFS
NFS config can be found at **/etc/exports**. After making changes to the config, you need to load with **exportfs**:
```
exportfs -ra
```
Then check with **showmount**:
```
showmount -e
```

## Using SSHFS to mount remote directory
SSHFS works similar to how mount work, but remotely. It can be run as follow:
```
sudo sshfs -o <options> <remote_server>:<directory_path> <localhost_directory>
```

## Port Management:
- Use **ss** command to get all the port.

### How to block a port?
Use ufw as follow:
```
ufw enable
ufw deny <port_number>
```
Note: If you are SSHing then make sure to enable SSH before enabling ufw as follow:
```
ufw allow ssh
```
### Using UFW
Make sure to get the current localhost ip address first as follow:
```
ip addr
```
- To re-direct
```
iptables -A PREROUTING -i eth0 -t nat -p tcp --dport <original port> -j REDIRECT --to-port <destination port>
```
To block outgoing traffic:
```
ufw deny out from any to <destination ip>
```



- Find current hostname:
```
root@mariadb:~# hostname
mycomputer
```
This value is stored at **/etc/hostname**

## How to change hostname
- Persistent change:
```
hostnamectl set-hostname <hostname>
```
- Non-persistent change:
```
sudo hostname <hostname>
```

- **Network Time Protocol (NTP)**: Is a method to update and synchronize system time. NTP consists of a daemon and a protocol. Time sources are divided up into ”strata”:
    0. A special purpose time device (Atomic clock, GPS radio, etc.)
    1. Server is any NTP server connected directly to a stratum 0 source 
    2. Server is any NTP server which references a stratum n server using NTP
Lowest strata is 15 which reads from 14. NTP may function as a client, server, or a peer.


## How to set and synchronize system time using time servers
1. Install the program:
```
sudo apt-get install ntp  # for Debian/Ubuntu
sudo yum install ntp      # for CentOS/RHEL
sudo dnf install ntp      # for Fedora
```
2. Configure the /etc/ntp.conf file from:
```
pool 0.ubuntu.pool.ntp.org iburst
pool 1.ubuntu.pool.ntp.org iburst
pool 2.ubuntu.pool.ntp.org iburst
pool 3.ubuntu.pool.ntp.org iburst
```
to:
```
server 0.ubuntu.pool.ntp.org iburst
server 1.ubuntu.pool.ntp.org iburst
server 2.ubuntu.pool.ntp.org iburst
server 3.ubuntu.pool.ntp.org iburst
```
3. Restart ntp server:
```
systemctl start ntp
```

**Note**: Make sure to check **man timesyncd.conf** for help.


## How to configure the OpenSSH server and client
1. Install the package:
```
sudo apt install openssh-client
sudo apt install openssh-server
```
