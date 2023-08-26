# 1) Qu'est-ce que le STP ?
- STP, pour "Spanning Tree Protocol", est un protocole de niveau 2 du modèle OSI (Liaison de données).
- Il est principalement associé aux commutateurs (switchs) Ethernet.
- Il agit sur les trames, et non les paquets.

# 2) Pourquoi utilise-t-on le STP ?
- STP empêche les boucles de commutation dans les réseaux, assurant ainsi que le réseau reste opérationnel.
- Les trames Ethernet ne possèdent pas de TTL (Time-To-Live), ce qui signifie qu'une trame pourrait circuler indéfiniment sur un réseau en boucle, causant des tempêtes de diffusion.
- Une boucle dans le réseau sans STP pourrait provoquer une congestion, et même un dysfonctionnement, des équipements de réseau.
- Sans STP, le réseau pourrait emprunter des chemins suboptimaux, ralentissant ainsi la transmission de données.
# 3) Comment fonctionne le STP ?
- Par défaut, STP est activé sur la plupart des commutateurs modernes. Lorsqu'un commutateur est allumé ou redémarré, il peut y avoir un délai (souvent 30 secondes) pendant lequel STP s'exécute avant que le réseau soit pleinement opérationnel.
## Étape 1 : Élection du commutateur racine (Root Bridge)
- Tous les commutateurs échangent des BPDUs (Bridge Protocol Data Units) pour élire un commutateur racine.
- Le choix se base sur :
    - 1 - La priorité la plus basse (par défaut, toutes ont la même valeur, donc on passe au critère suivant)
    - 2 - L'adresse MAC la plus basse (en cas d'égalité de priorité)
## Étape 2 : Détermination du port racine (Root Port, RP)
- Chaque commutateur détermine son port racine, c'est-à-dire le port qui a le chemin le plus court vers le commutateur racine.
- Si un commutateur a plusieurs chemins vers la racine avec des coûts équivalents, le choix se fera selon :
    - 1 - Le coût le plus bas de la liaison (path cost)
    - 2 - La priorité la plus basse du port
    - 3 - L'adresse MAC la plus basse du commutateur voisin
## Étape 3 : Désignation des ports désignés (Designated Ports, DP)
- Le port désigné pour un segment de réseau est le seul port sur ce segment autorisé à transmettre des trames vers ce segment.
- Chaque segment a un seul port désigné.
- Si deux commutateurs sur un segment ont des coûts équivalents pour devenir le port désigné, le choix se fera selon :
    - 1 - La priorité du port la plus basse
    - 2 - L'adresse MAC la plus basse du commutateur
## Étape 4 : Mise en état de blocage des ports non désignés
- Pour éviter les boucles, STP met en état de blocage tous les ports qui ne sont ni des ports racine ni des ports désignés. Ces ports peuvent être réactivés en cas de défaillance d'autres liens.
## Précisions sur l'élection
- Au départ, chaque commutateur se considère comme le commutateur racine. Grâce aux BPDUs échangés, ils s'accordent sur le véritable commutateur racine. Une fois le commutateur racine élu, il reste en place jusqu'à un changement majeur dans la topologie réseau.
# 4) Différents modes de STP

## PVST+ (Per-VLAN Spanning Tree Plus)

- PVST+ est une amélioration Cisco de l'original STP qui supporte le spanning-tree pour chaque VLAN individuellement. Chaque VLAN a donc son propre arbre couvrant, ce qui permet d'avoir une flexibilité pour configurer différents chemins redondants pour différents VLANs.
- Il utilise des BPDUs standard IEEE pour le tunneling sur les troncs.

## Rapid PVST+ (Rapid Per-VLAN Spanning Tree Plus)

- Rapid PVST+ est basé sur le protocole IEEE 802.1w RSTP (Rapid Spanning Tree Protocol) et permet une convergence plus rapide que le STP traditionnel ou le PVST+.
- Comme le PVST+, il maintient un spanning tree par VLAN, permettant une configuration flexible.
- Les temps de transition sont généralement moins de 10 secondes, comparés aux 30-50 secondes du PVST+.

## MST (Multiple Spanning Tree)

- Basé sur l'IEEE 802.1s, MST permet de mapper plusieurs VLANs dans un seul arbre couvrant.
- Contrairement à PVST+ qui maintient un STP pour chaque VLAN, MST réduit la charge sur le réseau en regroupant les VLANs en instances MST.
- C'est utile pour les réseaux avec de nombreux VLANs pour réduire la charge CPU et la bande passante nécessaire pour le STP.

# 5) Fonctions de protection STP

## PortFast

- PortFast est une fonction Cisco qui permet à un port de transitionner immédiatement de la mise en blocage à la mise en écoute, puis en apprentissage et enfin en transfert. Il est généralement utilisé pour les ports connectés à des hôtes, pour accélérer leur mise en ligne.
- **Attention** : Ne jamais activer PortFast sur un port connecté à un autre commutateur. Cela pourrait provoquer des boucles.

## BPDU Guard

- BPDU Guard est une fonction de sécurité qui désactive un port si des BPDUs sont reçus sur ce port. Comme PortFast est conçu pour être utilisé sur des ports connectés à des hôtes, il ne devrait pas recevoir de BPDUs.
- Si un dispositif malveillant ou mal configuré était connecté à ce port et commençait à envoyer des BPDUs, BPDU Guard le désactiverait pour protéger le réseau.
- C'est une excellente sécurité pour les ports où vous avez activé PortFast, car cela empêche quelqu'un de connecter un commutateur non autorisé et de potentiellement provoquer des boucles.
# 6) Configuration de STP 
## Vérification du STP

```
show spanning-tree [vlan vlan-id]
```
## Définir la priorité d'un commutateur

Pour changer la priorité d'un commutateur afin de l'influencer pour devenir le commutateur racine (Root Bridge) ou pour éviter qu'il le devienne, utilisez :
```
`spanning-tree vlan [vlan-id] priority [value]`
```
La valeur de priorité est un multiple de 4096, allant de 0 à 61440. Plus la valeur est basse, plus la priorité est élevée.

## Configurer un commutateur pour qu'il devienne le Root Bridge

Pour forcer un commutateur à devenir le Root Bridge, vous pouvez utiliser une macro :

```
`spanning-tree vlan [vlan-id] root primary`
```
Cette commande ajuste la priorité du commutateur à la valeur la plus basse dans le réseau pour le VLAN spécifié.

## Configurer le coût du chemin

Pour configurer manuellement le coût d'un port, utilisez :

```
`interface [interface-id] spanning-tree cost [value]`
```
## Configurer le mode STP

Cisco prend en charge plusieurs variantes de STP, dont PVST+, Rapid PVST+ et MST. Pour configurer le mode STP sur un commutateur, utilisez :

```
`spanning-tree mode {pvst | rapid-pvst | mst}`
```
## Protection STP

### PortFast
Accélère la connexion des hôtes en passant un port directement de la mise en blocage à la mise en écoute. Utilisé pour les ports connectés à des hôtes uniques :
```
`interface [interface-id] spanning-tree portfast`
```
**Attention** : Ne jamais activer PortFast sur un port connecté à un autre commutateur, cela pourrait provoquer des boucles.
### BPDU Guard
Désactive un port qui reçoit un BPDU, généralement utilisé en combinaison avec PortFast :

```
interface [interface-id] spanning-tree bpduguard enable
```