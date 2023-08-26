# Point-to-Point Protocol (PPP)

# 1) Introduction

- **PPP** est un protocole de couche de liaison de données utilisé pour établir une connexion directe entre deux nœuds.
- Il fonctionne sur une **liaison série** telle que les liaisons téléphoniques ou les liaisons optiques.
- Il est fréquemment utilisé pour les connexions Internet via des modems.
- PPP est capable de gérer la **multiplexion** de différents protocoles de couche réseau.
- Offre des fonctionnalités telles que l'**authentification**, la **compression** et l'**encryption**.
- Termes usuels :
    - **DTE (Data Terminal Equipment)** : Équipement terminal de données, souvent l'utilisateur final.
    - **DCE (Data Communication Equipment)** : Équipement de communication de données, habituellement l'opérateur de réseau.
- Pour dépanner : `show interface serial`

# 2) Fonctionnement de base

- **LCP (Link Control Protocol)** : S'occupe de l'établissement, de la configuration et du test de la liaison de données. Il détecte les boucles, négocie les options et termine la connexion.
- **NCP (Network Control Protocol)** : S'occupe des protocoles de couche réseau. Il négocie les options pour chaque protocole, permet l'encapsulation de plusieurs protocoles et gère la connexion une fois LCP établi.

# 3) Authentification

- **PAP (Password Authentication Protocol)** : Authentification simple en deux étapes. Le mot de passe est envoyé en clair, ce qui le rend vulnérable aux attaques.
- **CHAP (Challenge Handshake Authentication Protocol)** : Authentification en trois étapes qui utilise un challenge. Plus sécurisé que PAP car il utilise un mécanisme de hachage.

# 4) Caractéristiques de PPP

- PPP propose des services optionnels comme :
    - Authentification (PAP, CHAP)
    - Compression (Stacker, Predictor, MPP)
    - Encryption
- Pour établir une connexion PPP :
    1. Négocie les options LCP (MTU, authentification, compression, etc.)
    2. Authentification (si nécessaire)
    3. Établissement de la qualité de la liaison (optionnel)
    4. Négocie les options NCP
    5. Passage à l'état ouvert avec NCP

# 5) Encapsulation avec HDLC

- **HDLC (High-Level Data Link Control)** est souvent utilisé comme base pour PPP.
* Structure de trame PPP :
```
Flag | Address | Control+Protocol ID | Packet | FCS | Flag
```
* ***Protocol ID*** : identifie le protocole de couche réseau dans le champ de données de la trame.
* HDLC (High-Level Data Link Control) est un protocole de communication de données de la couche de liaison du modèle OSI. Il est défini par la norme ISO 3309 et est principalement utilisé dans les réseaux WAN. HDLC est un protocole point à point et orienté bit qui opère à la fois en modes point à point et multipoint.

## Caractéristiques principales d'HDLC :

1. **Encapsulation** : HDLC encapsule les paquets en trames qui sont transmises séquentiellement. Chaque trame possède des bits d'ouverture et de fermeture, une adresse, un champ de commande, un champ de données et un champ de somme de contrôle cyclique (CRC) pour la détection d'erreurs.
    
2. **Fiabilité** : HDLC utilise des accusés de réception pour confirmer la réception des trames et peut demander la retransmission de trames non reçues ou corrompues.
    
3. **Contrôle de flux** : HDLC utilise le contrôle de flux pour s'assurer que l'expéditeur ne surcharge pas le récepteur avec trop de données à la fois.
    

## Types d'opérations HDLC :

1. **Unicast** : Une trame est envoyée d'un dispositif à un autre dispositif.
    
2. **Multicast** : Une trame est envoyée d'un dispositif à un groupe de dispositifs.
    
3. **Broadcast** : Une trame est envoyée d'un dispositif à tous les autres dispositifs du réseau.
    

## Modes de fonctionnement d'HDLC :

1. **Mode Asynchrone équilibré (ABM)** : Il s'agit d'un mode peer-to-peer où les deux stations peuvent envoyer et recevoir des données. Ce mode ne nécessite pas de station principale pour contrôler le lien.
    
2. **Mode Asynchrone (ARM)** : Dans ce mode, une station secondaire peut initialiser la communication, mais la station principale a toujours le contrôle du lien.
    
3. **Mode Adressé (NRM)** : Dans ce mode, la station principale a le contrôle total du lien. Seules les stations principales peuvent initier la communication.
    

## Utilité d'HDLC :

- **Standardisation** : HDLC est largement reconnu et utilisé dans de nombreux environnements de réseau, en particulier dans les liaisons WAN.
    
- **Fiabilité** : Grâce à ses mécanismes intégrés de détection d'erreurs et de contrôle de flux, HDLC offre une transmission de données robuste et fiable.
    
- **Flexibilité** : Avec ses différents modes d'opération, HDLC peut être utilisé dans divers scénarios de communication, du point à point simple aux réseaux multipoints complexes.
    

## Remarque sur les variantes d'HDLC :

Plusieurs variantes d'HDLC ont été développées pour répondre aux besoins spécifiques des fournisseurs et des technologies. Par exemple, Cisco a sa propre version propriétaire d'HDLC, souvent appelée "Cisco HDLC", qui ajoute un champ supplémentaire pour identifier le protocole de couche supérieure (comme IP). Il est donc essentiel de veiller à la compatibilité lors de la mise en œuvre d'HDLC dans un environnement mixte.

En conclusion, HDLC est un protocole de couche de liaison solide et éprouvé qui offre une transmission de données fiable dans une variété de scénarios de réseau. Sa nature flexible et robuste en fait un choix populaire pour les liaisons WAN et d'autres communications point à point.

# Configuration PPP et HDLC

La configuration de PPP et HDLC est essentielle pour établir une communication efficace et sécurisée entre deux équipements sur une liaison série. Voici une explication détaillée de chaque étape de configuration présentée :

## 1) HDLC - Encapsulation par défaut

- **HDLC** est le protocole d'encapsulation par défaut pour les liaisons séries sur les routeurs Cisco. Pour vérifier la méthode d'encapsulation actuelle d'une interface, utilisez la commande `sh ip int [interface]`.
```
sh ip int S0/0/1 >>encapsulation hdlc
```
Cette commande affiche les détails de l'interface, y compris le type d'encapsulation.

## 2) Activation de PPP

- Pour changer l'encapsulation d'une interface en PPP, accédez au mode de configuration de l'interface et utilisez la commande `encapsulation ppp`.
```
R1(config)#int S0/0/0 R1(config-if)#encapsulation ppp
```
## 3) Configuration de l'authentification PPP

- Pour sécuriser la connexion PPP, on peut utiliser l'authentification. Deux méthodes sont principalement utilisées : **PAP** (Password Authentication Protocol) et **CHAP** (Challenge Handshake Authentication Protocol).
    
- Avant d'activer l'authentification, créez un compte de connexion pour chaque voisin PPP :
    
```
R1(config)#username @HOSTNAME_VOISIN password @mot_de_passe
```
- Pour activer l'authentification **CHAP** sur une interface :
```
R1(config-if)#ppp authentication chap
```
- Pour activer l'authentification **PAP** et envoyer les informations d'authentification à un voisin :
```
R1(config-if)#ppp pap sent-username @HOSTNAME password @MON_MP
```
## 4) Configuration complète

Un exemple complet de configuration pour un routeur R1 communiquant avec R2 pourrait ressembler à ceci :
```
R1(config)#username R2 password cisco 
R1(config)#int S0/0/0 
R1(config-if)#encapsulation ppp 
R1(config-if)#ppp authentication chap 
R1(config-if)#ppp pap sent-username R1 password cisco`
```
Cette configuration fait en sorte que R1 utilise PPP pour communiquer avec R2, utilise l'authentification CHAP pour vérifier l'identité de R2 et envoie ses informations d'authentification PAP à R2.