# **Guide IPV4**

## **1) Principe et explication**
- Chaque dispositif sur un réseau, qu'il s'agisse d'un ordinateur, d'une imprimante ou d'un routeur, a besoin d'une adresse IP pour communiquer avec d'autres dispositifs.
- L'adresse IP est essentielle pour identifier de manière unique chaque dispositif et pour acheminer les paquets de données de manière appropriée.
## **2) Composition d'une adresse IPV4**
- Une adresse IPV4 est constituée de _**32 bits**_
- Exprimée en quatre octets (par exemple, 172.16.254.1).
- Chaque octet peut varier de 0 à 255
- Il peut y avoir théoriquement 4 294 967 296 adresse IPv4 unique
### Extrait d'un paquet IP
* Rappel : Un paquet IP ne connait que lui et ses couches supérieurs, il contient : 
	* En-tête IP avec les informations purement IP
	* Section de bourrage (optionnelle)
	* Données des couches supérieurs
* La taille d'une en-tête paquet IP classique (sans options) est de 20 octets.
![IPV4_1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/IPV4_1.png)

| Composant              | Taille   | Description                                                                          |
| ---------------------- | -------- | ------------------------------------------------------------------------------------ |
| En-tête IP             | Variable | Contient toutes les métadonnées nécessaires pour le routage et la gestion du paquet. |
| Charge utile (Payload) | Variable | Les données effectivement transmises par le paquet.                                  |
### Tableau explicatif des champs d'en-tete IPv4  
|Champ|Taille|Description|
|---|---|---|
|Version|4 bits|Indique la version d'IP, IPv4 dans ce cas.|
|IHL (Internet Header Length)|4 bits|Longueur de l'en-tête en blocs de 4 octets.|
|Type of Service|8 bits|Qualité de service désirée pour le paquet (DSCP pour QoS).|
|Total Length|16 bits|Longueur totale du paquet, en-tête et charge utile incluses.|
|Identification|16 bits|Identifiant unique pour le paquet, utilisé dans la fragmentation.|
|Flags|3 bits|Contrôle la fragmentation du paquet.|
|Fragment Offset|13 bits|Position d'un fragment dans le paquet original.|
|Time to Live (TTL)|8 bits|Limite de temps ou de sauts avant que le paquet ne soit éliminé.|
|Protocol|8 bits|Indique le protocole de la couche supérieure auquel la charge utile est destinée.|
|Header Checksum|16 bits|Somme de contrôle de l'en-tête pour vérifier l'intégrité.|
|Source Address|32 bits|Adresse IP de l'expéditeur.|
|Destination Address|32 bits|Adresse IP du destinataire.|
|Options|Variable|Options supplémentaires pour la gestion des paquets; non toujours utilisées.|

## **III) Conversion binaire-décimale**
- Les adresses IPV4, bien qu'exprimées en décimales pour la commodité humaine, sont en réalité traitées en binaire par les dispositifs informatiques.
- Comprendre la conversion entre le format binaire et décimal est essentiel pour travailler avec des sous-réseaux et des masques de sous-réseau.

## **IV) Adresses spéciales**
- **Adresse réseau** : Identifie tout le réseau. Par exemple, pour le réseau 192.168.1.0/24, l'adresse réseau est 192.168.1.0.
- **Adresse broadcast** : Utilisée pour communiquer avec tous les dispositifs du réseau. Pour le réseau 192.168.1.0/24, l'adresse broadcast est 192.168.1.255.
- **Adresse de bouclage (Loopback)** : 127.0.0.1, utilisée pour tester la pile IP d'un hôte.

## **V) Classes d'adresses**

| Classe | Modèle de bit de départ | Masque de sous-réseau par défaut | Plage d'adresses  | Nombre d'adresses par réseau |
|-------|-------------------------|-----------------------------|-----------------|---------------------------|
| A     | 0                       | 255.0.0.0                   | 1.0.0.0–126.255.255.255 | 16,777,214             |
| B     | 10                      | 255.255.0.0                 | 128.0.0.0–191.255.255.255 | 65,534              |
| C     | 110                     | 255.255.255.0               | 192.0.0.0–223.255.255.255 | 254                 |
| D     | 1110                    | Aucun                      | 224.0.0.0–239.255.255.255 | Multidiffusion       |
| E     | 1111                    | Aucun                      | 240.0.0.0–255.255.255.255 | Expérimental         |

## **VI) Adresses privées**
- Ces adresses sont destinées à être utilisées à l'intérieur des réseaux privés et ne peuvent pas être routées sur Internet.
    - **10.0.0.0** - 10.255.255.255
    - **172.16.0.0** - 172.31.255.255
    - **192.168.0.0** - 192.168.255.255

## **VII) Types d'adresses**
- **Unicast** : Identifie une seule interface réseau.
- **Broadcast** : Utilisée pour envoyer des paquets à tous les dispositifs sur un réseau.
- **Multicast** : Identifie un groupe d'interfaces, permettant une communication "un vers plusieurs".

## **VIII) Subnetting et CIDR**

- **Subnetting** : Divise un réseau en sous-réseaux plus petits pour une utilisation efficace des adresses IP et une meilleure gestion du réseau.
- **CIDR (Classless Inter-Domain Routing)** : Une méthode plus moderne pour représenter les adresses IP et éliminer le besoin de classes d'adresses strictes. Exemple : 192.168.1.0/24 où "/24" représente le masque de sous-réseau.

## **IX) Épuisement des adresses IPV4**
- En raison de la croissance rapide d'Internet, le pool d'adresses IPV4 disponibles s'épuise.
- Cela a conduit à la création d'IPV6, une version plus récente du protocole Internet avec un espace d'adressage beaucoup plus grand.