# Guide SNMP

SNMP est un protocole conçu pour gérer et surveiller les dispositifs de réseau tels que les routeurs, les commutateurs et les serveurs. SNMP est largement utilisé dans les réseaux pour collecter des informations et configurer à distance des dispositifs.

# Généralités SNMP
* Mode de transport : UDP
* Ports de communication 
	* 161 : Utilisé par les agents SNMP pour écouter les requêtes provenant des managers SNMP
	* 162 : Utilisé par les managers pour écouter les notifications (souvent appelées traps) envoyées par les agents SNMP.

# Composants clés du SNMP

1. **Agent SNMP** : Equipements réseaux (routeurs, switchs, serveurs, imprimantes, ordi) Il s'agit d'un programme qui s'exécute sur les dispositifs de réseau. Il collecte et stocke des informations concernant le dispositif sur lequel il s'exécute.
    
2. **Gestionnaire SNMP (ou SNMP Manager)** : Il s'agit du système centralisé utilisé pour surveiller ou administrer des dispositifs SNMP. Il envoie des requêtes à l'agent et attend des réponses.
    
3. **MIB (Management Information Base)** : La MIB est un schéma (et non une base de données) de structure hiérarchique, un peu comme une langue, où chaque type d'information de l'agent est défini par un OID. Cet OID est ce qu'utilise le manager lorsqu'il souhaite obtenir une information de l'agent. Ni l'agent ni le manager ne stockent une base de données complète. Au lieu de cela, la MIB sert de schéma commun pour s'assurer que l'information fournie par l'agent correspond à l'OID demandé par le manager
    
4. **Traps** : Les traps sont des notifications ou des alertes envoyées par un agent au gestionnaire en cas d'événement spécifique.
    
# Types de messages SNMP
* Les messages SNMP (ou commandes) définissent la manière dont les gestionnaires SNMP et les agents interagissent entre eux
* Les PDUs SNMP encapsulent les commandes (comme GET, SET, TRAP) ainsi que les informations associées (comme les OIDs et les valeurs). 

Le format de PDU pour SNMP est spécifiquement conçu pour transmettre des informations relatives à la gestion du réseau. Les types de PDU dans SNMP incluent:

1. **GET Request PDU** : Utilisé pour interroger des informations.
2. **GETNEXT Request PDU** : Utilisé pour récupérer la valeur du prochain OID.
3. **SET Request PDU** : Utilisé pour modifier une valeur.
4. **GETBULK Request PDU** : Utilisé pour récupérer des volumes importants d'informations.
5. **RESPONSE PDU** : Une réponse à une demande du gestionnaire.
6. **TRAP PDU** : Utilisé par l'agent pour notifier le gestionnaire d'un événement.

# Exemple d'un GET REQUEST entre manager et agent 

## **Étape 1: Gestionnaire → Agent**
```
Type de PDU: GET Request PDU  
OID demandé: `1.3.6.1.2.1.1.1.0`  
Message: "Fournissez-moi la description du système pour l'OID 1.3.6.1.2.1.1.1.0."`
```
## **Étape 2: Agent → Gestionnaire**
Après avoir reçu la demande, l'agent consulte sa MIB pour trouver la valeur associée à cet OID. Supposons que cet agent gère un routeur Cisco.

```
Type de PDU: RESPONSE PDU  
OID renvoyé: `1.3.6.1.2.1.1.1.0`  
Valeur renvoyée: "Cisco IOS Software, 3700 Software (C3700-ADVENTERPRISEK9-M), Version 12.4(15)T7, RELEASE SOFTWARE (fc3)"  
Message: "La description du système pour l'OID 1.3.6.1.2.1.1.1.0 est 'Cisco IOS Software, 3700 Software (C3700-ADVENTERPRISEK9-M), Version 12.4(15)T7, RELEASE SOFTWARE (fc3)'."
````
# Différents scénarios d'échanges de PDU

| Type de PDU    | Message (Envoyé par le Gestionnaire)                      | Réponse Attendue (de l'Agent)                           |
|----------------|------------------------------------------------------------|---------------------------------------------------------|
| **GET REQUEST**| "Donnez-moi la valeur pour l'OID X."                       | RESPONSE PDU avec la valeur de l'OID X.                 |
| **GET NEXT**   | "Donnez-moi la valeur de l'OID qui vient après l'OID X."   | RESPONSE PDU avec la valeur de l'OID qui suit X.        |
| **SET**        | "Définissez la valeur de l'OID X à Y."                     | RESPONSE PDU indiquant succès ou erreur.                |
| **GET BULK**   | "Donnez-moi les valeurs pour un ensemble d'OID depuis X."  | RESPONSE PDU avec valeurs pour une série d'OID depuis X.|
| **GET RESPONSE**| (Pas envoyé par le Gestionnaire, c'est une réponse.)     | N/A (c'est déjà une réponse).                           |
| **TRAP**       | "Un événement spécifique s'est produit (ex: interface down)." | Aucune réponse attendue pour un TRAP.                   |

# Versions du SNMP

**SNMPv2 (Version 2)**
- **Authentification** : Tentative d'introduire une méthode party-based, mais elle s'est avérée trop complexe et n'a pas été largement adoptée.
- **Confidentialité** : Pas de chiffrement des messages, donc aucune garantie de confidentialité.
- **Intégrité** : Pas de garantie de l'intégrité des messages, car il n'y a pas de mécanisme de vérification des messages.

**SNMPv2c (Version 2 communauté)**
- **Authentification** : Utilise un "community string" pour l'authentification, qui est transmis en clair dans le réseau.
- **Confidentialité** : Pas de chiffrement, donc les données peuvent être lues en transit par quiconque capture les paquets.
- **Intégrité** : Comme le "community string" est transmis en clair, il est vulnérable à l'interception, ce qui peut compromettre l'intégrité des données.

**SNMPv3 (Version 3)**
- **Authentification** : Introduit une authentification des utilisateurs avec un mécanisme de mot de passe, ce qui est plus sûr que le simple "community string". Plusieurs méthodes d'authentification sont supportées, comme HMAC-MD5 et HMAC-SHA.
- **Confidentialité** : Offre la capacité de chiffrer les messages pour garantir la confidentialité des données en transit. DES, 3DES, AES sont parmi les algorithmes de chiffrement pris en charge.
- **Intégrité** : Grâce à l'authentification des utilisateurs et au chiffrement, SNMPv3 garantit que les données n'ont pas été altérées en transit.
- **Contrôle d'accès** : Offre des capacités étendues de contrôle d'accès basées sur l'utilisateur, permettant une gestion fine de ce que chaque utilisateur peut voir ou modifier.

# Configuration SNMPv2
1. On active le service SNMP
```
router(config)# snmp-server enable
```
2. On renseigne le Community string (mot de passe) pour intéragir et le type d'actions (RO ou RW). Dans un environnement de production on ne met jamais des community simple avec RW ! 
```
router(config)# snmp-server community [NOM_COMMUNAUTE] RO
router(config)# snmp-server community [NOM_COMMUNAUTE] RW

# Le manager qui communique avec le community RW pourra appliquer des modificiations
```
3. On peut autorisé l'accès SNMP à certaines IP seulement
```
router(config)# snmp-server host [IP] community [NOM_COMMUNAUTE]
```
4. On peut configurer l'envoi automatique de notification (TRAPS) au gestionnaire 
```
router(config)# snmp-server host [IP] traps version {2c,3} [NOM_COMMUNAUTE]
router(config)# snmp-server enable traps
```
5. On sauvegarde la configuration
```
router(config)# end
router# write memory
```

# Configuration SNMPv3 
* SNMPv3 rajoute une couche de sécurité en ajoutant des mécanismes d'authentifications et de chiffrement
* On utilise plus de Community strings mais des comptes de connexions
1. Créer un utilisateur SNMPv3 sur l'agent
```
snmp-server user [USER] [GROUP] v3 {md5,sha} {des,aes}
```
2. Créer un groupe SNMPv3
```
snmp-server group [GROUP] v3 [priv|auth|noauth] [read vue_lecture] [write vue_ecriture]

[priv|auth|noauth] : Détermine le niveau de sécurité pour le groupe :
	- noauth : Pas d'authentification ni de chiffrement
	- auth : Authentification mais pas de chiffrement
	- priv : Authentification et chiffrement

[read vue_lecture] : Définit la "vue" SNMP que le groupe est autorisé à lire. Une "vue" est essentiellement un sous-ensemble de la MIB
    
[write vue_ecriture] : Définit la vue SNMP que le groupe est autorisé à modifier
```
3. Définir les parties accessibles de la MIB (vue)
```
snmp-server view [NOM] [OID_MIB] [included|excluded]
```
