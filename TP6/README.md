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
  
  
