# TP 6 - Une topologie qui ressemble un peu à quelque chose, enfin ?

## Configuration de OSPF

Nous pouvons vérifier que la configuration c'est bien passé grâce à un `ping` et un `traceroute`:  
    
![Traceroute](./images/traceroute.PNG)  
  
## Let's end this properly

### 1. NAT : accès internet

On peut vérifier que le NAT est activé en effectuant un `curl 8.8.8.8` sur chacune des machines :  
  
![Curl](./images/curl.PNG)  
  
### 2. Un service d'infra

Notre serveur web installé, on peut y accèder depuis *client1* avec un `curl server1`:  
  
![Curl nginx](./images/curl_nginx.PNG)  
  
### 3. Serveur DHCP

Aprés installation du serveur DHCP et modification du fichiers */etc/dhcp/dhcpd.conf*, nous pouvons utiliser notre serveur DHCP :

```
[root@dhcp ~]# dhclient -v -r                                   # Lâche le bail DHCP (DHCPRELEASE)
Internet Systems Consortium DHCP Client 4.2.5
Copyright 2004-2013 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp0s8/08:00:27:81:f2:12
Sending on   LPF/enp0s8/08:00:27:81:f2:12
Listening on LPF/enp0s3/08:00:27:11:9f:9e
Sending on   LPF/enp0s3/08:00:27:11:9f:9e
Sending on   Socket/fallback
DHCPRELEASE on enp0s3 to 10.6.201.11 port 67 (xid=0x30056d2e)
[root@dhcp ~]# dhclient -v                                       # Redemande une IP (DORA)
Internet Systems Consortium DHCP Client 4.2.5
Copyright 2004-2013 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp0s8/08:00:27:81:f2:12
Sending on   LPF/enp0s8/08:00:27:81:f2:12
Listening on LPF/enp0s3/08:00:27:11:9f:9e
Sending on   LPF/enp0s3/08:00:27:11:9f:9e
Sending on   Socket/fallback
DHCPDISCOVER on enp0s8 to 255.255.255.255 port 67 interval 4 (xid=0x60f9670)
DHCPDISCOVER on enp0s3 to 255.255.255.255 port 67 interval 3 (xid=0x2a7dfd4)
DHCPREQUEST on enp0s3 to 255.255.255.255 port 67 (xid=0x2a7dfd4)
DHCPOFFER from 10.6.201.11
DHCPACK from 10.6.201.11 (xid=0x2a7dfd4)
bound to 10.6.201.51 -- renewal in 238 seconds.
[root@dhcp ~]# ip a                                                 # On vérifie
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:11:9f:9e brd ff:ff:ff:ff:ff:ff
    inet 10.6.201.51/24 brd 10.6.201.255 scope global dynamic enp0s3
       valid_lft 591sec preferred_lft 591sec
    inet6 fe80::a00:27ff:fe11:9f9e/64 scope link

```


### 4. Serveur DNS





### 5. Serveur NTP
  
