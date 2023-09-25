# Guide BGP

## 1) Généralités

- **BGP** : C'est l'acronyme de _**Border Gateway Protocol**_.
- BGP est surnommé le **"glue of the internet"** (la colle de l'Internet) car il est la charnière qui permet aux différentes parties du réseau mondial de communiquer entre elles.
- Il est fondamental de comprendre que BGP est un protocole de type **path vector**. Cela signifie qu'il conserve un enregistrement complet du chemin d'accès vers les réseaux de destination, plutôt que de se baser uniquement sur le comptage de sauts ou d'autres métriques. Cette caractéristique permet d'éviter les boucles de routage.
- **AS** : Signifie _**Autonomous System**_. Il s'agit d'un ensemble de réseaux IP ayant une politique de routage propre.
- L'utilité première de BGP est de permettre la communication entre différents AS.
- **ASN** : C'est l'identifiant unique d'un AS. BGP utilise cet identifiant pour référencer l'AS.
    - Géré par _**IANA**_, l'ASN est composé de :
        - 16 bits
        - _**Réservé**_ : 64496-64534
        - _**Privés**_ : 64512-65534
- Il est crucial de ne jamais redistribuer de routes BGP vers d'autres protocoles au sein du LAN. Cela pourrait entraîner une explosion du tableau de routage.
- BGP est un _**Policy Base Routing Protocol**_. Cela signifie que les paquets sont soumis à une route map avant d'être acheminés.
- C'est le protocole standardisé pour le _**routage externe**_, c'est-à-dire en dehors du LAN. BGP connecte différents _**systèmes autonomes**_ entre eux, qui à l'intérieur, peuvent utiliser des protocoles de routage internes comme OSPF, RIP ou EIGRP.
- En termes de BGP, une adjacence est aussi appelée relation de peering ou BGP Neighbor.

## 2) Principes

- BGP est le protocole responsable de la liaison entre différents systèmes autonomes.
- Sa caractéristique principale est d'être un protocole à vecteur de chemin : il ne se contente pas de définir une destination, mais également l'ensemble du chemin (PATH) pour y parvenir.
    - Cela permet d'éviter les boucles de routage en empruntant des chemins déjà connus.
- BGP fonctionne au-dessus du protocole TCP.
- La dernière version de BGP est la **version 4** qui offre le support du VLSM (Variable Length Subnet Masking).
- **BGP-MP (MultiProtocol)** : Une extension de BGP qui supporte IPV6.
- La **convergence** de BGP peut être plus lente que celle des IGP. Cette lenteur est souvent intentionnelle afin d'éviter des changements de routage trop rapides et potentiellement instables à l'échelle de l'Internet.
- **BGP Sessions** : BGP établit des sessions avec d'autres pairs (peers) BGP. Ces sessions sont de deux types :
    - **eBGP** : Entre routeurs appartenant à différents AS.
    - **iBGP** : Entre routeurs au sein du même AS.
- Les **attributs BGP** sont essentiels à la prise de décision en matière de routage. Ils comprennent notamment AS-PATH, NEXT-HOP, MED (Metric), LOCAL-PREFERENCE, et COMMUNITIES.

## 3) Comparaison entre IGP et BGP

- IGP est destiné à être utilisé à l'intérieur d'un AS, tandis que BGP est conçu pour opérer entre différents AS.
- BGP offre une plus grande flexibilité pour définir les chemins et prendre des décisions de routage. Cette souplesse est rendue possible grâce à ses nombreux attributs, qui peuvent être modifiés pour influencer les décisions.
- De par sa complexité et sa richesse en termes d'attributs, BGP est souvent considéré comme un protocole avancé.
- IGP base ses décisions de routage sur la métrique du meilleur chemin.
- BGP, en revanche, est un :
    - _**Policy Based Routing Protocol**_
    - Il contrôle le routage en utilisant de multiples attributs (BGP attributes)
    - L'AS-PATH décrit la liste des ASN que le routeur doit traverser pour atteindre une destination
    - Il peut optimiser l'utilisation de la bande passante en manipulant les attributs BGP.
- Scénarios d'utilisation de BGP :
    - L'AS a plusieurs connexions vers d'autres AS.
    - L’AS autorise le trafic de transit pour atteindre d’autres AS.
- Cas où BGP n'est pas recommandé :
    - Connexion unique vers Internet ou vers un autre AS.
    - Ressources hardware insuffisantes (CPU, RAM).
    - Absence de maîtrise du fonctionnement de BGP et de sa gestion des routes et des politiques PBR.
- Dans ces situations, il est préférable d'opter pour des routes statiques ou une route par défaut.

## 4) Autres points à considérer

- **BGP Route Reflectors** : Dans un réseau iBGP, chaque routeur doit établir une session avec tous les autres routeurs. Cette pleine maillage peut devenir complexe. Les "Route Reflectors" offrent une solution en permettant à certains routeurs de relayer les routes apprises aux autres routeurs de l'AS.
- **BGP Confederations** : C'est une autre réponse au défi de la pleine connectivité iBGP. Les confédérations subdivisent un AS en plusieurs petits AS, améliorant ainsi la scalabilité.
- **BGP Filtering** : Le filtrage est essentiel pour définir quelles routes sont acceptées et annoncées via BGP.
- **BGP Peering** : La sécurité des sessions BGP est primordiale car BGP peut être cible d'attaques. L'utilisation de mécanismes d'authentification est recommandée pour sécuriser les sessions eBGP.

## 5) Configuration BGP
* Activer protocole BGP 
```
R1(config)#router bgp @ASN
```
* Annoncer son réseau
```
R1(config-rtr)#network @mon_reseau mask @masque
```
* Annoncer ses voisins (ASN)
```
R1(config-rtr)#neighbor @IP_INT_VOISIN remote-as @ASN_voisin
```
* Modifier router-id BGP
```
R1(config-rtr)#bgp router-id X.X.X.X
```
* Exemple de configuration
```
R1(config)#router bgp 65329
R1(config-rtr)#bgp router-id 1.1.1.1
R1(config-rtr)#network 192.168.1.0 mask 255.255.255.0
R1(config-rtr)#neighbor 10.0.0.2 remote-as 65330
```
