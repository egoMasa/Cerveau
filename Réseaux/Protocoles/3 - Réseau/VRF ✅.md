## Guide sur les VRF (Virtual Routing and Forwarding)

### I) Généralités

- **Définition** : Les VRF sont des tables de routage virtuelles qui permettent de segmenter un routeur en plusieurs instances de routage, chacune étant isolée des autres. On peut le comparer à un VLAN mais de couche 3 
    
- **Applications** :
    - Création de réseaux privés virtuels (VPN) au sein d'un réseau local (LAN) ou d'un réseau étendu (WAN).
    - Isolation et séparation des clients ou des utilisateurs dans des environnements réseau partagés.
    - Augmentation de la sécurité par la prévention des accès non autorisés et l'isolement du trafic.

- **Caractéristiques** :
    - Chaque VRF dispose de sa propre table de routage.
    - Séparation des paquets basée sur la destination.
    - Possibilité de maintenir des environnements réseau privés et sécurisés au sein d'un même équipement.

### II) Fonctionnement

- **Table de Routage** : Chaque VRF possède une table de routage dédiée contenant les informations nécessaires pour acheminer les paquets destinés à cette VRF.
    
- **Routage** : Lorsqu'un paquet arrive sur un routeur, il est dirigé vers sa destination en utilisant la table de routage correspondante à la VRF déterminée.
    

### III) Système de Conjonction

1. **Route Distinguisher (RD)** :
    - C'est un identifiant unique utilisé pour distinguer les routes appartenant à différentes VRF.
    - Il garantit l'unicité des routes dans différentes VRF et évite les conflits.
    - Typiquement noté sous la forme ASN:nn, où ASN est le numéro de système autonome et nn est un nombre arbitraire.
    - Chaque VRF sur un routeur doit avoir un RD unique.

2. **Route Target (RT)** :
    - C'est un identifiant utilisé pour définir à quelles VRF les routes doivent être exportées ou d'où elles doivent être importées.
    - BGP est souvent utilisé pour propager ces informations entre VRF en utilisant les numéros ASN.
    
    a. **Route Target Import** :
    - Définit les routes qui doivent être ajoutées à la table de routage de la VRF.
    - "J'importe ce que les autres exportent."
    
    b. **Route Target Export** :
    - Définit les routes qui doivent être annoncées aux autres VRF.
    - "J'exporte ce que les autres importent."

## Configuration 
### Contexte
Supposons que nous ayons un routeur et que nous souhaitons isoler le trafic de deux départements : Marketing et Finance. Nous utiliserons VRF pour cela.
### Étape 1: Création des VRF
Nous allons créer deux VRFs : une pour le département Marketing et une autre pour le département Finance.
```
Router(config)# ip vrf Marketing
Router(config-vrf)# description VRF for Marketing Department
Router(config-vrf)# rd 1:1

Router(config)# ip vrf Finance
Router(config-vrf)# description VRF for Finance Department
Router(config-vrf)# rd 1:2
```
* Note : La commande `rd` définit le Route Distinguisher. Ici, `1:1` et `1:2` sont utilisés à titre d'exemple.

### Étape 2: Assignation des interfaces aux VRF
* Supposons que l'interface `GigabitEthernet0/1` soit utilisée par le département Marketing et `GigabitEthernet0/2` par le département Finance.
```
Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip vrf forwarding Marketing
Router(config-if)# ip address 192.168.1.1 255.255.255.0

Router(config)# interface GigabitEthernet0/2
Router(config-if)# ip vrf forwarding Finance
Router(config-if)# ip address 192.168.2.1 255.255.255.0
```
### Étape 3: Vérification
* Après avoir configuré les VRF, vous pouvez vérifier leur état.
```
Router# show ip vrf
Router# show ip route vrf Marketing
Router# show ip route vrf Finance
```


### IV) Conclusion

Les VRF offrent une manière puissante et flexible de gérer et de séparer le trafic sur un routeur. Elles permettent d'isoler différents flux de trafic, d'assurer la sécurité, et d'offrir des services différenciés sur un réseau partagé. En utilisant des identifiants uniques comme les Route Distinguishers et les Route Targets, il est possible d'assurer un routage précis et de gérer efficacement le trafic entre différentes instances VRF.