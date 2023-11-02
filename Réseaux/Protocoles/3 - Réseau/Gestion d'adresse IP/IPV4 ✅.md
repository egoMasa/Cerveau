# **Guide IPV4**

## **I) Principe et explication**

- Chaque dispositif sur un réseau, qu'il s'agisse d'un ordinateur, d'une imprimante ou d'un routeur, a besoin d'une adresse IP pour communiquer avec d'autres dispositifs.
- L'adresse IP est essentielle pour identifier de manière unique chaque dispositif et pour acheminer les paquets de données de manière appropriée.
- IPV4 est la quatrième version du protocole Internet, d'où le "V4".

## **II) Composition d'une adresse IPV4**

- Une adresse IPV4 est constituée de _**32 bits**_, généralement exprimée en quatre octets (par exemple, 172.16.254.1).
- Chaque octet peut varier de 0 à 255, offrant une vaste gamme d'adresses IP possibles.

(Note : Il serait bon de remplacer ou d'expliquer les images collées, car je ne peux pas voir les images mentionnées.)

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

## **X) Conclusion**

L'IPV4 a été un pilier de l'Internet depuis sa création, permettant la communication entre des milliards de dispositifs. Avec la croissance continue d'Internet, l'importance de comprendre IPV4 demeure, même si la transition vers IPV6 est en cours.
