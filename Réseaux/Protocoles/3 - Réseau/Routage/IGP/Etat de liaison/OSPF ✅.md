# Guide OSPF

# 1) Généralités

- Protocole de routage interne (IGP) à état de lien.
- OSPF est un protocole standardisé, utilisé dans de grands réseaux tels que les ISP.
- Il prend en compte le coût (accumulation des vitesses des liens) plutôt que uniquement le nombre de sauts.
- N'utilise pas TCP ou UDP pour communiquer mais via des LSA 
![OSPF1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/OSPF1.png)

# 2) Base de données de OSPF

| Base de données         | Description                                                                                      | Unicité                           | Commande d'accès                |
|-------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------|---------------------------------|
| **Table des voisins**   | Liste des routeurs voisins avec lesquels une communication bidirectionnelle a été établie.      | Unique à chaque routeur.         | `show ip ospf neighbor`         |
| **Table de topologie**  | Résumé du LSDB contenant tous les LSA, représentant la topologie globale du réseau.              | Partagée au sein d'une zone.     | `show ip ospf database`         |
| **Table de routage**    | Liste des itinéraires générés par l'algorithme OSPF, indiquant comment envoyer les paquets.     | Unique à chaque routeur.         | `show ip route`                 |
# 3) Type de routeur dans OSPF

| Type de routeur | Fonction                                                                                             | Rôle dans OSPF                                                                                                       | Exemple                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **ASBR**        | Fait le lien entre OSPF et d'autres réseaux ou systèmes autonomes, utilisant différents protocoles. | Introduit des informations sur les routes externes dans l'environnement OSPF.                                       | Un routeur OSPF connecté à un réseau BGP, introduisant des informations de routage externe à OSPF.                        |
| **ABR**         | Sert de point de connexion entre différentes zones OSPF au sein du même système autonome.           | Propage les informations de routage entre les zones et peut introduire la route par défaut dans des zones spéciales. | Un routeur OSPF reliant la zone Backbone (Area 0) à une autre zone OSPF, gérant les informations de routage entre ces zones. |
| **IR (Internal Router)** | Opère à l'intérieur d'une seule zone OSPF, sans connecter à d'autres zones ou systèmes autonomes.    | Transmet des paquets à l'intérieur d'une zone OSPF, en utilisant les informations de routage OSPF internes.           | Un routeur OSPF qui n'est connecté qu'à des routeurs dans la même zone OSPF, gérant le routage interne à cette zone.       |

![OSPF2.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/OSPF2.png)

# 4) Messages OSPF

| Type de paquet                        | Fonction                                                                                                                                                                       |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Hello**                             | - Découvrir les voisins/établir des relations de voisinage. <br>- Permet également de maintenir ces relations.                                                                 |
| **DBD (Description de BDD)**          | - Echange des sommaires de bases de données entre les routeurs OSPF. <br>- Permettent aux routeurs de déterminer quels états de lien ne sont pas synchronisés.                 |
| **LSR (Demande d'état de liens)**     | - Utilisé pour demander des informations d'état de liaison spécifiques. <br>- Ce paquet est envoyé lorsqu'un routeur découvre, via les DBD, qu'il lui manque des informations. |
| **LSU (Mise à jour d'état de liens)** | - Pour envoyer les informations d'état de liaison demandées en réponse à des LSR. <br>- Contient les informations réelles sur l'état des liens.                                |
| **LSA**                               | A PATCH                                                                                                                                                                        |
## Link State Advertisements (LSA)
* Les LSA sont des informations sur l'état des liens, permettant à OSPF de construire et de maintenir sa base de données et de calculer les meilleures routes.

| Type de LSA | Description                                                                                                                                            | Utilisation                                                                                                | Aspects Clés                                                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **1**       | Décrit les interfaces d’un routeur.                                                                                                                    | Utilisé par chaque routeur pour partager des informations sur ses interfaces directes et leurs états.      | Crucial pour construire une vue de la topologie de la zone à partir de la perspective de chaque routeur.                         |
| **2**       | Décrit les routeurs connectés au segment.                                                                                                              | Utilisé pour fournir des informations sur la structure d'un réseau multi-accès, comme un réseau Ethernet.  | Important pour comprendre la connectivité entre les routeurs sur les réseaux multi-accès.                                        |
| **3**       | Résumé de route envoyée dans une autre Area par l’ABR (Area Border Router).                                                                            | Permet aux routeurs d'une zone OSPF de connaître les réseaux disponibles dans d'autres zones.              | Fournit une connectivité inter-zones et permet la diffusion des résumés de routes entre zones.                                   |
| **4**       | Décrit l’ASBR. Généré par l’ABR et envoyé dans les autres zones. Permet de faire connaître le routeur ID dans d’autres zones.                          | Utilisé pour communiquer l'emplacement des routeurs ASBR à travers l'AS OSPF.                              | Essentiel pour le routage vers des destinations en dehors de l'AS OSPF, notamment pour les routes apprenant d'autres protocoles. |
| **5**       | Route redistribuée par l’ASBR (routes externes, type RIP, EIGRP, etc.).                                                                                | Utilisé pour introduire des informations sur les routes externes dans l'OSPF.                              | Permet à OSPF de router le trafic vers des réseaux qui ne sont pas partie de l'AS OSPF.                                          |
| **7**       | Utilisé dans une Not So Stubby Area (NSSA). Comme le type 5, mais qui peut circuler dans une NSSA. Il est transformé en Type 5 à la sortie de la NSSA. | Permet l'introduction de routes externes dans une zone NSSA, qui sont ensuite converties en LSA de type 5. | Crucial pour la gestion des routes externes dans les zones NSSA, offrant une flexibilité dans les environnements restreints.     |


## Résume 
- Les **paquets HELLO** servent à établir des voisins OSPF.
- Les **LSA** diffusent des informations sur l'état des liens, permettant à OSPF de construire et de maintenir sa base de données et de calculer les meilleures routes.
- Les **LSR** sont des demandes d'informations manquantes ou obsolètes.
- Les **LSU** répondent aux LSR et diffusent des mises à jour d'état de lien.
# 5) Établissement du protocole

### 1. Découverte des Voisins et Établissement des Adjacences
- **Paquets HELLO** : Les routeurs OSPF envoient périodiquement des paquets HELLO sur chaque interface OSPF pour découvrir et maintenir des relations de voisinage avec les autres routeurs OSPF sur le même réseau.
- **Établissement des Adjacences** : Lorsque deux routeurs OSPF se découvrent mutuellement (à travers les paquets HELLO), ils établissent une adjacence, c'est-à-dire une relation de voisinage plus formelle nécessaire pour l'échange d'informations de routage.
### 2. Échange des Informations d'État de Lien
- **LSA de Type 1 et 2** : Chaque routeur crée des LSA de type 1 (LSA de routeur) pour décrire ses propres liens et un LSA de type 2 (LSA de réseau) est généré par le routeur désigné sur les réseaux multi-accès.
- **Inondation des LSA** : Ces LSA sont ensuite inondés (flooded) à tous les voisins OSPF pour assurer que chaque routeur dans la zone OSPF a une vue cohérente de la topologie du réseau.
### 3. Construction de la Base de Données d'État de Lien (LSDB)
- **Synchronisation des LSDB** : Chaque routeur reçoit et stocke les LSA inondés dans sa propre base de données d'état de lien (LSDB). Cela permet à chaque routeur d'avoir une compréhension complète de la topologie de la zone OSPF.
### 4. Demande de Mises à Jour Spécifiques (Si Nécessaire)
- **LSR (Link State Request)** : Si un routeur détecte des informations manquantes ou obsolètes dans sa LSDB, il envoie des LSR aux voisins pour demander des mises à jour spécifiques.
- **LSU (Link State Update)** : Les routeurs répondent aux LSR avec des LSU, fournissant les informations d'état de lien demandées.
### 5. Calcul des Chemins Optimaux
- **Algorithme de Dijkstra** : Chaque routeur utilise l'algorithme de Dijkstra pour calculer le chemin le plus court vers tous les réseaux dans la zone OSPF, en se basant sur les informations contenues dans sa LSDB.
### 6. Maintenance et Mises à Jour Continues
- **Inondation Périodique des LSA** : Les LSA sont régulièrement mis à jour et inondés pour assurer que tous les routeurs disposent des informations les plus récentes.
- **Paquets HELLO** : Les paquets HELLO continuent d'être échangés pour maintenir les adjacences OSPF.


# 6) Zones OSPF

| Type de Zone   | Routes Internes à l'OSPF | Résumés des Zones OSPF | Routes Externes |
|----------------|--------------------------|------------------------|-----------------|
| Backbone       | Toutes les routes internes de toutes les zones OSPF | Informations détaillées sur la topologie de toutes les autres zones OSPF | Routes apprenant d'autres protocoles de routage ou d'autres systèmes autonomes, via LSA de type 5 |
| Standard       | Toutes les routes internes à la zone standard elle-même | Résumés des routes des autres zones OSPF, via LSA de type 3 | Routes externes à l'OSPF, si elles sont autorisées, via LSA de type 5 |
| Stubby         | Toutes les routes internes à la zone Stubby elle-même | Résumés des routes des autres zones OSPF, via LSA de type 3 | Aucune information sur les routes externes à l'OSPF. Utilisation d'une route par défaut pour le trafic sortant |
| Totally Stubby | Toutes les routes internes à la zone Totally Stubby elle-même | Aucun résumé des autres zones OSPF | Aucune information sur les routes externes à l'OSPF. Utilisation d'une route par défaut pour tout trafic sortant |
| NSSA           | Toutes les routes internes à la zone NSSA elle-même | Résumés des routes des autres zones OSPF, via LSA de type 3 | Routes externes introduites dans la zone via LSA de type 7, qui sont convertis en LSA de type 5 par l'ABR lorsqu'ils quittent la zone NSSA |

## Resume simplifiée
- **Zone Backbone (Area 0)** : Le centre nerveux du réseau OSPF, elle contient des informations détaillées sur toutes les zones du réseau OSPF, y compris des résumés de routes pour l'ensemble du réseau.
- **Zone Standard** : Une zone OSPF classique qui gère les routes internes et les résumés des autres zones OSPF, avec la possibilité d'accéder aux routes externes OSPF.
- **Zone Stubby** : Une zone OSPF conçue pour limiter les informations de routage ; elle gère les routes internes et les résumés des autres zones OSPF mais bloque les routes externes OSPF, utilisant une route par défaut pour tout le trafic sortant.
- **Zone Totally Stubby** : Une version plus restrictive de la zone Stubby, cette zone gère uniquement les routes internes et n'obtient pas de résumés des autres zones OSPF, s'appuyant sur une route par défaut pour tout le trafic sortant.
- **Zone NSSA (Not-So-Stubby Area)** : Une adaptation de la zone Stubby qui permet des routes externes au réseau OSPF. Elle gère les routes internes, reçoit les résumés des autres zones OSPF et utilise des LSA de type 7 pour les routes externes, qui sont ensuite convertis en LSA de type 5 par l'ABR.
# 7) Différents états de liens
| État du lien | Description | Fonction |
|--------------|-------------|----------|
| **Down** | Aucun paquet Hello reçu sur l'interface. | Indique qu'aucune communication OSPF n'est actuellement établie sur l'interface. |
| **Init** | Paquets Hello reçus d'un voisin, contenant l'ID du routeur. | Signifie qu'un paquet Hello a été reçu, mais qu'une communication bidirectionnelle n'est pas encore établie. |
| **Two-Way** | Communication bidirectionnelle établie entre les deux routeurs. | Confirme que les deux routeurs se sont vus l'un l'autre via des paquets Hello. Permet l'élection du DR (Designated Router) et du BDR (Backup Designated Router). |
| **ExStart** | État spécifique aux connexions point-à-point. | Marque le début de l'échange des paquets DBD (Database Description) et la détermination de quel routeur initiera l'échange. |
| **Exchange** | Échange de paquets DBD entre les routeurs. | Les routeurs partagent leurs bases de données d'état de lien respectives via des paquets DBD. |
| **Loading** | Échange de paquets LSR (Link State Request) et LSU (Link State Update) contenant des informations sur les routes. | Les routeurs demandent et reçoivent des informations supplémentaires nécessaires pour compléter leur base de données d'état de lien. |
| **Full** | Bases de données d'état de lien entièrement synchronisées entre les routeurs. | Indique que les bases de données d'état de lien sont pleinement synchronisées et que la relation de voisinage est complète. |

# 8) Mise à jour 
* Concernant les mises à jour, elles sont transmises uniquement en MULTICAST comme ceci
	-   Les mises à jour envoyées par le DR utilisent l’adresse IP ***224.0.0.5***
	-   Les mises à jour envoyées au DR et au BDR utilisent l’adresse IP ***224.0.0.6***
- Les adresses MULTICAST **224.0.0.5** et **224.0.0.6** sont réservées pour l'envoi des mises à jour de routage. Ces adresses permettent une diffusion efficace des mises à jour sans surcharger le réseau.
- Il existe un processus d'élection de deux routeurs dans chaque zone jouant le rôle de délégué et sous-délégué qui gèrent la table de routage transmise à la zone. Ce sont le **DR (Designated Router)** et le **BDR (Backup Designated Router)**. Ils sont surtout importants sur les réseaux de diffusion comme Ethernet pour réduire le volume de trafic OSPF.

# 9) Configuration OSPF (IPv4) 

## Monozone IPv4
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

## Multizone IPv4

```
router ospf [PID]
	router-id [X.X.X.X]
	network [ip_voisin] [masque_voisin_invert] area [area_ip_voisin]
```
## **Résumé de route en multizone** :
- Dans une configuration multizone, les routeurs peuvent résumer ou agréger les routes pour simplifier et réduire le nombre d'entrées dans la table de routage.
```
router ospf 1
	area X range @route_resumée
```

# 10) Configuration OSPFv3 (IPv6)

* OSPFv3 est une évolution d'OSPF (Open Shortest Path First) conçue spécifiquement pour prendre en charge le routage IPv6. Alors que OSPFv2 est utilisé pour IPv4, OSPFv3 traite le routage pour IPv6. Voici une exploration détaillée des éléments mentionnés dans votre texte :
### Échanges entre Routeurs et Multicast

- **Link-local** :
    - Dans IPv6, l'adresse link-local est une adresse IP qui est uniquement valable sur le lien ou le segment actuel. Elle n'est pas routable au-delà de ce segment. OSPFv3 utilise ces adresses pour les échanges entre routeurs sur le même lien.
- **Multicast OSPF Routers (FF02::5)** :
    - Il s'agit de l'adresse multicast à laquelle tous les routeurs OSPFv3 écoutent. Cette adresse est utilisée pour envoyer des paquets OSPF qui sont destinés à tous les routeurs sur un réseau local.
- **Multicast Designated Routers (FF02::6)** :
    - Cette adresse est écoutée par tous les Designated Routers (DR) et Backup Designated Routers (BDR) OSPFv3 sur un réseau local. Elle est utilisée pour optimiser la diffusion d'informations OSPF sur des réseaux tels que Ethernet.
### Configuration OSPFv3 monozone

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
### Configuration OSPFv3 Multizone
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
# 11) OSPFv3 Dual-Stack
* Déployer OSPF pour IPv4 et IPv6 en même temps 
```
R(config)#interface [INTERFACE]
R(config-if)#ospfv3 [PID] ipv4 area [NUM]
R(config-if)#ospfv3 [PID] ipv6 area [NUM]

R(config)#router ospfv3 [PID]
R(config-router)#address-family ipv4 unicast
R(config-router-af)#passive-interface [INTERFACE]
R(config-router)#address-family ipv6 unicast
R(config-router-af)#passive-interface [INTERFACE]
```

# Résumé de route en multizone
* Dans un environnement OSPF multizone, le résumé des routes peut être utilisé pour consolider plusieurs routes en une seule entrée
```
ipv6 router ospf 
	area X range @route_resumée  // Résumer les routes pour une zone spécifique

```
# Lien Virtuel OSPF
La configuration d'un lien virtuel OSPF entre deux Area Border Routers (ABRs) peut être nécessaire lorsque l'une des zones OSPF n'est pas directement connectée à la zone Backbone (Area 0). Voici les étapes générales pour configurer un lien virtuel OSPF :
## Étapes de Configuration de Base
1. **Identifier les ABRs** : Identifiez les deux routeurs ABR qui établiront le lien virtuel. L'un de ces ABRs doit avoir une interface dans la zone Backbone (Area 0), et l'autre ABR sera celui de la zone qui nécessite la connexion à la zone Backbone.
2. **Accéder à la Configuration du Routeur** : Connectez-vous à chaque ABR et accédez au mode de configuration.
3. **Configurer le Lien Virtuel** : Sur chaque ABR, configurez le lien virtuel en spécifiant le routeur ID de l'autre ABR et la zone de transit (la zone OSPF à travers laquelle le lien virtuel passera).
### Exemple de Commandes
Supposons que les routeurs ABR ont les router IDs `1.1.1.1` et `2.2.2.2`, et que la zone de transit est la zone 1. Voici à quoi pourrait ressembler la configuration sur chaque routeur :
#### Sur l'ABR avec Router ID `1.1.1.1` :
```bash
router ospf 1
 area 1 virtual-link 2.2.2.2
```
#### Sur l'ABR avec Router ID `2.2.2.2` :
```bash
router ospf 1
 area 1 virtual-link 1.1.1.1
```
