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
[root@client1 ~]# dhclient -v -r
Internet Systems Consortium DHCP Client 4.2.5
Copyright 2004-2013 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp0s8/08:00:27:9d:7e:b9
Sending on   LPF/enp0s8/08:00:27:9d:7e:b9
Listening on LPF/enp0s3/08:00:27:06:80:31
Sending on   LPF/enp0s3/08:00:27:06:80:31
Sending on   Socket/fallback
DHCPRELEASE on enp0s3 to 10.6.201.11 port 67 (xid=0x53c11051)
[root@client1 ~]# dhclient -v
Internet Systems Consortium DHCP Client 4.2.5
Copyright 2004-2013 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp0s8/08:00:27:9d:7e:b9
Sending on   LPF/enp0s8/08:00:27:9d:7e:b9
Listening on LPF/enp0s3/08:00:27:06:80:31
Sending on   LPF/enp0s3/08:00:27:06:80:31
Sending on   Socket/fallback
DHCPDISCOVER on enp0s8 to 255.255.255.255 port 67 interval 5 (xid=0x517a0807)
DHCPDISCOVER on enp0s3 to 255.255.255.255 port 67 interval 8 (xid=0x5f2ddd66)
DHCPREQUEST on enp0s3 to 255.255.255.255 port 67 (xid=0x5f2ddd66)
DHCPOFFER from 10.6.201.11
DHCPACK from 10.6.201.11 (xid=0x5f2ddd66)
bound to 10.6.201.50 -- renewal in 261 seconds.
[root@client1 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:06:80:31 brd ff:ff:ff:ff:ff:ff
    inet 10.6.201.50/24 brd 10.6.201.255 scope global dynamic enp0s3
       valid_lft 595sec preferred_lft 595sec
    inet6 fe80::a00:27ff:fe06:8031/64 scope link
       valid_lft forever preferred_lft forever
```


### 4. Serveur DNS





### 5. Serveur NTP
  
