## 1) Physique 
### Nombre de salle & Nombre de prises
* La première étape est de définir le nombre de salles présent dans le bâtiment
 et le nombre équipements par salles
 * Les équipements généralement présent sont : PC Fixe, Téléphone fixe, Imprimantes, Points d'accès sans fils, Projecteur et autres équipements qui auraient besoins d'une liaison filaire au switch.
### Placement/logique des salles de raccordement
* Il faut définir selon les besoins une ou plusieurs salles de raccordement ou seront présent les switches de couches accès auquel se reliront l'ensemble des équipements et terminaux. 
* Généralement une salles de raccordement par salle est suffisant et agira comme un concentrateur
* Les équipements et terminaux peuvent être alimentés soit via PoE ou via prises électriques si le réseau est fait pour (vérifier distance maximale PoE)
* Si un datacenter est présent dans le réseau, il est recommandé pour des questions de concentration des équipements et simplicité de gestion de raccorder l'ensemble des salles de raccordement au datacenter. 
### Plan physique 3D
* Afin d'avoir une vision réaliste de la gestion du raccordement et des points d'entrée et de sortie des câbles, une modélisation simpliste peut-être rendu et est grandement apprécié par les clients
* Pour cela différent logiciel existe généralement utilisé en architecture de bâtiment permettent d'obtenir des rendus réaliste comme ***AutoDesk Revit***
![[Pasted image 20240416142320.png]]
## 2) Réseau
### Bases
#### Différents modèle réseau d'entreprise (Tier 2 Tier 3)
* En conception d'architecture réseau, souvent 2 modèle type sont utilisés afin d'obtenir un ensemble scalable et offrant une liberté de configuration et de hautes performances, on parle de modèle Tier 2 et modèle Tier 3 
* ***Niveau Core (Cœur)*** : Cette couche est le point central de l'architecture réseau Tier 3, assurant une connectivité à haut débit entre les différents commutateurs de distribution. Les équipements de cette couche sont sélectionnés pour leur performance et leur capacité à gérer de grands volumes de trafic avec une latence minimale. La logique de placement vise à optimiser la connectivité, en permettant une communication rapide et efficace à travers tout le réseau. 
- ***Niveau Distribution*** : Les commutateurs de distribution agissent comme des intermédiaires entre la couche core et la couche access. Ils appliquent des politiques réseau, effectuent le routage interVLAN, et peuvent offrir des services avancés tels que la qualité de service (QoS) et le filtrage de sécurité. Le placement est conçu pour minimiser les chemins de données et simplifier le contrôle du trafic entrant et sortant des différentes zones du réseau. 
- ***Niveau Access*** : À la base de la hiérarchie, la couche access relie les dispositifs finaux, comme les ordinateurs, les imprimantes et les points d'accès sans fil, au réseau. Les commutateurs d'accès sont choisis pour leur capacité à fournir une connectivité fiable aux utilisateurs finaux et leur facilité de gestion.
#### Logique de câblage entre les couches 
1. **Couche d'accès (Access Layer)**:
    - **Pas de lien direct entre les switchs de niveau 2 (SW2) de la couche d'accès** : Ceci évite la création de boucles de réseau au niveau de la couche d'accès, ce qui est crucial pour la stabilité du réseau. Les protocoles STP (Spanning Tree Protocol) sont généralement utilisés pour gérer les boucles potentielles, mais il est préférable de ne pas créer de connexions directes inutiles qui compliqueraient la topologie du réseau.
    - **Les SW2 d'accès peuvent être reliés à chaque switch de niveau 3 (SW3) de distribution** : Cette configuration assure une redondance et une disponibilité élevées. Chaque switch d'accès a des liens montants vers plusieurs switchs de distribution, permettant une continuité de service même en cas de défaillance d'un lien ou d'un switch.
2. **Couche de distribution (Distribution Layer)**:
    - **Les SW3 de distribution doivent être impérativement reliés à chaque SW3 de la couche core** : Cela garantit que la couche de distribution est correctement intégrée à la couche core pour un routage efficace et pour maintenir les performances du réseau. Cette interconnexion offre également une redondance, car si un switch de la couche core échoue, le switch de distribution peut toujours acheminer le trafic via un autre switch core.
    - **Pas de lien direct entre les SW3 de la couche de distribution** : Éviter de connecter directement les switchs de distribution entre eux aide à simplifier la gestion du réseau et à réduire le risque de boucles de routage.
3. **Couche core (Core Layer)**:
    - **Lien direct entre les SW3 de la couche core** : Les switchs de la couche core doivent être interconnectés pour fournir un chemin de haute capacité et faible latence à travers le réseau. Cela permet de gérer efficacement le trafic entre les différentes zones du réseau et de maintenir des performances optimales. Les connexions directes entre les switchs core facilitent également la mise en œuvre de protocoles de redondance comme le protocole VRRP (Virtual Router Redundancy Protocol) ou HSRP (Hot Standby Router Protocol) pour assurer la haute disponibilité.
#### Gestion bande passante 
Dans une architecture réseau en trois couches typique (core, distribution et access), la répartition de la bande passante et la nécessité de débits élevés varient significativement entre les couches :

| Couche            | Besoins en débit | Fonctions principales                                        | Exemples de vitesses de liaison    |
|-------------------|------------------|-------------------------------------------------------------|------------------------------------|
| **Core (Cœur)**   | Très élevé       | Routage à haute vitesse, redondance, interconnexion réseau  | 10 Gbps, 40 Gbps, 100 Gbps         |
| **Distribution**  | Élevé            | Aggregation des liens, routage inter-VLAN, sécurité         | 1 Gbps, 10 Gbps                    |
| **Accès**         | Modéré           | Connexion des dispositifs utilisateurs, politiques de base  | 100 Mbps, 1 Gbps                   |


#### Architecture standard
![[Pasted image 20240416144552.png]]
#### Architecture avancée avec redondance de lien (EtherChannel)
![[Pasted image 20240416142529.png]]

#### Architecture avancée avec sécurité (Firewall)
![[Pasted image 20240416145006.png]]
#### Plan d'adressage IPv4 (Plage et sous réseau)
* Afin d’obtenir un plan d’adressage hiérarchique capable de répondre au besoin du client, nous avons appliqué la méthode d’adressage suivante : 
1. ***Prédire le nombre d’IP nécessaire*** : Évaluer le nombre total d'appareils qui auront besoin d'une adresse IP, en incluant les serveurs, les postes de travail, les périphériques réseau et les appareils mobiles.
2. ***Définir le masque nécessaire*** : Choisir un masque de sous-réseau qui offre suffisamment d'adresses pour le nombre prévu d'hôtes, tout en laissant de la place pour la croissance future. 
3. ***Choisir une plage d’adresse privée*** : Choisir entre une des 3 plages d’adresses privées standard parmi les suivantes : 

| Réseau         | Nombre d'hôtes max | Utilisation                                          |
|----------------|--------------------|------------------------------------------------------|
| `10.x.x.x/8`   | 16 777 216         | Réseau très étendu sur une grande zone géographique, multisite, etc. |
| `172.16.x.x/12`| 1 048 576          | Réseau de taille moyenne mais avec un grand espace   |
| `192.168.x.x/16`| 65 536            | Réseau plus petit                                    |

4. ***Faire un premier VLSM (Variable Length Subnet Masking)*** : Subdiviser l'adresse de réseau principal en sous-réseaux pour les différents bâtiments, en allouant des espaces d'adresses IP en fonction de leurs besoins spécifiques. 
5. ***Faire un second VLSM*** : Réaliser une subdivision supplémentaire des sous-réseaux pour des groupes plus petits, des zones spécialisées ou des segments sécurisés, afin de finaliser les plans de l'adressage IP. 
#### Points d'accès sans fils et SSID
* Pour gérer les connections sans fils et l'attribution des utilisateurs dans le bon VLAN, on peut configurer plusieurs SSIDs, chaque point d'accès sans fil peut gérer des réseaux virtuels distincts (VLANs) pour différents groupes d'utilisateurs, comme les étudiants et les professeurs. Chaque SSID peut avoir des paramètres de sécurité et d'accès spécifiques qui correspondent aux besoins et aux politiques applicables à chaque groupe.
* Le contrôle d'accès aux SSIDs est souvent géré par un serveur RADIUS en conjonction avec WPA2-Enterprise. Lorsqu'un utilisateur tente de se connecter à un SSID, le point d'accès communique avec le serveur RADIUS pour authentifier l'utilisateur. Le serveur RADIUS vérifie si l'utilisateur a les droits nécessaires pour accéder à ce VLAN spécifique et, après une authentification réussie, l'utilisateur est connecté au VLAN approprié.
### Avancé
#### Routage interne (EIGRP/OSPF)
* Concernant le choix du protocole de routage interne, nous avons généralement deux choix possibles : EIGRP et OSPF
* OSPF est un protocole standard ouvert et non propriétaire et est supporté sur tous les équipements de chaque marques 
* EIGRP lui est propriétaire Cisco est uniquement déployable sur ces équipements mais possède des qualités accrue face à OSPF, meilleure métrique plus précise, demande moins de performances et plus facile à déployer.
* OSPF quand à lui demande bien plus de performance au niveau des équipements mais offre une plus grande liberté de configuration et de redistributions de routes grace à son système de Area qui permet meme dans des grands réseaux d'optimiser les partages de routes
* Généralement dans un environnement Cisco EIGRP est le choix le plus logique tandis que sur les autres marques OSPF est le meilleur choix.

| Caractéristique       | EIGRP                                                   | OSPF                                                        |
|-----------------------|---------------------------------------------------------|-------------------------------------------------------------|
| Type de protocole     | Protocole de routage avancé (Distance Vector)           | Protocole de routage de type link-state                     |
| Standard              | RFC 7868 (Informational) - plus courant sur Cisco       | Standard ouvert et non propriétaire (RFC 2328)              |
| Support multi-fournisseur | Historiquement propriétaire Cisco, mais peut être implémenté par d'autres fabricants  | Oui, supporté sur la plupart des équipements réseau        |
| Métrique              | Composite basée sur le débit et la latence              | Basée sur le coût des chemins, souvent associé à la bande passante |
| Utilisation des ressources | Généralement considéré comme moins exigeant          | Peut exiger plus de CPU et de mémoire dans les grands réseaux |
| Configuration         | Réputé pour être plus simple et rapide à configurer     | Nécessite une planification plus détaillée en raison des areas |
| Convergence           | Rapide, avec utilisation de queries et replies pour la découverte des routes | Plus lent en raison de la nature du protocole link-state    |
| Scalabilité           | Efficace dans les réseaux de taille moyenne à grande    | Très évolutive avec la structure en areas pour les très grands réseaux |
| Interopérabilité      | Meilleur dans les environnements dominés par Cisco      | Préféré dans les environnements multi-fournisseurs         |


#### Haute disponibilité (HSRP)
- **La couche de distribution** : HSRP est souvent mis en place entre les switchs de la couche de distribution pour assurer la continuité du service en cas de défaillance d'un appareil. Les switchs configurés avec HSRP choisissent un routeur actif et un ou plusieurs routeurs de secours pour prendre le relais si le routeur actif tombe en panne.
- **La couche core** : Dans certains cas, HSRP peut également être utilisé dans la couche core pour garantir une haute disponibilité au niveau le plus élevé du réseau. Cela permet une reprise rapide du trafic en cas de panne d'un des routeurs core.
#### Redondance de liens (EtherChannel)
 * ***Entre la couche d'accès et la couche de distribution*** : On utilise souvent EtherChannel pour les liens montants entre les switchs de la couche d'accès et ceux de la couche de distribution. Cela permet de maximiser la bande passante disponible entre ces deux couches et d'améliorer la tolérance aux pannes. En regroupant plusieurs ports, on s'assure que si un port ou un câble échoue, le trafic peut continuer à passer par les autres ports du groupe sans interruption.
- **Entre la couche de distribution et la couche core** : Les liens entre les switchs de distribution et les switchs core peuvent également utiliser EtherChannel pour fournir une bande passante accrue et une redondance entre ces deux niveaux critiques du réseau.
#### Segmentations des réseaux (VLANs)
* La segmentation par VLAN permet de séparer logiquement différents groupes d'utilisateurs, types de dispositifs ou applications sans la nécessité d'une séparation physique.
#### Optimisation des flux (QoS)
* Pour gérer efficacement la qualité de service (QoS) au sein d'un IUT, il est essentiel de classifier et de prioriser les différents types de trafic réseau. Cela garantit que les applications critiques, telles que la voix sur IP (VoIP) et la vidéoconférence, bénéficient d'une bande passante suffisante et d'une latence réduite, même en période de congestion du réseau.
#### Translations d'adresses (NAT/PAT)
#### Optimisation couche accès (STP/PORTSECURITY/BPDUGUARD)

### Sécurité 
- [ ] Filtrage des flux et segmentation des zones (DMZ,IN,OUT)
- [ ] Placement des FW/IDS/IPS
- [ ] Contrôle d'accès et authentification (AAA RADIUS EAP 802.1X)
### Externe 
- [ ] Liaison fournisseur d'accès Internet (Type d'offre/MPLS)
- [ ] Routage externe (BGP/Default Route)
- [ ] Liaison site à site (VPN/GRE)
### Equipements 
- [ ] Tableau des marques/gammes/performances pour les équipements
- [ ] Tableau des types de câbles (longueur/performances)
## 3) Datacenter 
### Bases
- [ ] Modèle d'architecture datacenter (Tier3/SpineLeaf)
- [ ] Architecture standard Spine Leaf
- [ ] Architecture avancée avec redondance par couche
- [ ] Architecture avancée avec haute disponibilité
- [ ] Architecture avancée avec sécurité
### Avancé
- [ ] Alimentation (principale et secondaire)
- [ ] LoadBalancing avec Répartition multisites
- [ ] Equipements nécessaires pour les serveurs
- [ ] Logique d'externalisation des serveurs
## 4) Services
- [ ] Liste des services déployables (Tableau)
- [ ] Liste des solutions disponibles (gratuite et payantes)
- [ ] Logique de configuration type 
- [ ] Couts des licences/serveurs