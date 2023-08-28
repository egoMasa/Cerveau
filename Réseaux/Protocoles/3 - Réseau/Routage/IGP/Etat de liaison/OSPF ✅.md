# Guide OSPF

## 1) Généralités

- Protocole de routage interne (IGP) à état de lien.
- OSPF est un protocole standardisé, utilisé dans de grands réseaux tels que les ISP.
- Alternative au protocole de vecteur de distance.
- Il prend en compte le coût plutôt que uniquement le nombre de sauts.
- Lorsqu'un routeur OSPF est initialement connecté à un réseau, il tente de :
    - Créer des contiguïtés avec ses voisins.
    - Procéder à l'échange des informations de routage.
    - Calculer les meilleures routes.
    - Converger.
## 2) Composantes

- Différents types de **paquets** :
	- **Hello** - Utilisé pour découvrir les voisins.
	- **DBD (Description de BDD)** - Pour échanger des sommaires de bases de données.
	- **LSR (Demande d'état de liens)** - Pour demander des informations d'état de liaison spécifiques.
	- **LSU (Mise à jour d'état de liens)** - Pour répondre aux LSR avec les informations d'état de liaison demandées.
	- **LSA (Accusé de réception d'état de lien)** - Pour confirmer la réception des mises à jour d'état de lien.
- Trois différentes **bases de données** :
	- **Table des voisins** :
		- Liste des routeurs voisins vers lesquels un routeur a établi une communication bidirectionnelle.
		- Unique à chaque routeur.
		- Accessible via la commande `show ip ospf neighbor`.
	- **Table de topologie** :
		- Un résumé du LSDB (Link State Database) contenant tous les LSA.
		- Représente la topologie globale du réseau.
		- Table partagée au sein d'une zone uniquement.
		- Accessible via la commande `show ip ospf database`.
	- **Table de routage** :
		- Liste des itinéraires générés via l'algorithme OSPF.
		- Unique à chaque routeur.
		- Contient des informations sur comment envoyer les paquets.
		- Accessible via la commande `show ip route`.
## 3) Établissement du protocole

- Chaque interface routeur possède une valeur (coût) déterminant le meilleur chemin vers la destination.
- **Etape 1** : Établissement des liaisons de voisinage (HELLO).
	- Les routeurs s'envoient des messages HELLO.
	- Si un voisin est présent/compatible OSPF, un état de voisinage est établi.
- **Etape 2** : Échange de l'état et du coût (LSA).
	- Les routeurs s'envoient des messages LSA contenant l'état et le coût de l'interface.
	- Les LSA sont propagés vers les autres routeurs.
	- Continue jusqu'à ce que toutes les interfaces d'une zone aient reçu le LSA de chacune.
- **Etape 3** : Création de la table de topologie (LSDB).
	- Les routeurs construisent la table de topologie à partir des LSA recensés.
- **Etape 4** : Création de l'arborescence SPF.
	- La table de topologie est traitée par l'algorithme SPF pour créer une arborescence SPF.
- **Etape 5** : Choix du meilleur itinéraire.
	- Les meilleurs chemins créés par SPF sont proposés à la table de routage IP.
	- Routes insérées sauf si une route est déjà présente avec une distance administrative plus faible (statique).

## 4) Zone unique et zone multiples

- **Zone unique** :
    - Tous les routeurs sont dans la zone de backbone (0).
    - Temps de convergence plus long dû aux mises à jour.
- **Zone multiples** :
    - Routeurs séparés par zone mais forcément reliés par la zone 0.
    - Nécessite un routeur qui relie les zones (ABR).
    - Permet une table de routage plus petite.
    - Réduit la fréquence de calcul de SPF.

## 5) Types de paquets OSPF

- **Hello** - Découvre les voisins OSPF.
- **DBD** - Vérifie la synchronisation de la BDD entre les routeurs.
- **LSR** - Demande l'enregistrement des états spécifiques entre 2 routeurs.
- **LSU** - Envoie les enregistrements des états demandés.

## 6) Différents états de liens
* Etat Down
	* Si aucun paquet hello recu sur interface
* Etat Init
	* Paquets Hello recu de la part d'un voisin
	* Contient l'ID du routeur
* Etat Two-Way
	* Communication bidirectionnelle entre les 2 routeurs
	* Election du DR et BDR
* Etat ExStart
	* Uniquement en PTP
	* Choix du routeur qui initie l'échange de paquets DBD avec numéro de séquence 
* Etat Exchange
	* Echange de paquets DBD
* Etat Loading
	* Paquets LSR et LSU avec informations supplémentaires sur les routes
	* Traitement des routes via SPF
* Etat Full
	* Base de données d'état entièrement synchronisé

## 7) Mise à jour 
* Concernant les mises à jour, elles sont transmises uniquement en MULTICAST comme ceci
	-   Les mises à jour envoyées par le DR utilisent l’adresse IP ***224.0.0.5***
	-   Les mises à jour envoyées au DR et au BDR utilisent l’adresse IP ***224.0.0.6***
- Les adresses MULTICAST **224.0.0.5** et **224.0.0.6** sont réservées pour l'envoi des mises à jour de routage. Ces adresses permettent une diffusion efficace des mises à jour sans surcharger le réseau.
- Il existe un processus d'élection de deux routeurs dans chaque zone jouant le rôle de délégué et sous-délégué qui gèrent la table de routage transmise à la zone. Ce sont le **DR (Designated Router)** et le **BDR (Backup Designated Router)**. Ils sont surtout importants sur les réseaux de diffusion comme Ethernet pour réduire le volume de trafic OSPF.

## 8) Commandes OSPF 
1. **Activer OSPF sur le routeur** :
- Utilisé pour démarrer le processus OSPF sur le routeur.
```
R1(config)#router ospf @ID
```

2. **Annoncer un réseau voisin** :
- Cette commande informe OSPF des réseaux directement connectés que le routeur devrait annoncer aux autres routeurs OSPF.
```
R1(config-router)#network @ip_reseau_voisin @masque_inverse area @area
```

3. **Changer la priorité de l’interface routeur** :
- Cette commande est utilisée pour définir la priorité d'une interface dans le processus d'élection du DR (Designated Router) et BDR (Backup Designated Router). Une priorité plus élevée est plus susceptible d'être élue.
```
R1(config-router)#ip ospf priority <0-255>
```

4. **Changer l'ID du routeur** :
- Changer l'identifiant unique du routeur OSPF. L'ID du routeur est normalement dérivé de l'adresse IP la plus élevée de toutes ses interfaces, mais cette commande vous permet de définir manuellement cet ID.
```
R1(config-router)#router-id @IP
```

5. **Partager une route par défaut/statique sur le routeur de sortie** :
- Utilisé pour propager une route par défaut dans le domaine OSPF. Très utile si un routeur est la passerelle de sortie pour Internet ou un autre réseau.
```
R1(config-router)#default-information originate
```

6. **Empêcher une interface de partager la mise à jour de la table** :
- Cette commande empêche OSPF d'envoyer des mises à jour par une interface spécifique. C'est utile pour les interfaces connectées à des réseaux qui n'ont pas besoin de ces mises à jour.
```
R1(config-router)#passive-interface @interface
```

7. **Réinitialiser les adjacences** :
- Parfois, il peut être nécessaire de réinitialiser les adjacences OSPF, par exemple après avoir apporté des modifications majeures à la configuration OSPF.
```
clear ip ospf process
```

## OSPF Multizone

Le protocole OSPF multizone est une extension d'OSPF qui permet de diviser un grand domaine OSPF en zones plus petites et plus gérables. Cela peut aider à améliorer l'efficacité et à réduire les temps de convergence.

- **Zonage** :
    - Le zonage OSPF permet d'effectuer un routage précis selon une zone délimitée afin de limiter les impacts des changements de topologies, réduisant ainsi les ressources nécessaires pour recalculer les tables de routage.

- **LSA (Link State Advertisement)** :
    - Son objectif principal est de maintenir une topologie commune au sein des routeurs d'une zone. Il est responsable de l'envoi des mises à jour topologiques.
        - Types 1 et 2 sont confinés à une seule zone.
        - Type 3 permet la communication entre zones.

- **SPF (Shortest Path First)** :
    - Il s'agit de l'algorithme utilisé par OSPF pour déterminer le chemin le plus court vers une destination. Dans le contexte multizone, l'objectif est de réduire la fréquence de ses calculs pour optimiser les performances.

- **LSDB (Link State Data Base)** :
    - C'est la base de données où OSPF stocke les informations topologiques. Chaque routeur dans une zone a une LSDB identique.

- **ABR (Area Border Router)** :
    - Routeur servant de point de passage entre deux zones, dont la zone principale appelée BackBone. Il résume et propage les LSA entre les zones.

- **ASBR (Autonomous System Border Router)** :
    - Routeur qui connecte OSPF à d'autres systèmes autonomes, souvent utilisé avec des protocoles comme BGP.

- **Réduction de la table de routage** :
    - L'un des principaux avantages d'utiliser OSPF en multizone est de réduire la taille de la table de routage, améliorant ainsi l'efficacité du routeur.

- **LSU (Link State Update)** :
    - Message utilisé pour mettre à jour les informations topologiques dans OSPF.

- **LSR (Link State Request)** :
    - Message envoyé par un routeur pour demander des mises à jour spécifiques dans OSPF.

- **IA (Inside Area)** :
    - Se réfère à des informations ou des activités qui ont lieu à l'intérieur d'une zone OSPF spécifique.

### **Configuration multizone** :
```
router ospf 1
	router-id X.X.X.X
	network @ip_voisin @masque_voisin_invert area @area_ip_voisin
```
### **Résumé de route en multizone** :
- Dans une configuration multizone, les routeurs peuvent résumer ou agréger les routes pour simplifier et réduire le nombre d'entrées dans la table de routage.
```
router ospf 1
	area X range @route_resumée
```

## OSPFv3 

* OSPFv3 est une évolution d'OSPF (Open Shortest Path First) conçue spécifiquement pour prendre en charge le routage IPv6. Alors que OSPFv2 est utilisé pour IPv4, OSPFv3 traite le routage pour IPv6. Voici une exploration détaillée des éléments mentionnés dans votre texte :

### Échanges entre Routeurs et Multicast

- **Link-local** :
    - Dans IPv6, l'adresse link-local est une adresse IP qui est uniquement valable sur le lien ou le segment actuel. Elle n'est pas routable au-delà de ce segment. OSPFv3 utilise ces adresses pour les échanges entre routeurs sur le même lien.
- **Multicast OSPF Routers (FF02::5)** :
    - Il s'agit de l'adresse multicast à laquelle tous les routeurs OSPFv3 écoutent. Cette adresse est utilisée pour envoyer des paquets OSPF qui sont destinés à tous les routeurs sur un réseau local.
- **Multicast Designated Routers (FF02::6)** :
    - Cette adresse est écoutée par tous les Designated Routers (DR) et Backup Designated Routers (BDR) OSPFv3 sur un réseau local. Elle est utilisée pour optimiser la diffusion d'informations OSPF sur des réseaux tels que Ethernet.
### Configuration OSPFv3

La configuration de base d'OSPFv3 pour IPv6 est similaire à celle d'OSPFv2 pour IPv4, mais avec des commandes spécifiques à IPv6 :

```
ipv6 unicast routing                 // Activer le routage IPv6

ipv6 router ospf 1                  // Entrer dans la configuration OSPFv3
	router-id 1.1.1.1             // Définir un ID de routeur, toujours en format IPv4
	
int G0/0/0                          // Configurer une interface spécifique
	ipv6 address 2001:db8:cafe::1/64  // Attribuer une adresse IPv6 à l'interface
	ipv6 ospf 1 area 0                // Activer OSPFv3 sur cette interface dans la zone 0
	ipv6 ospf priority 20             // Définir la priorité OSPF pour le processus de DR/BDR
	ipv6 ospf cost 20                 // Définir le coût OSPF pour cette interface
	
// Commandes pour vérifier la configuration et le fonctionnement
sh ipv6 route ospf                 // Voir les routes apprises par OSPFv3
sh ipv6 ospf neighbor              // Voir les voisins OSPFv3
sh ipv6 int brief                  // Résumé des interfaces IPv6

```
### OSPFv3 Multizone
* Dans un environnement multizone, OSPFv3 divise le réseau en zones pour améliorer l'efficacité et la scalabilité. Chaque zone est un domaine de diffusion séparé :
```
ipv6 unicast-routing               // Activer le routage IPv6

ipv6 router ospf 1                 // Entrer dans la configuration OSPFv3
	router-id X.X.X.X             // ID du routeur

int G0/0                           // Configuration pour une interface spécifique
	ipv6 ospf 1 area @area_reseau_voisin_interface // Spécifier la zone pour cette interface

```
### Commandes de vérification
```
show ipv6 ospf                     // Informations générales sur OSPFv3
show ipv6 route                   // Table de routage IPv6
show ipv6 ospf database           // Base de données d'état de liaison OSPFv3
show ipv6 ospf interface          // Informations sur les interfaces OSPFv3
show ipv6 ospf neighbor           // Informations sur les voisins OSPFv3
```

## Résumé de route en multizone
* Dans un environnement OSPF multizone, le résumé des routes peut être utilisé pour consolider plusieurs routes en une seule entrée
```
ipv6 router ospf 
	area X range @route_resumée  // Résumer les routes pour une zone spécifique

```