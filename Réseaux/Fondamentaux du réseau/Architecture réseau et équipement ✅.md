# Guide Architecture réseau et équipements

# I) Types de réseau

Les réseaux informatiques peuvent être classés en fonction de leur portée géographique, de leur échelle ou de la manière dont ils sont construits et gérés. La taille et la portée sont souvent les principales caractéristiques distinctives. Voici une description de certains types courants de réseaux :

- _**Réseau LAN (Local Area Network)**_ :
    - **Définition** : Il s'agit d'un réseau qui couvre une petite zone géographique, comme une maison, un bureau ou un bâtiment.
    - **Caractéristiques** : Les LAN offrent généralement des débits de données élevés et ont un nombre limité de stations ou de dispositifs connectés. Ils utilisent généralement des technologies comme Ethernet ou Wi-Fi.
    - **Usage** : Typiquement utilisé pour partager des ressources comme des fichiers ou des imprimantes entre utilisateurs finaux.

- _**Réseau WAN (Wide Area Network)**_ :
    - **Définition** : Un réseau qui s'étend sur une vaste zone géographique, telle qu'une ville, un pays ou même le monde entier.
    - **Caractéristiques** : Les WAN sont généralement plus lents que les LAN en termes de débit, principalement en raison de la grande distance que les données doivent parcourir et de la complexité de la gestion d'un grand nombre de connexions et de transmissions. Les WAN utilisent souvent des technologies comme MPLS, Frame Relay ou des liaisons louées.
    - **Usage** : Un exemple typique de WAN est Internet. Cependant, les entreprises utilisent également des WAN pour interconnecter leurs bureaux dispersés géographiquement.

- _**Réseau CAN (Campus Area Network)**_ :
    - **Définition** : Un réseau qui couvre une zone plus grande qu'un LAN mais reste confinée à un espace géographique spécifique, comme un campus universitaire ou un parc d'entreprise.
    - **Caractéristiques** : Les CAN sont souvent composés de plusieurs bâtiments ou structures interconnectés par des liaisons haut débit. Ils peuvent utiliser des technologies similaires à celles des LAN mais à une échelle plus grande.
    - **Usage** : Typiquement utilisé par les universités, les grandes entreprises ou les institutions qui nécessitent une connectivité haute vitesse entre plusieurs bâtiments sur un site spécifique.

- _**Réseau PAN (Personal Area Network)**_ :
    - **Définition** : Il s'agit d'un réseau centré autour d'un individu, souvent dans un espace très restreint, comme une pièce ou un bureau.
    - **Caractéristiques** : Les PAN sont généralement utilisés pour interconnecter des appareils personnels tels que téléphones, ordinateurs portables, écouteurs et montres intelligentes. La technologie Bluetooth est un exemple courant utilisé dans les PAN.
    - **Usage** : Les PAN sont principalement utilisés pour les communications à courte portée, la synchronisation des appareils et le partage de données entre les appareils personnels.

- _**Réseau MAN (Metropolitan Area Network)**_ :
    - **Définition** : Un réseau qui couvre une zone géographique plus grande qu'un LAN ou un CAN, mais plus petite qu'un WAN, généralement une ville ou une région métropolitaine.
    - **Caractéristiques** : Les MAN sont conçus pour fournir une connectivité dans une région métropolitaine et peuvent servir de pont entre plusieurs LAN pour former un réseau plus grand. Ils peuvent utiliser des technologies comme Ethernet ou ATM.
    - **Usage** : Les MAN sont souvent utilisés par les gouvernements locaux ou les fournisseurs de services pour offrir des services de connectivité à l'échelle de la ville.

# II) Equipements réseau

## Routeurs
- **Description** :
    - Un routeur est un équipement réseau qui relie différents segments ou réseaux. Il opère principalement à la couche 3 (couche réseau) du modèle OSI et est responsable de l'acheminement des paquets d'informations d'un réseau à un autre en utilisant la meilleure voie possible.
- **Fonctionnement** :
    - Le routeur utilise des tables de routage pour déterminer le chemin le plus efficace pour acheminer les paquets. Il prend en compte l'adresse IP de destination pour prendre ses décisions de routage.
- **Avantages & Inconvénients** :
    - **Avantages** : Permet la communication entre différents sous-réseaux, peut filtrer le trafic en fonction des adresses IP, et offre des capacités avancées comme le NAT (Network Address Translation) ou le VPN.
    - **Inconvénients** : Plus complexe à configurer qu'un simple switch, peut nécessiter une mise à jour régulière de ses tables de routage.

## Switchs L2 (commutateur)
- **Description** :
    - Un switch de niveau 2 fonctionne principalement à la couche 2 (couche de liaison de données) du modèle OSI. Il utilise les adresses MAC pour acheminer les paquets au sein d'un réseau local (LAN).
- **Fonctionnement** :
    - Lorsqu'un paquet arrive sur un port, le switch regarde l'adresse MAC de destination et l'achemine vers le port correspondant. Il construit et gère une table MAC pour savoir quel appareil est connecté à quel port.
- **Avantages & Inconvénients** :
    - **Avantages** : Réduit les collisions sur un réseau en segmentant les domaines de collision, offre une bande passante dédiée pour chaque port, et peut soutenir des configurations VLAN.
    - **Inconvénients** : Ne peut pas segmenter les domaines de diffusion (ce qui pourrait être souhaité pour des raisons de sécurité ou de performance).

## Switchs L3 

- **Description** :
    - Un switch de niveau 3, souvent appelé switch de routage, fonctionne à la fois aux couches 2 et 3 du modèle OSI. Il combine les fonctionnalités d'un switch et d'un routeur.
- **Fonctionnement** :
    - En plus de la commutation basée sur les adresses MAC, il peut aussi acheminer le trafic basé sur les adresses IP, tout comme un routeur.
- **Avantages & Inconvénients** :
    - **Avantages** : Offre à la fois des fonctions de commutation et de routage, permet une segmentation plus poussée du réseau, et peut améliorer les performances en effectuant des opérations de routage à des vitesses de commutation.
    - **Inconvénients** : Plus coûteux que les commutateurs traditionnels de niveau 2 et peut nécessiter une configuration plus complexe.
## Hub (concentrateur)
- **Description :**
    - Un hub est un dispositif simple qui relie plusieurs segments d'un réseau local (LAN). C'est un appareil de couche 1 (couche physique) du modèle OSI.
- **Fonctionnement :**
    - Lorsqu'un paquet arrive sur l'un des ports du hub, celui-ci le duplique et l'envoie à tous les autres ports. C'est pour cette raison qu'on le considère souvent comme un équipement "non intelligent".
- **Avantages & Inconvénients :**
    - **Avantage :** Simplicité et coût faible.
    - **Inconvénients :** Augmente le trafic sur le réseau (puisqu'il transmet les paquets à tous les dispositifs), ne filtre pas les collisions, et ne convient pas aux grands réseaux.
## Répéteur
- **Description :**
    - Un répéteur est un équipement de couche 1 (couche physique) du modèle OSI conçu pour étendre la portée d'un signal électrique ou optique dans un réseau.
- **Fonctionnement :**
    - Il reçoit un signal, l'amplifie et le transmet ensuite sur le segment suivant du réseau. En amplifiant le signal, il permet d'étendre la distance sur laquelle le signal peut voyager sans dégradation.
- **Avantages & Inconvénients :**
    - **Avantage :** Prolonge la portée du signal dans un réseau.
    - **Inconvénients :** Peut propager le bruit avec le signal, ne filtre pas le trafic réseau, et sa capacité à étendre un réseau est limitée (on ne peut pas simplement chaîner de nombreux répéteurs pour étendre indéfiniment un réseau).

## Firewall 
- **Description :**
    - Un pare-feu est un dispositif de sécurité réseau qui surveille et filtre le trafic entrant et sortant selon un ensemble de règles de sécurité définies. Il peut exister sous forme de logiciel ou d'équipement dédié.
- **Fonctionnement :**
    - Le pare-feu analyse le trafic réseau et prend des décisions sur l'autorisation ou le blocage des paquets en fonction de ses règles de sécurité. Il peut se baser sur des adresses IP, des ports, des protocoles, ou d'autres critères.
- **Avantages & Inconvénients :**
    - **Avantages :** Fournit une première ligne de défense contre les menaces externes, permet de définir et de contrôler les politiques de sécurité du réseau, et peut offrir d'autres fonctionnalités telles que le VPN, l'inspection profonde des paquets, etc.
    - **Inconvénients :** Peut représenter un goulot d'étranglement s'il n'est pas correctement dimensionné pour le trafic réseau, nécessite une configuration et une gestion soignées pour éviter de bloquer le trafic légitime ou de laisser passer le trafic malveillant.

# III) Topologie réseau

### Topologie physique

La topologie physique désigne l'arrangement physique des composants d'un réseau et la manière dont ils sont connectés. Voici quelques topologies courantes:

**1) Bus :**
- Tous les appareils sont connectés à un seul câble réseau, qui commence et se termine par des terminateurs.
- La vitesse est limitée en raison de la nature de la topologie.
- Utilise la méthode d’accès CSMA/CD (Carrier Sense Multiple Access with Collision Detection) : une machine veut communiquer écoute le réseau. Si une autre machine émet, elle attend; sinon, elle commence à émettre.
- Les collisions sont possibles, réduisant l'efficacité.

**2) Étoile :**
- Tous les appareils sont connectés à un point central comme un commutateur, un routeur ou un concentrateur.
- Si le dispositif central tombe en panne, le réseau entier est affecté.
- La collision est gérée par le dispositif central, offrant une meilleure performance comparée à la topologie bus.

**3) Mesh (Maillée) :**
- Chaque appareil est connecté à tous les autres appareils du réseau.
- Offre une haute disponibilité et une redondance, mais est coûteux en termes de câblage et de configuration.
- Est utilisée principalement dans des scénarios où la disponibilité est cruciale.

**4) Anneau :**
- Les appareils sont connectés en cercle.
- Utilise un "jeton" pour permettre à un seul appareil de communiquer à la fois, évitant ainsi les collisions.
- Si un appareil ou une connexion échoue, cela peut affecter le réseau entier.

**5) Hybride :**
- Combinaison de deux topologies ou plus pour répondre à des besoins spécifiques.
- Par exemple, une topologie en étoile combinée avec une topologie en anneau.

### Topologie logique

La topologie logique représente le chemin suivi par les données lorsqu'elles transitent à travers le réseau, indépendamment de l'architecture physique sous-jacente. Cela se concentre davantage sur le mode de transmission et de réception des informations plutôt que sur la manière dont les appareils sont connectés physiquement.

**Points clés :**

- **Différence fondamentale :** Alors que la topologie physique se préoccupe de la manière dont les appareils sont matériellement connectés (par exemple, par des câbles ou sans fil), la topologie logique s'intéresse à la manière dont les données sont effectivement transmises dans ce réseau.
    
- **Protocoles et modes :** Les topologies logiques sont souvent définies par des protocoles réseau. Par exemple, Ethernet utilise une topologie logique bus, même si physiquement il peut être structuré comme une étoile.
    
- **Indépendance :** La topologie logique peut être différente de la topologie physique. Par exemple, un réseau en étoile sur le plan physique peut fonctionner comme un bus sur le plan logique, en fonction du protocole utilisé.
    

**En résumé :** La topologie physique décrit la conception et la structure du réseau, comment les différents composants sont connectés. En revanche, la topologie logique décrit le chemin que les données empruntent lorsqu'elles se déplacent à travers le réseau, indépendamment de cette structure physique. C'est la manière dont les informations circulent, dictée par les protocoles et les méthodes de transmission utilisés.

