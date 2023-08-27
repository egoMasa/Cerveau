# **Guide Adressage IPV6**

## **I) Introduction et principes fondamentaux**

- **IPv6** a été développé pour répondre à la pénurie d'adresses IPV4, principalement en raison de la croissance rapide d'Internet et du nombre croissant d'appareils connectés.
- Une adresse IPv6 est composée de _**128 bits**_, contrairement à IPv4 qui en comporte _**32**_. Cette taille accrue offre un espace d'adressage presque illimité.

## **II) Structure d'une adresse IPv6**

- Une adresse IPv6 typique est constituée de huit groupes de quatre chiffres hexadécimaux, comme 
```
A524:72D3:2C80:DD02:0029:EC7A:002B:EA73 = 8 champs
 16   16   16   16   16   16   16   16  
 16   32   48   64   80   96   112  128
```
- Elle est divisée entre le préfixe réseau (partie du réseau) et l'identifiant de l'interface (partie hôte).

## **III) Caractéristiques clés d'IPv6**

- **Autoconfiguration** : Les appareils peuvent se configurer automatiquement en utilisant le protocole _**SLAAC**_ (Stateless Address Autoconfiguration).
- Avec IPv6, la nécessité du **NAT** (Network Address Translation) est réduite car chaque appareil peut avoir une adresse unique.
- IPv6 a un en-tête simplifié pour une efficacité accrue.
- L'**ARP** (Address Resolution Protocol) a été remplacé par le **NDP** (Neighbor Discovery Protocol) dans IPv6.
- Pas de **broadcast** en IPv6. Au lieu de cela, le multicast et l'anycast sont utilisés.

## **IV) Types d'adresses**

### Unicast 
- _**Unique Local**_
	- Adresses privées non routable sur Internet
	- Exemple : _**FC00::/7**_
- _**Globale Unicast (GUA)**_
	- IP publique routable sur Internet
	- Plusieurs niveau d'encapsulation de réseau via le masque (faible = générale)
		- /3 = IANA (Autorité responsable)
		- /23 = RIR (Région)
		- /32 = LIR (Villes)
		- /48 = Sites (Immeuble)
		- /64 = Sous réseau (Etage)
	- Exemple : _**2000::/3**_
- _**Link-Local (LLA)**_
	- IP sur cable
	- Utilisée pour les communications sur le même segment réseau que l'interface de destination.
	- Exemple : _**FE80::/10**_
- _**Loopback**_
	- Exemple : _**::1/128**_
### Multicast**_ (One to Many)
- Adresse qui permet à un paquet de données d'être envoyé à un groupe de dispositifs sur un réseau. Les dispositifs qui font partie du groupe peuvent recevoir les paquets de données en fonction de leur adhésion au groupe.
- Well-Known Multicast Adresseses (FF00::/8)
	- FF02::1 : All IPv6 devices
	- FF02::2 : All IPv6 routers
	- FF02::5 : All OSPFv3 Routers
	- FF02::6 : All OSPFv3 DR Routers
	- FF02::9 : All RIP routers
	- FF02::A : All EIGRP Routers
### Anycast (IP de Groupe)
- Assignée à plusieurs interfaces réseau sur différents dispositifs, permettant à un paquet de données d'être envoyé au dispositif le plus proche géographiquement.
## V) Adresses réservées

- Route par défaut = _**::/0**_
- Non spécifié = _**::/128**_
- Loopback = _**::1/128**_
- Link-local unicast = _**FE80::/10**_
- Multicast = _**FF00::/8**_
- Globale unicast : Les autres

## **VI) Simplification des adresses**
- On peut barrer une ligne de zero 1 fois seulement
- Si autre champs de zero il deviennent 1 zero pour chaque
- On peut barrer un zero si il est au début

```
2031:0000:130F:0000:0000:09C0:876A:130B
2031:0:130F::9C0:876A:130B
```

## VII) Adressage et attribution
* L'attribution d'adresses peut se faire manuellement ou automatiquement via **SLAAC** ou **DHCPv6**.
### Manuelle via format IEEE (EUI-64)

- On prend l'adresse MAC (48bits, 6octets)
- On prend le premier octets (2 premier chiffre)
- On passe de 0 à 1 le second bits de droite
- On rajoute 2 octets de bourrage FF,FE entre le 3ème octet et le 4ème

```
00:21:86:10:CE:84
02:21:86:FF:FE:10:CE:84	
```


## **VII) Transition IPv4 vers IPv6**

- Dans le monde réel, la transition complète vers IPv6 prend du temps. Plusieurs mécanismes de transition existent pour permettre la coexistence d'IPv4 et IPv6:
    - **Dual Stack**: Les dispositifs fonctionnent simultanément avec IPv4 et IPv6.
    - **Tunnels**: Les paquets IPv6 sont "enveloppés" dans des paquets IPv4 pour être transportés.
    - **Traduction**: Traduction des paquets IPv4 en paquets IPv6 et vice-versa.

## **VIII) Sécurité en IPv6**

- Avec IPv6, la sécurité est intégrée à la conception. Le protocole **IPsec**, qui était optionnel dans IPv4, est obligatoire dans IPv6.
- Les dispositifs doivent implémenter IPsec pour être conformes à la norme IPv6, ce qui rend la communication plus sécurisée par défaut.

## **IX) Conclusion**

Alors que IPv4 a été la colonne vertébrale de l'Internet pendant des décennies, IPv6 est l'avenir, avec son vaste espace d'adressage et ses améliorations intégrées. Comprendre IPv6 est essentiel pour toute personne travaillant dans le domaine des réseaux et des technologies de l'information.

# Configuration IPV6
### **SLAAC (Stateless Address Autoconfiguration)**

SLAAC est une méthode pour attribuer des adresses IPv6 sans nécessiter un serveur DHCP. Le dispositif crée automatiquement sa propre adresse IPv6 en utilisant son adresse MAC et les annonces du routeur du réseau sur lequel il se trouve.

### Configuration automatique via SLAAC/DHCPv6 sur les routeurs Cisco**

#### **1. Activer la transmission IPv6**

```
`R(config)# ipv6 unicast-routing`
```
Cela active le routage IPv6 sur le routeur.

#### **2. Activer IPv6 sur une interface spécifique**
```
R(config)# interface G0/0/0 
R(config-if)# ipv6 enable
```
Cette commande active IPv6 sur l'interface spécifiée (dans ce cas, G0/0/0).

#### **3. Attribuer une adresse IPv6 à une interface**

Si vous avez une adresse IPv6 spécifique que vous souhaitez attribuer à une interface :
```
R(config)# interface [NOM_INTERFACE] 
R(config-if)# ipv6 address [PREFIXE/MASQUE]
```
#### **4. Attribuer une adresse lien-local à une interface**

Les adresses lien-local sont utilisées pour les communications sur le même segment réseau que l'interface de destination.
```
R(config)# interface [NOM_INTERFACE]
R(config-if)# ipv6 address FE80::[VOTRE_VALEUR] link-local  
```

### DHCPv6
#### Configurer DHCPv6 sur le routeur**

Si vous souhaitez utiliser DHCPv6 pour attribuer des adresses plutôt que SLAAC :

1. Définissez une plage d'adresses pour DHCPv6 :
```
R(config)# ipv6 dhcp pool [NOM_DU_POOL] 
R(dhcp-config)# address prefix [PREFIXE/MASQUE]
```
2. Liez cette plage d'adresses à une interface spécifique :
```
R(config)# interface [NOM_INTERFACE] 
R(config-if)# ipv6 dhcp server [NOM_DU_POOL]
```

## **Commandes utiles pour le dépannage et la surveillance**

1. **Afficher la configuration IPv6 d'une interface**
```
show ipv6 interface [NOM_INTERFACE]
```
2. **Afficher la table de routage IPv6**
```
show ipv6 route
```

3. **Afficher les voisins découverts**
```
show ipv6 neighbors
```