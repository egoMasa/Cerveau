# Guide QoS 

# Sommaire 
- [x] Principe et objectifs QoS
- [x] Bande passante, Latence, Perte, Gigue, Echo, 
- [x] Différents modèle de QoS (Best Effort, IntServ, DiffServ)
- [x] Marquage Ethernet CoS L2 (entête trame 802.1Q, Cos 0-7)
- [x] Marquage IP ToS L3 et DSCP
- [ ] Valeurs de QoS (AF,IPP,CS,DP,ECN)
- [x] Algorithme de files d'attente 
	- [ ] Gestion de congestion classique
		- [ ] FIFO (Hardware queue, software queue, scheduler)
		- [ ] PQ
			- [ ] 4 file statique non configurable 
			- [ ] Files haute priorités sont vidés en premier
			- [ ] Files basses priorités potentiellement jamais vidé 
		- [ ] CQ
			- [ ] Rotation entre les files hautes et basses
			- [ ] Nombre d'octets par cycle/file définit 
			- [ ] Toutes les files se vident
		- [ ] WFQ
			- [ ] Files dynamique pour chaque flux
	- [ ] Gestion plus valorisée
		- [ ] CBWFQ
			- [ ] File avec pourcentage de la bande passante
			- [ ] Reservation selon classes
		- [ ] LLQ
			- [ ] File supplémentaire avec priorité stricte qui passent au dessus
		- [ ] IP RTP Priority
- [ ] Configuration Cisco (L3 et L2)

# 1) Principe et objectifs de la QoS (Quality of Service)

### Principe de base
1. **Marquage et Classification** :
   - **Marquage L2** : Utilise l'entête 802.1Q pour marquer les trames Ethernet avec un champ CoS (Class of Service) qui a des valeurs allant de 0 à 7. Cela permet de différencier les trames selon leur priorité.
   - **Marquage L3** : Utilise le champ TOS (Type of Service) dans l'entête IP, transformé en DSCP (Differentiated Services Code Point) pour offrir une granularité plus fine dans la classification du trafic.
2. **Gestion des files d'attente** : Les paquets sont triés dans différentes files d'attente selon leur priorité, permettant une gestion plus efficace de la bande passante et des ressources réseau.
### Objectifs
1. **Priorisation du Trafic** : 
   - Permet de donner la priorité à certains types de trafic, comme la voix sur IP (VoIP) ou la vidéo, qui sont sensibles à la latence et à la perte de paquets.
   - Réduit les problèmes de latence, gigue, perte de paquets, et écho, particulièrement critiques pour les applications en temps réel.
2. **Contrôle et Gestion de la Bande Passante** :
   - Assure une utilisation optimale de la bande passante disponible.
   - Prévient la congestion du réseau en régulant le trafic en fonction de son importance et de sa nature.
3. **Amélioration de la Qualité de l'Expérience Utilisateur** :
   - Garantit que les applications critiques fonctionnent de manière fluide et sans interruption.
   - Contribue à une meilleure expérience utilisateur, surtout dans des environnements d'entreprise où différents types de trafic coexistent.
4. **Flexibilité et Évolutivité** :
   - Permet aux administrateurs réseau de configurer et d'adapter les politiques de QoS selon les besoins changeants de l'organisation.
   - Offre la capacité de gérer efficacement le trafic sur des réseaux de plus en plus complexes et chargés.

En résumé, la QoS dans les réseaux Cisco, et plus généralement dans les environnements de réseau modernes, est essentielle pour assurer une gestion efficace du trafic, en donnant la priorité aux applications critiques tout en optimisant l'utilisation de la bande passante disponible. Cela est crucial pour maintenir la performance, la fiabilité et la qualité de service dans des environnements réseau diversifiés.

# 2) Bande Passante, Latence, Perte, Gigue, Écho

## Bande Passante
- **Définition** : La bande passante est la capacité de transmission de données d'un réseau. Elle joue un rôle crucial dans la QoS, car une bande passante insuffisante peut entraîner des retards et des pertes de paquets.
- **QoS** : La gestion de la bande passante dans la QoS vise à allouer suffisamment de ressources réseau pour garantir la performance des applications critiques.
## Latence
- **Définition** : La latence est le temps de transit d'un paquet de données de sa source à sa destination.
- **Seuils Acceptables** : Pour les applications en temps réel, une latence entre 150 et 200 ms est généralement considérée comme acceptable.
- **Impact QoS** : La QoS cherche à minimiser la latence, particulièrement pour le trafic sensible comme la VoIP, où un délai élevé peut affecter significativement la qualité de l'appel.
## Perte de Paquets
- **Définition** : La perte de paquets se produit lorsque des paquets de données sont perdus pendant leur transmission sur le réseau.
- **Taux Acceptable** : Un taux de perte de 1 à 3% est souvent toléré, mais cela dépend du type d'application.
- **Rôle de la QoS** : La QoS aide à gérer et à prévenir la congestion réseau, réduisant ainsi les risques de perte de paquets.
## Gigue (Jitter)
- **Définition** : La gigue est la variation du temps de latence entre les paquets de données.
- **Seuil** : Une gigue inférieure à 100 ms est généralement requise pour des applications en temps réel.
- **Gestion QoS** : La QoS utilise des techniques comme le buffering de gigue pour minimiser l'impact de la variation de la latence sur la qualité de service.
## Écho
- **Définition** : L'écho dans les réseaux est le délai entre l'émission d'un signal et la réception de ce signal réverbéré.
- **Seuil de Perception** : Un écho n’est pas perceptible s’il est inférieur à 50 ms.
- **Contrôle QoS** : Bien que la QoS ne puisse pas directement contrôler l'écho, une bonne gestion de la latence et de la gigue peut aider à réduire son impact.


# 3) Différents modèles de QoS 
* Les trois modèles principaux sont Best Effort, Integrated Services (IntServ), et Differentiated Services (DiffServ). Chacun a une approche unique pour la gestion de la qualité de service.
## Best Effort
- **Principe** : Le modèle Best Effort ne fournit aucune garantie de QoS. Il traite tous les paquets de données de manière égale, sans priorité ni distinction.
- **Fonctionnement** :
	- **Premier Arrivé, Premier Servi (FIFO)** : Les paquets sont traités dans l'ordre où ils arrivent, sans égard pour leur type ou leur importance.
	- **Aucune Réservation de Ressources** : Il n'y a pas de mécanismes pour réserver de la bande passante ou des ressources pour des types de trafic spécifiques.
	- **Adapté aux Réseaux à Faible Congestion** : Ce modèle fonctionne bien dans les environnements où la congestion du réseau est minime et où il n'y a pas de besoin critique en termes de performance pour certains types de trafic.
## Integrated Services (IntServ)
- **Principe** : IntServ est un modèle qui fournit une QoS garantie en réservant des ressources réseau pour chaque flux de trafic.
- **Fonctionnement** :
	- **Réservation de Ressources** : Les applications demandent une certaine qualité de service (comme la bande passante, la latence) pour leur trafic, et le réseau s'engage à fournir ces ressources spécifiques.
	- **Protocole RSVP (Resource Reservation Protocol)** : Utilisé pour réserver des ressources le long du chemin emprunté par le paquet dans le réseau.
	- **Convient aux Applications Critiques** : Idéal pour des applications comme la VoIP ou la vidéoconférence qui nécessitent une qualité de service garantie.
	- **Limitation** : Peut être difficile à mettre en œuvre et à maintenir à grande échelle en raison de la complexité de la gestion des réservations de ressources.
## Differentiated Services (DiffServ)
- **Principe** : DiffServ attribue des niveaux de service différents à différents types de trafic sans réservation de ressources spécifiques.
- **Fonctionnement** :
	- **Marquage des Paquets** : Les paquets sont marqués selon leur type de trafic, généralement en utilisant le champ DSCP dans l'entête IP.
	- **Classes de Service** : Les paquets marqués sont traités selon leur classe de service, définie par leur marquage DSCP.
	- **Politiques Basées sur les Classes** : Les politiques de traitement (comme la priorisation, la limitation de débit) sont appliquées en fonction des classes de service.
	- **Scalabilité et Flexibilité** : Ce modèle est plus facile à déployer et à gérer à grande échelle comparé à IntServ, car il ne nécessite pas de réservation individuelle de ressources pour chaque flux.
## Résumé
- **Best Effort** : Simple, sans discrimination ni garantie de QoS.
- **IntServ** : Réservation de ressources par flux, idéal pour les applications critiques mais difficile à échelonner.
- **DiffServ** : Classification et traitement des paquets basés sur des politiques, équilibrant la flexibilité et la gestion de la qualité de service.

Chaque modèle a ses avantages et ses inconvénients, et le choix du modèle dépend des besoins spécifiques du réseau et des applications qu'il supporte. DiffServ est souvent privilégié dans les grands réseaux d'entreprise en raison de sa scalabilité et de sa flexibilité.

# 4) Différents algorithme de file d'attente

* Les algorithmes de file d'attente sont des éléments clés dans la gestion de la QoS. Ils déterminent comment les paquets sont traités et transmis dans les réseaux. Voici un aperçu des différents types d'algorithmes de file d'attente mentionnés :
## Gestion de Congestion Classique
- **FIFO (First In, First Out)**
	- **Principe** : Les paquets sont traités dans l'ordre de leur arrivée.
	- **File d'attente** : Peut être implémentée en hardware ou en software.
	- **Scheduler** : Détermine l'ordre de traitement des paquets.

- **PQ (Priority Queuing)**
	- **Files Statiques Non Configurables** : Les paquets sont triés en quatre files de priorité fixe.
	- **Priorité** : Les files de haute priorité sont traitées en premier.
	- **Risque** : Les files de basse priorité peuvent ne jamais être vidées en cas de trafic intense sur les files de haute priorité.

- **CQ (Custom Queuing)**
	- **Rotation** : Alterne le traitement des paquets entre les files de haute et de basse priorité.
	- **Allocation** : Définit le nombre d'octets à traiter par cycle et par file.
	- **Équité** : Assure que toutes les files se vident, évitant la faim des files de basse priorité.

- **WFQ (Weighted Fair Queuing)**
	- **Dynamique** : Crée une file dynamique pour chaque flux de trafic.
	- **Équitable** : Assure un traitement équitable basé sur le poids attribué à chaque flux.
## Gestion Plus Valorisée
- **CBWFQ (Class-Based Weighted Fair Queuing)**
	- **Ressources Allouées** : Chaque file se voit attribuer un pourcentage de la bande passante.
	- **Classification** : Les paquets sont classés et mis en file d'attente selon des classes définies.

- **LLQ (Low Latency Queuing)**
	- **File Supplémentaire à Haute Priorité** : Ajoute une file avec priorité stricte pour les trafics critiques (comme la VoIP).
	- **Supériorité** : Cette file a la priorité sur toutes les autres, garantissant une latence faible pour les trafics prioritaires.

- **IP RTP Priority**
	- **Spécialisé pour la VoIP** : Conçu pour donner la priorité aux paquets RTP (Real-Time Protocol), souvent utilisés dans la VoIP.
	- **Priorité Élevée** : Assure une transmission rapide et prioritaire des paquets RTP.
## Résumé
- **Classiques** (FIFO, PQ, CQ, WFQ) : Offrent des méthodes basiques de gestion de la congestion, de la plus simple (FIFO) à la plus équitable (WFQ).
- **Avancées** (CBWFQ, LLQ, IP RTP Priority) : Introduisent des mécanismes plus sophistiqués, permettant une gestion plus fine de la QoS selon les besoins spécifiques de différents types de trafic.
--- 

# 5) Marquage Ethernet CoS L2 et Marquage IP ToS L3/DSCP

La QoS (Quality of Service) dans les réseaux repose en grande partie sur le marquage des paquets de données pour indiquer leur priorité et leur type de service. Ce marquage est réalisé à deux niveaux clés : au niveau Ethernet (Couche 2 - L2) et au niveau IP (Couche 3 - L3). Voici un aperçu détaillé de ces deux processus :

## 1. Marquage Ethernet CoS L2 (Class of Service - Niveau de Couche 2)
- **Entête 802.1Q** : 
	- Dans les réseaux Ethernet, le marquage CoS est intégré dans l'entête 802.1Q, qui est utilisé pour le tagging VLAN (Virtual Local Area Network).
	- Cette entête ajoute 4 octets au cadre Ethernet standard, dont 3 bits sont dédiés au champ CoS.
- **Valeurs CoS (0-7)** :
	- Le champ CoS peut prendre des valeurs de 0 à 7, représentant différents niveaux de priorité.
	- La valeur 0 est la plus basse priorité, tandis que 7 est la plus haute. Ces valeurs sont utilisées pour déterminer la priorité de traitement des trames dans le réseau.
	- Par exemple, une trame marquée avec un CoS de 7 sera traitée avant une trame marquée avec un CoS de 2.
- **Utilisation** :
	- Les switches et les routeurs capables de lire l'entête 802.1Q utilisent les informations de CoS pour décider comment traiter chaque trame, par exemple, en les dirigeant vers des files d'attente de priorité différente.

## 2. Marquage IP ToS L3 et DSCP (Type of Service - Niveau de Couche 3)
- **Champ ToS et DSCP** :
	- Dans les paquets IP, le marquage de la QoS était initialement réalisé à l'aide du champ ToS (Type of Service).
	- Avec l'introduction de DiffServ, le champ ToS a été restructuré en DSCP (Differentiated Services Code Point), qui offre une granularité plus fine pour la classification du trafic.
- **Valeurs DSCP** :
	- Le champ DSCP comprend les 6 premiers bits de l'ancien champ ToS, offrant jusqu'à 64 valeurs différentes pour marquer les paquets.
	- Ces valeurs permettent de spécifier la manière dont le trafic doit être traité. Par exemple, une valeur DSCP élevée peut indiquer un trafic à haute priorité qui nécessite une faible latence.
- **Utilisation** :
	- Les routeurs et les commutateurs examinent les valeurs DSCP pour déterminer la classe de service des paquets IP, influençant ainsi les décisions de transmission, comme le choix de la file d'attente et les priorités de traitement.
	- Différentes politiques de QoS peuvent être appliquées en fonction des valeurs DSCP, comme la limitation de débit, la priorisation, ou la prévention de congestion.
#### En Résumé
- **Marquage Ethernet CoS L2** : S'applique aux trames Ethernet, utilisant l'entête 802.1Q pour définir la priorité de traitement des trames au sein des réseaux locaux.
- **Marquage IP ToS L3 et DSCP** : S'applique aux paquets IP, utilisant le champ DSCP pour une classification plus détaillée du trafic, influençant la manière dont les paquets sont traités dans les réseaux étendus.


# 2) Configuration Cisco 

## Etape 1 : Activer QoS et l'étiquetage des interfaces sur SW
```
SW(config)#int [INTERFACE]
SW(config-if)#mls qos trust device cisco-phone
SW(config-if)#mls qos cos 5
SW(config-if)#mls qos trust dscp

SW(config)#int [INTERFACE]
SW(config-if)#switchport mode access
SW(config-if)#switchport access vlan 30
SW(config-if)#mls qos trust cos
SW(config-if)#mls qos cos [VALEUR]
```
**Explications** :
- `int [INTERFACE]` : Sélection de l'interface à configurer.
- `switchport mode access` : Définit le mode de l'interface en mode accès.
- `switchport access vlan 30` : Affecte l'interface au VLAN 30.
- `mls qos trust device cisco-phone` : Active la QoS et fait confiance aux étiquettes CoS/DSCP envoyées par un téléphone Cisco.
- `mls qos cos 5` : Affecte une valeur CoS de 5 aux paquets si aucune étiquette n'est présente.
- `mls qos trust dscp` : Configure l'interface pour qu'elle fasse confiance aux étiquettes DSCP pour la priorisation du trafic.
## Etape 2 : Définition d'une class-map sur le routeur
```
Routeur(config)#class-map match-all [LaClasse ]
Routeur(config)#description [Classification de H323] 
Routeur(config)#match protocol [h323]
```
- **Action** : Cette commande crée une nouvelle classe de correspondance nommée `[LaClasse]`. Le `match-all` signifie que tous les critères définis dans cette classe doivent être satisfaits pour qu'un paquet soit considéré comme appartenant à cette classe.
- **Action** : Ajoute une description à la class-map, ici indiquant qu'elle est destinée à la classification du trafic H323 (souvent utilisé pour la signalisation dans la VoIP).
- **Action** : Définit un critère de correspondance pour la classe. Dans ce cas, les paquets utilisant le protocole H323 seront classés dans `[LaClasse]`

## Etape 3 : Création d'une Policy-Map sur le routeur
```
Routeur(config)#policy-map [MaPolitique] 
Routeur(config)#class [LaClasse] 
Routeur(config)#set ip dscp [ef,af,cs] 
Routeur(config)#description [modification du champ dscp à la valeur ef]
```
- **Action** : Crée une nouvelle politique de QoS nommée `[MaPolitique]`. Cette politique définit comment le trafic doit être traité.
- **Action** : Associe la class-map précédemment créée (dans ce cas `[LaClasse]`) à la policy-map. Cela signifie que les actions définies dans la policy-map seront appliquées au trafic qui correspond aux critères de `[LaClasse]`.
- **Action** : Définit une action dans la policy-map qui marque (ou re-marque) les paquets de la classe spécifiée avec une valeur DSCP spécifique (`ef`, `af`, `cs`). Ces valeurs déterminent la priorité et le traitement des paquets dans le réseau.
- **Action** : Ajoute une description à la policy-map, expliquant l'action effectuée, ici indiquant que le champ DSCP des paquets est modifié à la valeur spécifiée (par exemple, `ef`).
## Etape 4 : Application de la policy-map sur une interface 
```
Routeur(config)#interface Serial0/0/0 service-policy output QoS
```
* **Action** : Applique la policy-map nommée `QoS` à l'interface `Serial0/0/0` du routeur pour le trafic sortant. Cela signifie que le trafic passant par cette interface sera traité conformément aux règles définies dans la policy-map `QoS`
## Etape 3 : Vérifier configuration QoS 

### Sur un Switch Cisco

1. **Vérification de la Configuration Générale de la QoS**
   - `show mls qos` : Affiche l'état global de la QoS sur le switch.

2. **Vérification des Paramètres QoS sur une Interface Spécifique**
   - `show mls qos interface [INTERFACE]` : Fournit des détails sur la configuration QoS de l'interface spécifiée.

3. **Vérification des Statistiques de QoS**
   - `show mls qos interface [INTERFACE] statistics` : Montre les statistiques de QoS pour l'interface spécifiée, comme le nombre de paquets marqués.

4. **Vérification de la Configuration de la File d'Attente**
   - `show queueing interface [INTERFACE]` : Permet de voir la configuration de la file d'attente pour l'interface donnée.

5. **Vérification du Mappage de CoS à la Queue**
   - `show mls qos maps cos-queue` : Affiche le mappage de la valeur CoS (Class of Service) aux queues sur le switch.
### Sur un Routeur Cisco

1. **Vérification des Class-Maps et Policy-Maps**
   - `show class-map` : Affiche toutes les class-maps configurées sur le routeur.
   - `show policy-map` : Affiche toutes les policy-maps configurées.

2. **Vérification de la Politique Appliquée à une Interface**
   - `show policy-map interface [INTERFACE]` : Fournit des détails sur les policy-maps appliquées à une interface spécifique, y compris les statistiques de trafic pour chaque classe.

3. **Vérification des Correspondances de Trafic**
   - `show access-lists` : Utile pour voir les listes d'accès utilisées dans les configurations de QoS pour classifier le trafic.

4. **Vérification des Statistiques de QoS**
   - `show policy-map interface [INTERFACE]` : Fournit également des statistiques sur la façon dont les paquets sont traités par les différentes classes et politiques sur l'interface.

# Exemple de sh run 
## 1. Configuration switch 
```
! Configuration de base du Switch

mls qos

interface GigabitEthernet0/1
 description Connection to Cisco Phone
 switchport mode access
 switchport access vlan 30
 mls qos trust device cisco-phone
 mls qos cos 5
 mls qos trust dscp

interface GigabitEthernet0/2
 description Data VLAN Interface
 switchport mode access
 switchport access vlan 30
 mls qos trust cos
 mls qos cos 3
```
## 2. Configuration routeur 
```
! Configuration de base du Routeur

! Configuration des class-maps
class-map match-all VoIP
 match protocol h323

class-map match-all Critique
 match protocol eigrp

class-map match-any Autre
 match protocol http 
 match protocol icmp

class-map match-all FTP
 match protocol ftp

! Configuration des policy-maps
policy-map QoS
 class VoIP
  set ip dscp ef
  description Trafic VoIP - Priorité Haute
 class Critique
  set ip dscp cs6
  description Trafic Critique - EIGRP
 class FTP
  set ip dscp cs5
  description Trafic FTP
 class Autre
  set ip dscp default
  description Autres Trafics

! Application de la politique de QoS aux interfaces
interface Serial0/0/0
 service-policy output QoS


```





1. Commande 
```
SW(config)#int [INTERFACE]
SW(config-if)#mls qos trust device cisco-phone
SW(config-if)#mls qos cos 5
SW(config-if)#mls qos trust dscp
```
2. Commande 
```
SW(config)#int [INTERFACE]
SW(config-if)#switchport mode access
SW(config-if)#switchport access vlan 30
SW(config-if)#mls qos trust cos
SW(config-if)#mls qos cos [VALEUR]
```
3. Verification 
```
SW#show mls qos interface [INTERFACE]
```
4. Routeur 
```
Routeur(config)#class-map match-all LaClasse 
Routeur(config)#description Classification de H323 
Routeur(config)#match protocol h323 
Routeur(config)#policy-map MaPolitique 
Routeur(config)#class LaClasse 
Routeur(config)#set ip dscp ef 
Routeur(config)#description modification du champ dscp à la valeur ef
```
5. Routeur 2 
```
class-map match-all VoIP 
	match protocol h323 
class-map match-all Critique 
	match protocol eigrp 
class-map match-any Autre
	match protocol http 
	match protocol icmp 
class-map match-all FTP 
	match protocol ftp
	
policy-map QoS 
	class VoIP 
		set ip dscp ef 
	class Critique 
		set ip dscp cs6 
	class FTP 
		set ip dscp cs5 
	class Autre 
		set ip dscp default

interface Serial0/0/0 service-policy output QoS
```
6. Routeur 3 
```
class-map match-all VoIP 
	match protocol h323 
class-map match-all Critique 
	match protocol eigrp 
class-map match-any Autre 
	match protocol http 
	match protocol icmp 
class-map match-all FTP 
	match protocol ftp

interface Serial0/0/0 service-policy output QoS
```