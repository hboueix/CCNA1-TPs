# TP 6 - Une topologie qui ressemble un peu à quelque chose, enfin ?

## Configuration de OSPF

Nous pouvons vérifier que la configuration c'est bien passé grâce à plusieurs commandes à effectuer sur chaque routeur.  
  
------
  
**Router 1**  
  
* `show ip route` :
```
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
O       10.6.100.8/30 [110/20] via 10.6.100.2, 00:05:18, Ethernet0/0
O       10.6.100.12/30 [110/20] via 10.6.100.6, 00:05:18, Ethernet0/1
C       10.6.100.0/30 is directly connected, Ethernet0/0
O IA    10.6.101.0/30 [110/30] via 10.6.100.6, 00:05:18, Ethernet0/1
                      [110/30] via 10.6.100.2, 00:05:18, Ethernet0/0
C       10.6.100.4/30 is directly connected, Ethernet0/1
O IA    10.6.201.0/24 [110/40] via 10.6.100.6, 00:02:31, Ethernet0/1
                      [110/40] via 10.6.100.2, 00:02:32, Ethernet0/0
C       10.6.202.0/24 is directly connected, Ethernet0/2
```  
  
**Router 2**  
  
* `show ip route` :
```
Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
C       10.6.100.8/30 is directly connected, Ethernet0/1
O       10.6.100.12/30 [110/20] via 10.6.100.10, 00:08:14, Ethernet0/1
C       10.6.100.0/30 is directly connected, Ethernet0/0
O IA    10.6.101.0/30 [110/20] via 10.6.100.10, 00:08:14, Ethernet0/1
O       10.6.100.4/30 [110/20] via 10.6.100.1, 00:08:14, Ethernet0/0
O IA    10.6.201.0/24 [110/30] via 10.6.100.10, 00:05:27, Ethernet0/1
O IA    10.6.202.0/24 [110/20] via 10.6.100.1, 00:08:16, Ethernet0/0

```
