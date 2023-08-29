# Guide sur RADIUS

## 1. C'est quoi le protocole RADIUS?

**RADIUS** (Remote Authentication Dial-In User Service) est un protocole client-serveur qui fournit une gestion centralisée de l'authentification, de l'autorisation et de la comptabilité (également connu sous le nom de processus AAA) pour les utilisateurs qui se connectent et utilisent un réseau ou un service. Il a été initialement développé pour les connexions dial-up, mais il est maintenant largement utilisé dans de nombreux autres contextes réseau.

## 2. C'est quoi le but et l'intérêt du protocole?

Le but principal de RADIUS est de centraliser l'authentification des utilisateurs, de leur fournir des autorisations spécifiques en fonction de leurs droits et de comptabiliser leur utilisation du réseau. En d'autres termes, il s'assure que les utilisateurs sont bien ceux qu'ils prétendent être (authentification), qu'ils ont les bonnes permissions (autorisation) et que leurs activités sont enregistrées (comptabilité).

L'intérêt du protocole RADIUS réside dans:

- **Centralisation**: Les informations d'authentification, d'autorisation et de comptabilité sont toutes centralisées, ce qui facilite la gestion et l'administration des droits et des accès des utilisateurs.
- **Sécurité**: Il offre une méthode sécurisée pour authentifier les utilisateurs et autoriser l'accès aux ressources réseau.
- **Extensibilité**: RADIUS est conçu pour supporter et s'intégrer avec une variété d'appareils et de systèmes, de l'équipement d'accès à distance aux points d'accès sans fil.
- **Inter-opérabilité**: Il est compatible avec une grande variété de dispositifs et d'équipements, le rendant idéal pour les environnements hétérogènes.

## 3. Quels sont les cas courants d'utilisation du protocole?

RADIUS est couramment utilisé dans les scénarios suivants:

1. **Réseaux sans fil**: Dans les environnements Wi-Fi d'entreprise, RADIUS est souvent utilisé pour authentifier les utilisateurs avant de leur accorder l'accès au réseau sans fil. Cela s'applique tant pour les employés que pour les invités.
2. **VPN (Virtual Private Networks)**: Les entreprises qui offrent un accès VPN à leurs employés utilisent souvent RADIUS pour authentifier ces utilisateurs lorsqu'ils se connectent au réseau de l'entreprise à distance.
3. **Réseaux commutés**: Dans les premiers jours d'Internet, RADIUS était fréquemment utilisé pour authentifier les utilisateurs de services dial-up. Bien que moins courant aujourd'hui, certains réseaux commutés existent encore et peuvent utiliser RADIUS.
4. **Réseaux filaires d'entreprise**: Pour une sécurité accrue, certaines entreprises utilisent RADIUS pour authentifier les utilisateurs avant de leur permettre d'accéder au réseau local (LAN).
5. **Hotspots publics**: Dans les lieux tels que les aéroports, les hôtels et les cafés, où un accès Internet est offert au public, RADIUS peut être utilisé pour gérer l'authentification des utilisateurs et la comptabilité de leur utilisation.
6. **Contrôle d'accès réseau (NAC)**: RADIUS est souvent intégré dans les solutions NAC pour s'assurer que seuls les dispositifs conformes et authentifiés peuvent accéder au réseau.

## 4. Quels sont les éléments du protocole RADIUS?

RADIUS fonctionne dans un contexte client-serveur et possède plusieurs composants clés:

1. **Client RADIUS**: C'est un dispositif qui demande l'authentification d'un utilisateur. Cela peut être un commutateur, un routeur, un point d'accès, un serveur VPN ou tout autre dispositif nécessitant une authentification utilisateur avant d'accorder l'accès à un réseau ou un service.

2. **Serveur RADIUS**: C'est le serveur qui traite les demandes du client RADIUS. Il contient ou a accès à une base de données d'informations d'authentification utilisateur. Le serveur RADIUS vérifie les informations d'authentification fournies par le client RADIUS (au nom de l'utilisateur) contre sa base de données, autorise l'accès et informe le client du résultat.

3. **Agent de relais RADIUS**: Dans certains scénarios plus complexes, un agent relais peut être utilisé pour transférer les demandes RADIUS entre le client et le serveur.

4. **Base de données d'authentification**: C'est là que les informations d'authentification, comme les noms d'utilisateur et les mots de passe, sont stockées. Elle peut être intégrée directement au serveur RADIUS ou être une base de données externe à laquelle le serveur RADIUS accède.

5. **Attributs**: RADIUS fonctionne avec une série d'attributs-paires-valeurs (APV) qui définissent les détails de la demande, comme le nom d'utilisateur, l'adresse IP, le service demandé, etc.

## 5. Quels sont les versions et les caractéristiques?

**RADIUS** a évolué au fil des ans, mais contrairement à certains protocoles, il n'a pas de "versions" multiples à proprement parler. Cependant, il y a eu plusieurs mises à jour de ses spécifications pour répondre à de nouveaux besoins.

**Caractéristiques de RADIUS**:

1. **Authentification**: RADIUS prend en charge plusieurs méthodes d'authentification, dont PAP, CHAP, MS-CHAP, EAP, etc.

2. **Autorisation**: Une fois qu'un utilisateur est authentifié, le serveur RADIUS envoie un ensemble d'attributs au client RADIUS, indiquant les services auxquels l'utilisateur peut accéder.

3. **Comptabilité**: Le serveur RADIUS enregistre les informations sur les sessions utilisateur, telles que la durée de la session, les données transmises/reçues, la cause de la déconnexion, etc.

4. **Flexibilité**: RADIUS est flexible et peut être intégré avec une variété de bases de données, y compris SQL, LDAP, etc.

5. **Extensibilité**: De nombreux fournisseurs d'équipements réseau ont ajouté leurs propres attributs spécifiques au vendeur pour étendre les fonctionnalités de RADIUS.

6. **Sécurité**: RADIUS utilise le protocole UDP pour le transport. Bien que les mots de passe soient obscurcis lors de la transmission entre le client et le serveur, le protocole lui-même n'est pas considéré comme étant hautement sécurisé. C'est pourquoi il est souvent utilisé en combinaison avec d'autres mécanismes de sécurité ou dans des environnements de réseau sécurisés.

Il est essentiel de noter que, malgré ses nombreuses utilisations, RADIUS présente certaines limitations en termes de sécurité et d'évolutivité. Par conséquent, dans certains environnements, il est complété ou remplacé par des protocoles tels que TACACS+ ou Diameter.

## 8. Comment une communication qui utilise RADIUS s'établit?

Le processus d'authentification RADIUS peut être décrit en une séquence d'étapes pour illustrer la manière dont une demande d'accès est traitée. Voici un aperçu des étapes et des échanges qui se produisent :

1. **Demande d'accès de l'utilisateur** : 
	- Lorsqu'un utilisateur tente d'accéder à un réseau ou à une ressource, il fournit ses informations d'identification (comme un nom d'utilisateur et un mot de passe) à un dispositif, appelé le client RADIUS (par exemple, un point d'accès WiFi).
    
2. **Transmission au serveur RADIUS** :
	- Le client RADIUS envoie ensuite une demande d'authentification, généralement sous forme de paquet "Access-Request", au serveur RADIUS. Ce paquet contient les informations d'identification de l'utilisateur ainsi que d'autres attributs liés à la demande.

3. **Traitement de la demande par le serveur RADIUS** :
	- Le serveur RADIUS reçoit le paquet "Access-Request" et recherche dans sa base de données ou dans une source d'authentification externe pour vérifier les informations d'identification fournies.
    
4. **Réponse du serveur RADIUS** :
	- Si les informations d'identification sont correctes et que l'utilisateur est autorisé à accéder à la ressource :
		- Le serveur RADIUS envoie un paquet "Access-Accept" au client RADIUS avec les attributs appropriés pour la session de l'utilisateur.
	- Si les informations d'identification sont incorrectes ou si l'utilisateur n'est pas autorisé :
		- Le serveur RADIUS envoie un paquet "Access-Reject".
	- Si des informations supplémentaires sont nécessaires pour compléter l'authentification (comme dans le cas d'une authentification à deux facteurs) :
		- Le serveur RADIUS envoie un paquet "Access-Challenge", demandant des informations supplémentaires.

5. **Établissement de la connexion** :
	- Une fois le paquet "Access-Accept" reçu, le client RADIUS fournit à l'utilisateur l'accès à la ressource ou au réseau en fonction des attributs renvoyés par le serveur RADIUS.

6. **Comptabilité** :
	- En plus de l'authentification et de l'autorisation, le serveur RADIUS peut également enregistrer des détails sur la session de l'utilisateur. Lorsque la session de l'utilisateur commence, le client RADIUS envoie un paquet "Accounting-Start" (ou "Accounting-Request Start") au serveur RADIUS.
	- Lorsque la session de l'utilisateur se termine, le client RADIUS envoie un paquet "Accounting-Stop" avec des détails sur la durée de la session, la quantité de données transférées, etc.

1. **Fin de la session** :
	- Lorsque l'utilisateur termine sa session ou est déconnecté pour une raison quelconque, le client RADIUS envoie une notification appropriée au serveur RADIUS.

L'utilisation de RADIUS implique un échange continu de ces paquets pour gérer l'authentification, l'autorisation et la comptabilité des utilisateurs sur le réseau.

## 9. Quels sont les failles de sécurité du protocole RADIUS?

RADIUS, bien que largement adopté, a montré des faiblesses et des vulnérabilités au fil des années :

1. **Transmission en clair**: Dans ses premières versions, RADIUS transmettait des attributs en clair, notamment le mot de passe utilisateur, ce qui pourrait être intercepté par des attaquants sur le réseau.

2. **Attaques par rejeu**: Sans mise en œuvre appropriée, RADIUS peut être vulnérable aux attaques par rejeu, où un attaquant capture un paquet RADIUS valide et le rejoue pour obtenir un accès non autorisé.

3. **Manque d'intégrité des paquets**: Les paquets RADIUS originaux ne garantissent pas l'intégrité des données, permettant ainsi à un attaquant de modifier potentiellement les paquets en transit.

4. **Attaques DoS**: Comme beaucoup d'autres protocoles, RADIUS peut être vulnérable aux attaques de déni de service, où un attaquant envoie une grande quantité de demandes d'authentification pour surcharger le serveur RADIUS.

5. **Vulnérabilités de mise en œuvre**: Comme pour tout protocole, la manière dont RADIUS est mis en œuvre et configuré peut introduire des failles de sécurité. Les versions obsolètes, les configurations par défaut et les mauvaises pratiques peuvent toutes rendre les systèmes RADIUS vulnérables.

## 10. Comment sécuriser le protocole RADIUS?

Pour atténuer les risques associés à l'utilisation de RADIUS, voici quelques bonnes pratiques et recommandations :

1. **Utiliser le protocole RADIUS sur IPsec ou TLS**: La mise en œuvre de RADIUS sur IPsec ou TLS (souvent appelé RADSEC) garantit que les communications sont cryptées, protégeant contre l'interception et la modification des paquets.

2. **Filtres d'adresses IP**: Limitez les clients RADIUS qui peuvent se connecter au serveur RADIUS en utilisant des listes de contrôle d'accès basées sur les adresses IP.

3. **Utiliser des mots de passe forts**: Assurez vous que tous les périphériques et utilisateurs qui interagissent avec le serveur RADIUS utilisent des mots de passe forts.

4. **Surveiller et auditer**: Activez la journalisation détaillée et surveillez régulièrement les journaux du serveur RADIUS pour détecter toute activité suspecte.

5. **Mettre à jour régulièrement**: Assurez vous que le logiciel du serveur RADIUS est régulièrement mis à jour pour bénéficier des dernières corrections de sécurité.

6. **Éviter les configurations par défaut**: Modifiez les paramètres par défaut, en particulier les mots de passe et les clés partagées par défaut.

7. **Utiliser une authentification à plusieurs facteurs**: Si possible, intégrez une authentification à plusieurs facteurs pour augmenter la sécurité des authentifications RADIUS.

8. **Redondance et haute disponibilité**: Pour éviter les attaques de déni de service et garantir une disponibilité continue, mettez en place des serveurs RADIUS redondants.

9. **Isoler le serveur RADIUS**: Placez le serveur RADIUS dans un réseau isolé ou derrière un pare-feu pour limiter l'exposition aux attaques potentielles.

10. **Réduire la portée**: Si possible, utilisez RADIUS uniquement lorsque cela est nécessaire et explorez des alternatives plus sécurisées pour certaines utilisations.

## Configuration RADIUS Cisco 

### **Côté Serveur :**

#### **1. Configuration de base :**
Avant de commencer, assurez-vous que votre équipement est correctement configuré avec les informations de base comme l'adresse IP, le masque de sous-réseau, etc.

#### **2. Installation du serveur RADIUS :**
Si vous utilisez un équipement Cisco pour héberger le serveur RADIUS, comme le Cisco Identity Services Engine (ISE), suivez les étapes d'installation appropriées pour ce produit.

#### **3. Configuration du serveur RADIUS :**
```bash
! Activer le mode configuration
Router(config)# radius-server host [IP_DU_SERVEUR] auth-port 1812 acct-port 1813

! Définir la clé secrète pour le serveur RADIUS (à garder privée)
Router(config)# radius-server key [CLE_SECRETE]
```

#### **4. Configurer l'authentification via RADIUS en activant l'authentification RADIUS pour les connexions entrantes :**
```bash

Router(config)# aaa new-model
Router(config)# aaa authentication login default group radius local
```

### **Côté Client :**

#### **1. Configuration de base :**
Comme pour le serveur, assurez-vous que l'équipement client est correctement configuré avec les informations de base.

#### **2. Configuration du client pour utiliser RADIUS :**
```bash
! Activer le mode configuration
Router(config)# aaa new-model

! Configurer le serveur RADIUS
Router(config)# radius-server host [IP_DU_SERVEUR] auth-port 1812 acct-port 1813

! Définir la clé secrète (doit correspondre à celle du serveur)
Router(config)# radius-server key [CLE_SECRETE]

! Utiliser RADIUS pour l'authentification
Router(config)# aaa authentication login default group radius local
```
