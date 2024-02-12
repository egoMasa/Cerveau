# Comprendre la différence entre la commutation et le routage

# I) Commutation
## Principe de commutation
- La commutation est une technique utilisée pour transmettre des données (trames) au sein d'un même réseau.
- Elle connecte plusieurs périphériques sur un réseau local (LAN).
- Les commutateurs (switches) sont responsables de cette opération.
- Elle est basée sur l'adresse MAC de la trame.

❗ La commutation n'est possible que pour les nœuds au sein d'un même sous réseau, si une trame est à destination d'un autre sous réseau, il faut passer par un routeur
### 1. Processus d'Envoi d'une Trame (Cas où le Port de Destination n'est pas Connu)
- **Transmission Initiale** :
    - Un appareil (par exemple, PC1) envoie une trame avec une adresse MAC de destination.
    - Si le switch auquel PC1 est connecté (disons Switch A) ne connaît pas le port associé à cette adresse MAC, il doit déterminer comment acheminer la trame.
- **Flood** :
    - Switch A effectue un "flood", envoyant la trame sur tous ses ports actifs, à l'exception du port sur lequel la trame a été reçue.
    - Cela permet à la trame d'atteindre potentiellement le destinataire, même si l'emplacement exact n'est pas connu.
### 2. Processus d'Apprentissage des Adresses MAC par les Switches Intermédiaires
- **Apprentissage par Observation** :
    - Chaque fois qu'un switch reçoit une trame sur un port, il enregistre l'adresse MAC source de la trame et associe cette adresse au port de réception dans sa table d'adresses MAC.
    - Cela permet au switch de "se souvenir" de l'emplacement des appareils sur le réseau.
- **Acheminement des Trames Futures** :
    - Lorsque le même switch reçoit à nouveau une trame destinée à cette adresse MAC, il sait désormais sur quel port la transmettre directement, sans nécessiter un nouveau flood.
### 3. Processus de Retour de la Trame vers son Expéditeur
- **Trame de Réponse** :
    - Lorsque le destinataire (disons PC2) répond, il crée une trame de réponse avec l'adresse MAC de l'expéditeur initial (PC1) comme destination.
- **Transmission via Switches Intermédiaires** :
    - La trame de réponse traverse les switches intermédiaires (Switch D, C, B, A). Chaque switch utilise sa table d'adresses MAC pour diriger la trame.
    - Ces switches ont probablement appris l'adresse MAC de PC1 lors de l'acheminement initial, ce qui rend le chemin de retour plus direct et efficace.
- **Arrivée à l'Expéditeur** :
    - La trame de réponse atteint finalement Switch A, qui la transmet directement à PC1, l'expéditeur initial.
### Points Clés
- **Indépendance des Switches** : Chaque switch opère de manière indépendante, se basant sur sa propre table d'adresses MAC pour acheminer les trames.
- **Efficacité et Apprentissage** : L'efficacité du réseau augmente avec l'apprentissage des adresses MAC, réduisant la nécessité de floods répétés.
- **Pas de Communication Inter-Switch pour l'Acheminement** : Il n'y a pas de communication nécessaire entre les switches pour acheminer les trames; chaque switch décide de manière autonome.
## Table d'adresse MAC
* Chaque commutateur possède sa propre table d'adresse MAC qui relie un port à l'adresse MAC du périphérique connecté sur ce port
* Une table d'adresse MAC peut être configuré dans 2 modes différents : 
	* ***Dynamique*** (défaut) :  Le commutateur apprendra automatiquement les adresses MAC et remplira sa table d'adresses MAC (table CAM) en examinant l'adresse MAC source des trames entrantes et des trames d'inondation s'il ne sait pas où transférer la trame
	* ***Statique*** : Pour empécher qu'un attaquant usurpe une certaine adresse MAC pour modifier les entrées de la table d'adresses MAC, on configure manuellement les entrées dans la table d'adresses MAC. Une entrée statique remplacera toujours les entrées dynamiques.
* Consulter la table d'adresse MAC d'un commutateur 
```
show mac address-table dynamic
show mac address-table dynamic [MAC]
show mac address-table dynamic interface [interface]
```
* Vider la table d'adresse MAC
```
clear mac address-table dynamic
```
* Afficher le temps de vieillissement en seconde d'une adresse MAC (durée pendant laquelle une adresse MAC reste dans la table d'adresses MAC du commutateur avant d'être automatiquement supprimée si elle n'est plus utilisée ou vue sur le réseau). Si le commutateur ne voit pas une adresse MAC particulière pendant X secondes, elle sera supprimée de la table d'adresses MAC
```
SW1#show mac address-table aging-time 
Global Aging Time:  300
Vlan    Aging Time
----    ----------
```
* Transformer une entrée dynamique en entrée statique
```
mac address-table static [MAC] [vlan X] interface [interface]
show mac address-table static
```
* Empecher le traffic vers une adresse MAC
```
SW1(config)#mac address-table static [MAC] vlan [NUM] drop
```

## Mode duplex et vitesse
* Pour une communication entre 2 ports fonctionne, il faut respecter 2 paramètres 
* **Mode Duplex** : Le mode duplex d'un port de commutateur fait référence à la manière dont les données sont transmises entre le commutateur et les appareils connectés.
    - **Full Duplex** : Permet la transmission de données dans les deux sens simultanément. Cela signifie que l'appareil peut envoyer et recevoir des données en même temps, ce qui améliore les performances.
    - **Half Duplex** : Limite la transmission de données à un seul sens à la fois. L'appareil ne peut soit envoyer soit recevoir des données à un moment donné, ce qui peut conduire à des collisions si plusieurs appareils tentent de communiquer simultanément.
- **Même Vitesse de Transmission** : Les deux ports doivent fonctionner à la même vitesse (par exemple, 10Mb/s, 100Mb/s, 1Gb/s, etc.). Si les vitesses sont différentes, la communication peut être altérée ou même impossible. La négociation automatique (auto-negotiation) permet souvent de résoudre ce problème en sélectionnant la vitesse maximale commune supportée par les deux appareils.
- Afficher le mode en cours et vitesse de transmission
```
show interfaces fa0/1

Auto-duplex, 10Mb/s, media type is 10/100BaseTX
Half-duplex, Auto-speed, media type is 10/100BaseTX
```
* Configurer vitesse du port et mode duplex
```
interface fa0/3
	speed [auto]
	duplex [auto]
```

![[commutation1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/commutation1.png)
## II) Routage

### Principe
- Le routage permet d'acheminer des paquets entre différents réseaux.
- Les routeurs sont les dispositifs responsables de cette opération.
- Ils utilisent les adresses IP pour prendre leurs décisions.
- Le chemin emprunté peut être déterminé à l'aide d'algorithmes de routage.
- Les informations de couche 2 (comme l'adresse MAC) sont remplacées à chaque saut par un routeur.
❗ Un routeur ne peut pas avoir deux interfaces dans le même sous-réseau IP, chaque interface sur un routeur doit être connectée à un sous-réseau distinct
❗ La logique est : un switch permet de communiquer sur un seul sous réseau commun, un routeur permet de lier plusieurs sous réseau différent

![routage](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/routage1.png)
### Table de Routage
- **Construction** : Chaque routeur maintient une table de routage qui contient des informations sur les réseaux de destination et les interfaces ou prochains sauts (next hops) associés pour y accéder.
- **Informations Contenues** : La table de routage liste généralement le réseau de destination, le masque de sous-réseau, l'interface de sortie ou l'adresse du prochain routeur (next hop), et parfois des métriques pour déterminer le meilleur chemin.
### Mise à Jour de la Table de Routage
- **Routage Statique** :
    - Dans les configurations de routage statique, un administrateur réseau configure manuellement les routes dans la table de routage.
    - Par exemple, l'administrateur peut spécifier que pour atteindre le réseau 192.168.2.0/24, le paquet doit être envoyé vers l'adresse IP de R2.
- **Routage Dynamique** :
    - Dans le routage dynamique, les routeurs utilisent des protocoles de routage (comme OSPF, BGP, EIGRP) pour échanger automatiquement des informations sur les réseaux.
    - Ces protocoles permettent aux routeurs de découvrir les réseaux disponibles et de construire dynamiquement des tables de routage qui reflètent la topologie actuelle du réseau.
### Processus de routage de paquet
#### 1. Envoi du Paquet par PC1
- **Initiation de la Communication** :
    - PC1 crée un paquet destiné à PC2. Il détermine que PC2 est sur un réseau différent car il compare l'adresse IP de destination avec son propre masque de sous-réseau.
- **Envoi au Gateway/Routeur par Défaut** :
    - Ne pouvant pas communiquer directement avec PC2, PC1 envoie le paquet à sa passerelle par défaut, qui est le routeur.
#### 2. Transmission par les Switches
- **Passage par le Premier Switch** :
    - Le paquet passe d'abord par le switch auquel PC1 est connecté. Ce switch envoie le paquet vers le routeur sans avoir à se soucier des adresses IP, car il opère au niveau 2 (couche liaison de données).
#### 3. Processus de Routage par le Routeur

##### 3.1 Cas ou routeur directement connecté au sous-réseau de destination
- **Réception par le Routeur** :
    - Le routeur reçoit le paquet sur l'interface connectée au sous-réseau de PC1.
- **Détermination du Chemin** :
    - Le routeur examine l'adresse IP de destination du paquet (celle de PC2) et consulte sa table de routage pour déterminer sur quelle interface il doit envoyer le paquet pour atteindre le sous-réseau de PC2.
- **Envoi vers le Deuxième Sous-réseau** :
    - Une fois le chemin déterminé, le routeur envoie le paquet sur son interface connectée au sous-réseau de PC2.
##### 3.2 Cas ou routeur directement non connecté au sous-réseau de destination
- **Consultation de la Table de Routage** : Lorsque R1 reçoit un paquet destiné à un sous-réseau auquel il n'est pas directement connecté (par exemple, le sous-réseau de PC2), il consulte sa table de routage pour trouver une route vers ce sous-réseau.
    
- **Trouver le Prochain Saut (Next Hop)** : La table de routage indique non seulement la destination (le sous-réseau cible), mais aussi l'adresse du prochain saut (next hop) ou l'interface de sortie à utiliser pour se rapprocher de cette destination. Le prochain saut est souvent l'adresse IP d'un autre routeur (comme R2 ou R3), qui est sur le chemin vers le sous-réseau de destination.
    - Par exemple, si R1 a un paquet destiné au sous-réseau 192.168.2.0/24 (sous-réseau de PC2) et qu'il n'est pas directement connecté à ce sous-réseau, il recherchera dans sa table de routage pour trouver un enregistrement correspondant à cette destination.
    - La table de routage peut indiquer que le meilleur chemin pour atteindre ce sous-réseau passe par R2. Dans ce cas, le prochain saut sera l'adresse IP de R2.
- **Acheminement du Paquet** : R1 envoie ensuite le paquet à l'adresse du prochain saut (dans cet exemple, R2) via l'interface appropriée.
- **Processus au Routeur Suivant** : Lorsque R2 reçoit le paquet, il répète le même processus : il consulte sa propre table de routage pour déterminer comment acheminer le paquet. Si R2 est directement connecté au sous-réseau de destination, il envoie le paquet directement à ce réseau. Sinon, il le transmet au prochain saut indiqué dans sa table de routage.
##### Points Clés
- **Tables de Routage Interconnectées** : Chaque routeur utilise sa propre table de routage, mais ces tables sont interconnectées en termes de fonctionnalité. Elles dirigent collectivement le paquet à travers le réseau en passant de saut en saut.
- **Métriques de Chemin** : Les routeurs choisissent les chemins basés sur des métriques qui peuvent inclure le nombre de sauts, la bande passante, la latence, ou d'autres facteurs de coût. Ceci est particulièrement vrai dans des protocoles de routage dynamiques comme OSPF.
###### Exemple de Table de Routage pour R1
|Destination|Masque|Prochain Saut|Interface de Sortie|Coût|
|---|---|---|---|---|
|192.168.1.0|255.255.255.0|Directement connecté|Eth0|0|
|192.168.2.0|255.255.255.0|10.0.0.2|Eth1|10|
|192.168.3.0|255.255.255.0|10.0.0.3|Eth1|20|

Dans cet exemple, R1 est directement connecté au sous-réseau 192.168.1.0/24 (donc, le coût est de 0 et il est indiqué comme "Directement connecté"). Pour atteindre les autres sous-réseaux, il doit passer par R2 ou R3, comme indiqué dans les colonnes "Prochain Saut" et "Coût".

#### 4. Transmission Finale vers PC2
- **Passage par le Deuxième Switch** :
    - Le paquet arrive au switch connecté au sous-réseau de PC2. Ce switch, en utilisant sa table d'adresses MAC, envoie le paquet à PC2.
- **Réception par PC2** :
    - PC2 reçoit le paquet et, si nécessaire, envoie une réponse qui suivra un processus similaire en sens inverse pour retourner à PC1.
### Cas particuliers
- **Routage sur liaison série** : Lors d'une connexion point-à-point, le routeur encapsule le paquet dans le format de trame approprié pour l'interface de sortie (par exemple, HDLC ou PPP). Les adresses de couche 2 ne sont pas nécessaires dans ce contexte.
- **Routage sur liaison normale** : Les adresses MAC source et destination changent à chaque passage par un routeur, tandis que les adresses IP restent constantes tout au long du chemin.
### Modifications des champs
- Quand un hôte A envoie un paquet vers un hôte B via un routeur :
    1. L'adresse MAC source est celle de l'hôte A, l'adresse MAC destination est celle de la passerelle (le routeur).
    2. Quand le routeur reçoit le paquet, il change l'adresse MAC source à celle de son interface de sortie et l'adresse MAC destination à celle du prochain saut ou de l'hôte B si celui-ci est sur le réseau directement connecté.
    3. Sur une liaison série, les informations de couche 2 peuvent ne pas être utilisées.
