# Guide BGP

# 1) Fondamentaux de BGP
## But et généralités
- **BGP** = **Border Gateway Protocol**
- Protocole de routage extérieur
- Rend possible l'interconnexion entre différents AS. 
- Échanger les blocs d'adresses IP et leurs masques de sous-réseau associés entre AS. 
- Prend en charge des réseaux de tailles et de topologies variées.
- Utilise TCP sur le port 179
- BGP est un protocole de routage de type **"path vector"** = Regarde le chemin complet pour arriver à destination plutôt que juste le meilleur prochain saut
![BGP1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP1.png)
## Quand utiliser BGP
* Contrôle du trafic sortant et la manière dont le réseau est accessible de l'extérieur
* Annoncer des préfixes IP pour rendre accessible des services hébergés aux autres AS
* Spécifier des politiques de routage qui influencent la sélection de chemin via des route-map(performance/sécurité)
![BGP2.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP2.png)
## Définition d'un AS
* Ensemble de réseaux sous une seule et même politique de routage (IGP)
* Contrôlé par une organisation 
	➢ Entreprise (Thales) 
	➢ Organismes publics (Université, Renater) 
	➢ ISP (Free, Orange, SFR, …) 
* Identifié par un ASN (Autonomous System Number) unique 
	➢ Attribué par les Registres Internet Régionaux (RIR). 
	* France (RIPE NCC) ; 
	* USA (ARIN)
* Plage publique ASN = AS1 – AS 64495 
* Plage privée ASN = AS 64512 – AS 65534
![BGP3.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP3.png)
![BGP4.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP4.png)

# 2) Type de BGP

## eBGP vs iBGP
|  | eBGP | iBGP |
| ---- | ---- | ---- |
| **Utilité** | Routage entre différents AS | Routage à l'intérieur d'un même AS |
| **Informations échangées** | - Annonce les préfixes réseau internes de son propre système autonome (AS) à un autre AS | - Annonce les préfixes réseau qu'il a appris via ses liens eBGP à d'autres routeurs à l'intérieur du même AS. <br>- Échange les informations de route via un Route Reflector |
| **Peering** | Nécessite une connexion directe entre les AS participants. | Fonctionne sans connexion directe entre tous les routeurs internes |
| **Sélection de chemin** | Préfère généralement les chemins avec le plus petit nombre de sauts | Ne modifie pas les attributs des routes lors de leur propagation à travers le réseau interne |

![BGP5.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP5.png)
## Multihoming
* Connexion d’un réseau à plus d'un fournisseur d'accès Internet (ISP) pour augmenter la redondance et la disponibilité.
* Permet au réseau de communiquer ses préférences de routage à plusieurs fournisseurs et de choisir le meilleur chemin.
* Réalisé avec eBGP, en établissant des sessions BGP séparées avec chaque fournisseur d'accès Internet.
![BGP6.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP6.png)
# 3) Fonctionnement 

## Peering (Session entre 2 routeurs BGP)
* Établissement d’une connexion directe entre deux routeurs BGP pour échanger des informations de routage.
* Sessions configurées sur eBGP entre AS différents ou sur iBGP à l'intérieur du même AS.
* Nécessite une configuration manuelle et inclut : 
	* ➢ l'échange des adresses des pairs ; 
	* ➢ la configuration des politiques de routage.
![BGP7.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP7.png)

## Messages BGP (Entre 2 routeurs BGP )
| Message      | Fonction |
|--------------|----------|
| **OPEN**     | - Initialisation d'une connexion BGP entre deux routeurs<br>- Sert à négocier les paramètres de la session (numéro d'AS, ID de routeur...) |
| **UPDATE**   | - Annoncer de nouvelles routes<br>- Retirer des routes précédemment annoncées<br>- Transportent des informations sur les attributs de chemin |
| **KEEPALIVE**| - Indiquer qu'une connexion est toujours active<br>- Maintenir la session BGP ouverte et confirme que les deux parties sont toujours disponibles |
| **NOTIFICATION** | - Signaler des erreurs ou des problèmes dans la session BGP |
## Attributs de chemin/routes BGP 
| Attribut de chemin | Description |
|--------------------|-------------|
| **ORIGIN**         | - Indique l'origine de la mise à jour de routage<br>- Valeurs possibles : IGP (obsolète) et Incomplete (moyen non spécifié à BGP)<br>- Préférence ORIGIN IGP over EGP et EGP over Incomplete |
| **AS_PATH**        | - Liste les numéros d'AS que la mise à jour de routage a traversé<br>- Éviter les boucles de routage sureBGP (Cluster List pour iBGP)<br>- Plus le chemin est court, plus il est préféré |
| **NEXT_HOP**       | - Adresse du prochain routeur pour atteindre la destination annoncée<br>- eBGP : adresse de l'interface du routeur qui annonce la route<br>- iBGP : adresse du routeur d'où provient la route ou adresse du peer eBGP d'où la route a été apprise |
| **Weight**         | - Spécifique à Cisco<br>- Appliqué localement sur le routeur et non transmis à d'autres routeurs<br>- Nombre entre 0 et 65535 (65535 étant la route la plus préférée)<br>- Les routes locales ont un poids de 32 768 (par défaut) / celles apprises de pairs ont un poids de 0 |
# 4) Selection de chemin BGP
* BGP donne des attributs à chacune de ses routes apprises. 
* Certains attributs ont un priorité dans l'algorithme de BESTPATH de BGP.
* On peut donc influencer quelles routes ou AS seront préférées par rapport à d'autre selon nos critères de politique de routage.

| Priorité | Attribut BGP | Description |
| ---- | ---- | ---- |
| 1 | **Weight** | - Spécifique à Cisco, local au routeur. Préfère le chemin avec le poids le plus élevé. |
| 2 | **Local Preference** | - Chemin au sein de l'AS. Une préférence locale plus élevée est préférée. |
| 3 | **AS Path** | - Chemin qui traverse le moins d'AS. Liste des AS est courte : le chemin est préféré. |
| 4 | **Origin** | - Préfère les chemins avec l'origine la plus fiable. (IGP > EGP > Incomplete) |
| 5 | **MED (Multi Exit Discriminator)** | - Compare les chemins du même AS voisin.<br>- Le chemin avec le MED le plus bas est préféré. |
| 6 | **eBGP vs iBGP** | - Les chemins appris via eBGP sont préférés sur ceux appris via iBGP. |
| 7 | **Proximité IGP vers le prochain saut (Next Hop)** | - Préfère le chemin avec la métrique IGP la plus basse vers le prochain saut BGP. |
| 8 | **Autres critères** | - Chemin le plus ancien, ID du routeur le plus bas, et l'adresse du voisin la plus basse. |
## Exemple 1 : AS 5 vers AS 1 basé sur l'AS PATH uniquement
![BGP8.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP8.png)
## Exemple 2 : Extrait d'un bestpath BGP
![BGP9.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP9.png)
# 5) Sécurité BGP
## Authentification
* Authentification par mot de passe possible pour prévenir les connexions non autorisées. 
* Utilisation de MD5 pour sécuriser les échanges entre pairs BGP 
	* ➢ Empêche les attaques de type "man-in-the-middle". 
	* ➢ Détournement de trafic malveillant
![BGP10.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP10.png)
## Améliorer la Sécurité avec des Configurations Avancées
* Implémenter un filtrage rigoureux des annonces de routes 
	* ➢ Éviter la propagation de routes malveillantes ou incorrectes. 
* Utiliser des ACLs pour contrôler l'accès aux routeurs BGP et aux ressources réseau. 
* Utiliser RPKI (Resource Public Key Infrastructure) pour valider l'origine des annonces de routes 
	* ➢ Réduit le risque de détournement de préfixe
![BGP11.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/BGP11.png)

# 6) Configuration de BGP

## Configuration classique d'un peering entre 2 AS
* Activer protocole BGP 
```
R1(config)#router bgp [ASN]
```
* Annoncer son réseau
```
R1(config-rtr)#network [NET_LAN] mask [NETMASK]
```
* Annoncer ses voisins (ASN)
```
R1(config-rtr)#neighbor [IP_INT_VOISIN] remote-as [ASN_VOISIN]
```
* Modifier router-id BGP
```
R1(config-rtr)#bgp router-id [X.X.X.X]
```
* Exemple de configuration
```
R1(config)#router bgp 65329
R1(config-rtr)#bgp router-id 1.1.1.1
R1(config-rtr)#network 192.168.1.0 mask 255.255.255.0
R1(config-rtr)#neighbor 10.0.0.2 remote-as 65330
```

## Modification des attributs de chemin dans BGP

* **Modifier l'attribut ORIGIN** (indiquer l'origine de la route annoncée)
```
route-map [ROUTEMAP_NAME] permit 10
	set origin [igp | egp | incomplete]

router bgp [ASN]
	network [NET_LAN] mask [NETMASK]
	neighbor [IP_INT_VOISIN] route-map [ROUTEMAP_NAME] [in|out]
```

* **Modifier l'attribut AS_PATH** (influencer le chemin BGP)
```
route-map [ROUTEMAP_NAME] permit 10
	set as-path prepend [ASN_SEQ]

router bgp [ASN]
	neighbor [IP_INT_VOISIN] route-map [ROUTEMAP_NAME] [in|out]
```

* **Modifier l'attribut NEXT_HOP** (spécifier le prochain saut pour une route BGP)
```
route-map [ROUTEMAP_NAME] permit 10
	set ip next-hop [IP_NEXT_HOP]

router bgp [ASN]
	neighbor [IP_INT_VOISIN] route-map [SET_NEXTHOP] [in|out]
```

* **Modifier l'attribut WEIGHT** (influencer le choix de la route localement)
```
router bgp [ASN]
	neighbor [IP_INT_VOISIN] weight [WEIGHT_VALUE]
```

* **Exemple de configuration avec modification des attributs**
```
route-map SET_ORIGIN permit 10
	set origin igp
	
router bgp 65329
	bgp router-id 1.1.1.1
	network 192.168.1.0 mask 255.255.255.0
	neighbor 10.0.0.2 remote-as 65330
	neighbor 10.0.0.2 weight 200
	neighbor 10.0.0.2 route-map SET_ORIGIN out
```
## 4) Autres points à approndir

- **BGP Route Reflectors** : Dans un réseau iBGP, chaque routeur doit établir une session avec tous les autres routeurs. Cette pleine maillage peut devenir complexe. Les "Route Reflectors" offrent une solution en permettant à certains routeurs de relayer les routes apprises aux autres routeurs de l'AS.
- **BGP Confederations** 
- **BGP Filtering**

