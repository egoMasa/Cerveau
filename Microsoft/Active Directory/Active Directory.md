# Sommaire 
1. Windows Server 
2. Service d'annuaire ADDS
	1. Protocole LDAP
	2. Controleur de domaine (DC) et RODC  (Read-Only Domain Controller)
	3. Domaine, Foret et Arbre
	4. Unité d'organisation (OU): Objets et attributs (utilisateurs, groupes, ressources)
	5. Identifiant : GUID, SID, DN, RDN, FQDN
	6. Roles FSMO : Schema Master, Domain Naming Master, RID, PDC Emulator, Infrastructure Master
	7. Lien de confiance : Parent-child, Cross-link, External, Tree-root, Forest, transitive or non-transitive
	8. Stratégie et politique de groupe (GPO)
	9. Repertoire SYSVOL
3. Service DHCP
4. Service DNS
5. Service de fédération d'identité ADFS
6. Authentification des services (LM,NTLM,Kerberos)

# 1) Windows Server 

**Windows Server** est une famille de systèmes d'exploitation serveur conçu pour gérer les réseaux, les applications et les services web dans un environnement d'entreprise. Les principales versions incluent Windows Server 2016, 2019, et plus récemment, Windows Server 2022.

### Caractéristiques et Capacités de Windows Server

1. **Rôles de serveur spécialisés** : Windows Server peut être configuré pour une variété de rôles de serveur, y compris mais non limité à :
   - Serveur de fichiers
   - Serveur d'impression
   - Serveur web (IIS)
   - Serveur de messagerie
   - Serveur de base de données
   - Serveur d'authentification

# 2) Service d'annuaire ADDS (Active Directory)

## Présentation d'ADDS (Active Directory Domain Services)

**Active Directory Domain Services (ADDS)** est un service de Microsoft Windows Server qui permet de déployer et de gérer un service d'annuaire dans un environnement réseau. Lorsqu'on parle d'Active Directory (AD), on fait généralement référence à un serveur Windows sur lequel la fonctionnalité ADDS est activée.

## Fonctionnalités Clés d'ADDS

1. **Gestion Centralisée des Utilisateurs et des Ressources** : ADDS fournit un framework pour centraliser la gestion des utilisateurs, des groupes, des ordinateurs et d'autres objets au sein d'un réseau d'entreprise.

2. **Authentification et Autorisation** : Il permet une authentification unique (SSO) et gère les droits d'accès des utilisateurs et des groupes à diverses ressources dans le réseau.

3. **Réplication et Redondance** : ADDS assure la réplication des données entre plusieurs contrôleurs de domaine pour garantir la redondance et la fiabilité des données.

4. **Hiérarchie et Structure Organisée** : Il organise les ressources en unités d'organisation (OU), domaines, forêts et arbres, facilitant ainsi la gestion et la délégation des contrôles d'accès.

5. **Gestion des Politiques de Groupe (GPO)** : Permet de définir et d'appliquer des politiques de sécurité et de configuration à l'échelle de l'ensemble du réseau.

6. **Services de Noms de Domaine (DNS)** : Intègre étroitement les services DNS pour la résolution de noms et la localisation des services et des ressources.

7. **Interopérabilité** : Offre des fonctionnalités pour interagir avec d'autres services d'annuaire, comme LDAP (Lightweight Directory Access Protocol), et supporte des scénarios de fédération avec d'autres forêts.

8. **Sécurité Renforcée** : Intègre des fonctionnalités de sécurité avancées comme le Kerberos et le chiffrement pour protéger les données et les communications au sein du réseau.

#### Importance d'ADDS

ADDS est essentiel pour les entreprises car il permet une gestion efficace et sécurisée des identités et des accès, ce qui est crucial dans les environnements d'entreprise modernes. La capacité d'ADDS à fournir une authentification centralisée et une gestion des politiques à travers un large éventail de ressources informatiques simplifie considérablement l'administration du système et améliore la sécurité globale du réseau.

En résumé, ADDS est le pilier de l'Active Directory, offrant des outils puissants pour la gestion des identités, des accès et des politiques dans un environnement d'entreprise. Lorsque ADDS est déployé sur un serveur Windows, ce dernier devient un contrôleur de domaine, jouant un rôle central dans la gestion du réseau et des services d'annuaire.

# 3) Lightweight Directory Access Protocol (LDAP)

## Principe du protocole LDAP 
LDAP (Lightweight Directory Access Protocol) est un protocole de communication utilisé pour interagir avec un service d'annuaire. Ses principales fonctions incluent la récupération, la modification et la suppression d'informations dans l'annuaire. Voici un résumé de ses utilisations principales :

1. **Récupération d'Informations** :
   - LDAP est souvent utilisé pour extraire des informations stockées dans un annuaire, telles que les détails des utilisateurs, des groupes, ou d'autres objets.
   - Les applications peuvent effectuer des recherches dans l'annuaire pour obtenir des informations spécifiques, comme les adresses e-mail, les noms d'utilisateur, ou les appartenance à des groupes.

2. **Vérification des Droits d'Accès** :
   - LDAP permet de vérifier si un utilisateur est présent dans l'annuaire et s'il possède les droits nécessaires pour accéder à une ressource ou un service particulier.
   - Cette fonctionnalité est cruciale pour l'authentification et l'autorisation dans les systèmes de gestion des accès.

3. **Modification et Gestion des Données** :
   - En plus de la récupération, LDAP permet également de modifier les informations de l'annuaire, comme la mise à jour des attributs d'un utilisateur ou le changement de son mot de passe.
   - Il peut également être utilisé pour ajouter de nouveaux utilisateurs ou supprimer des utilisateurs existants.

## Fonctionnement d'une Authentification LDAP

1. **Requête Initiale de l'Utilisateur**
   - L'utilisateur envoie ses identifiants (généralement un nom d'utilisateur et un mot de passe) à une application ou un service qui agit comme un client LDAP.

2. **Bind Request du Client LDAP au Contrôleur de Domaine**
   - Le client LDAP (l'application ou le service) crée une requête de liaison (bind request) et l'envoie au contrôleur de domaine AD. Cette requête contient les identifiants de l'utilisateur.

3. **Traitement de la Bind Request par le Contrôleur de Domaine**
   - Le contrôleur de domaine reçoit la bind request et vérifie les identifiants fournis contre ceux stockés dans l'AD.

4. **Bind Response du Contrôleur de Domaine**
   - Si les identifiants sont corrects, le contrôleur de domaine envoie une réponse de liaison (bind response) positive, indiquant une authentification réussie.
   - Si les identifiants sont incorrects, une réponse négative est renvoyée.

5. **Requêtes Supplémentaires (Facultatives)**
   - Si l'authentification est réussie et que des informations supplémentaires sont nécessaires, le client LDAP peut effectuer d'autres requêtes (comme une recherche dans l'annuaire) en utilisant la session authentifiée.

6. **Réponses Aux Requêtes Supplémentaires**
   - Le contrôleur de domaine répond aux requêtes supplémentaires, fournissant les informations demandées si l'utilisateur authentifié a les droits nécessaires.

## Tableau des requêtes LDAP

| Type de Requête LDAP | Description                        | Réponse Attendue                                           |
|----------------------|------------------------------------|-----------------------------------------------------------|
| Bind Request         | Demande d'authentification         | Bind Response: Succès ou échec de l'authentification       |
| Search Request       | Requête de recherche dans l'AD     | Search Response: Résultats de recherche ou aucun résultat  |
| Add Request          | Ajout d'un nouvel objet dans l'AD  | Add Response: Succès ou échec de l'ajout                   |
| Modify Request       | Modification d'un objet dans l'AD  | Modify Response: Succès ou échec de la modification        |
| Delete Request       | Suppression d'un objet de l'AD     | Delete Response: Succès ou échec de la suppression         |
| Modify DN Request    | Modification du DN d'un objet      | Modify DN Response: Succès ou échec de la modification DN  |
| Compare Request      | Comparaison d'un attribut d'objet  | Compare Response: Succès ou échec de la comparaison        |
| Extended Request     | Requête LDAP étendue               | Extended Response: Résultats spécifiques à la requête      |
| Unbind Request       | Fermeture de la session LDAP       | Aucune réponse attendue (fermeture de connexion)           |

## Explications :

- **Bind Request/Response** : Utilisé pour l'authentification. La réponse indique si les identifiants fournis sont valides.
- **Search Request/Response** : Employé pour interroger l'AD. La réponse inclut les objets ou les informations demandés.
- **Add/Modify/Delete Request/Response** : Utilisés pour ajouter, modifier ou supprimer des objets dans l'AD. La réponse indique si l'opération a réussi.
- **Modify DN Request/Response** : Utilisé pour changer le DN (Distinguished Name) d'un objet. Utile pour déplacer des objets ou renommer des entrées.
- **Compare Request/Response** : Compare une valeur donnée à celle d'un attribut spécifique d'un objet. Répond si la comparaison est vraie ou fausse.
- **Extended Request/Response** : Permet d'exécuter des opérations LDAP spéciales non couvertes par les autres types de requêtes.
- **Unbind Request** : Ferme la session LDAP. Aucune réponse n'est attendue puisque la connexion est simplement fermée.



# 4) Controleur de domaine (DC)

Un **Contrôleur de Domaine (DC)** est un serveur dans un réseau Windows qui est responsable de l'authentification des utilisateurs et des ordinateurs dans un domaine Active Directory (AD). Il stocke une copie de l'annuaire AD, qui contient toutes les informations sur les comptes d'utilisateurs, les politiques de sécurité, et d'autres données importantes pour la gestion du réseau.

### Rôles et Fonctionnalités d'un DC

1. **Gestion des Identifiants et des Accès** :
   - Le DC authentifie les utilisateurs et les ordinateurs dans le domaine, s'assurant qu'ils ont les droits appropriés pour accéder aux ressources du réseau.

2. **Répondre aux Requêtes LDAP** :
   - Il traite les requêtes LDAP provenant des clients et d'autres serveurs, telles que les demandes d'information sur les utilisateurs ou les groupes.

3. **Réplication et Synchronisation** :
   - Dans un environnement avec plusieurs DCs, ils se synchronisent entre eux pour s'assurer que les données de l'annuaire sont cohérentes et à jour sur tous les contrôleurs de domaine.

4. **Sécurité et Politiques de Groupe** :
   - Le DC applique les politiques de groupe (GPO) définies pour le domaine, contrôlant ainsi les paramètres de sécurité et de configuration des ordinateurs et des utilisateurs du domaine.

5. **Placement dans la Forêt ou l'Arbre Active Directory** :
   - Un DC est typiquement associé à un domaine spécifique, mais fait partie d'une forêt plus large, qui est une collection de domaines dans une structure hiérarchique.

### Types de Contrôleurs de Domaine

- **Contrôleur de Domaine Principal (PDC)** : Dans les versions plus anciennes de Windows Server, le PDC était le serveur principal pour un domaine. Dans les versions actuelles, tous les DCs sont essentiellement égaux, mais un DC est toujours désigné comme PDC Emulator pour des raisons de compatibilité.

- **Contrôleur de Domaine en Lecture Seule (RODC)** : Un RODC est une version spéciale du DC qui contient une copie en lecture seule de l'annuaire. Il est utilisé dans les emplacements où la sécurité physique du serveur ne peut être garantie.


# 5) Structure foret, arbre et domaine 

### Forêt Active Directory

Une **forêt** est la plus grande unité structurelle dans Active Directory. Elle est constituée de :

- **Plusieurs domaines** : Chaque forêt peut contenir un ou plusieurs domaines.
- **Un schéma commun** : Tous les domaines au sein d'une forêt partagent un schéma d'annuaire commun, qui définit les types d'objets et les attributs qui peuvent être stockés dans Active Directory.
- **Une base de données de noms de domaine globale** : Cela permet de s'assurer que chaque domaine au sein de la forêt a un nom unique.
- **Relations de confiance automatiques** : Chaque domaine dans une forêt a une relation de confiance automatique avec les autres domaines de la forêt.

### Arbres Active Directory

Un **arbre** est un groupe de domaines dans une forêt. Les caractéristiques d'un arbre incluent :

- **Structure hiérarchique** : Un arbre est une collection de domaines organisée de manière hiérarchique. Le premier domaine créé dans un arbre devient le domaine racine de cet arbre.
- **Espace de noms contigu** : Tous les domaines dans un arbre partagent un espace de noms commun. Par exemple, si le domaine racine est "entreprise.com", les sous-domaines pourraient être "hr.entreprise.com", "ventes.entreprise.com", etc.

### Domaines Active Directory

Un **domaine** est un sous-ensemble d'une forêt et peut être considéré comme la base de construction d'Active Directory. Chaque domaine :

- **Stocke des informations sur les objets** : Les domaines contiennent des informations sur les utilisateurs, les groupes, les ordinateurs, et d'autres objets.
- **Peut avoir sa propre politique de sécurité** : Chaque domaine peut avoir des stratégies de groupe et des contrôles d'accès distincts.
- **Est géré par un ou plusieurs contrôleurs de domaine** : Les contrôleurs de domaine au sein d'un domaine gèrent l'authentification et la synchronisation des informations pour ce domaine.

### Relation entre Forêts, Arbres et Domaines

- **Forêt** : L'ensemble comprenant plusieurs arbres, partageant un schéma et une base de données de noms de domaine globale.
- **Arbre** : Un groupe de domaines connectés dans une structure hiérarchique avec un espace de noms contigu.
- **Domaine** : L'unité de base dans un arbre, gérant les informations spécifiques et la politique de sécurité pour ce segment de la forêt.

En résumé, une forêt Active Directory est une collection d'arbres, où chaque arbre est une hiérarchie de domaines partageant un espace de noms commun. Chaque domaine est une entité administrative qui stocke des informations sur les objets et applique des politiques de sécurité. Cette structure permet une gestion organisée et efficace des ressources et des politiques de sécurité dans un environnement d'entreprise étendu.

# 6) Identifiants AD 
### 1. GUID (Globally Unique Identifier)
- **Nature** : Un GUID est un identifiant unique de 128 bits généré par le système pour garantir l'unicité à travers le réseau.
- **Usage** : Utilisé pour identifier de manière unique des objets au sein d'Active Directory, tels que les utilisateurs, les groupes, et les contrôleurs de domaine.
- **Caractéristique** : Le GUID reste constant même si l'objet est déplacé ou renommé dans Active Directory.
### 2. SID (Security Identifier)
- **Nature** : Un SID est un identifiant unique utilisé pour gérer les contrôles d'accès et les permissions.
- **Usage** : Attribué à chaque compte utilisateur, groupe, et autres entités de sécurité dans Active Directory.
- **Caractéristique** : Chaque fois qu'un compte utilisateur ou groupe est créé, un nouveau SID est généré et reste associé à cet objet, même si son nom change.
### 3. DN (Distinguished Name)
- **Nature** : Le DN est une chaîne de caractères qui identifie de manière unique chaque objet dans l'annuaire LDAP.
- **Usage** : Représente le chemin complet de l'objet dans Active Directory, incluant son nom, les unités d'organisation (OU) et les domaines auxquels il appartient.
- **Caractéristique** : Le DN change si l'objet est déplacé dans une autre OU ou renommé.
### 4. RDN (Relative Distinguished Name)
- **Nature** : Le RDN est une partie du DN qui identifie de manière unique l'objet au sein de son conteneur immédiat.
- **Usage** : Utilisé pour identifier un objet dans son contexte local, par exemple, le nom d'un utilisateur au sein d'une unité d'organisation spécifique.
- **Caractéristique** : Le RDN est généralement le nom de l'objet lui-même, sans inclure le chemin complet de l'annuaire.
### 5. FQDN (Fully Qualified Domain Name)
- **Nature** : Un FQDN est l'adresse complète d'un hôte ou d'un serveur dans le réseau.
- **Usage** : Utilisé pour identifier les emplacements dans les réseaux, y compris Internet, avec un nom de domaine complet.
- **Caractéristique** : Inclut le nom d'hôte (par exemple, "serveur") et le domaine (par exemple, "entreprise.com"), formant ainsi "serveur.entreprise.com".
### Résumé des Différences

| Identifiant | Description                                                  | Usage                                                                                      | Caractéristique                                                                                      |
|-------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| GUID        | Globally Unique Identifier, 128 bits                         | Identifie de manière unique des objets dans Active Directory                               | Reste constant, même si l'objet est déplacé ou renommé                                               |
| SID         | Security Identifier                                          | Attribué à chaque compte utilisateur, groupe et entités de sécurité                        | Généré lors de la création de l'objet et reste associé même si le nom de l'objet change              |
| DN          | Distinguished Name                                           | Représente le chemin complet de l'objet dans l'annuaire LDAP/AD                            | Change si l'objet est déplacé dans une autre OU ou renommé                                           |
| RDN         | Relative Distinguished Name                                  | Identifie un objet dans son contexte local (au sein de son conteneur immédiat)              | Généralement le nom de l'objet lui-même, sans le chemin complet                                      |
| FQDN        | Fully Qualified Domain Name                                  | Identifie les emplacements dans les réseaux, y compris Internet, avec un nom de domaine complet | Comprend le nom d'hôte et le domaine (ex. "serveur.entreprise.com")                               |


# 7) Roles FSMO 

## Définition FSMO
* Les rôles FSMO (Flexible Single Master Operations) sont des rôles spéciaux attribués à certains contrôleurs de domaine (DC) au sein d'une forêt Active Directory. Chacun de ces rôles a des responsabilités uniques qui sont cruciales pour le bon fonctionnement de l'ensemble de l'environnement Active Directory.

* Dans un réseau Active Directory, bien que la plupart des tâches puissent être effectuées par n'importe quel DC (ce qu'on appelle le modèle multi-maître), il existe certaines opérations qui ne peuvent être gérées de manière fiable que par un seul DC à la fois pour éviter des conflits ou des incohérences. Ces opérations spéciales sont gérées par les rôles FSMO.

* Chaque rôle FSMO a une portée et des responsabilités spécifiques, et ils sont répartis entre les DCs de la manière suivante :

1. **Schema Master et Domain Naming Master** : Ces rôles ont une portée de forêt, ce qui signifie qu'il n'y a qu'un seul Schema Master et un seul Domain Naming Master dans toute la forêt Active Directory.
    
2. **RID Master, PDC Emulator, et Infrastructure Master** : Ces rôles ont une portée de domaine, ce qui signifie qu'il y a un de chacun de ces rôles dans chaque domaine de la forêt.

## Tableau récapitulatif des rôles
| Rôle FSMO            | Portée        | Fonction                                                                                   | Importance                                                                                             |
|----------------------|---------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Schema Master        | Forêt         | Gère les mises à jour du schéma d'Active Directory.                                         | Assure l'unicité et la cohérence du schéma dans toute la forêt.                                        |
| Domain Naming Master | Forêt         | Gère l'ajout et la suppression de domaines dans la forêt.                                  | Empêche les conflits de noms de domaine au sein de la forêt.                                           |
| RID Master           | Domaine       | Génère les identifiants relatifs pour les nouveaux objets AD au sein du domaine.            | Assure l'unicité des SID pour les nouveaux objets dans le domaine.                                     |
| PDC Emulator         | Domaine       | Sert de référence principale pour l'heure et les changements de mot de passe dans le domaine. | Important pour la compatibilité et la synchronisation de l'heure au sein du domaine.                    |
| Infrastructure Master| Domaine       | Met à jour les références croisées entre les objets de différents domaines.                 | Garantit que les références à des objets dans d'autres domaines sont à jour.                           |

## Attribution des rôles 

1. **Premier Contrôleur de Domaine** :
	- Lorsque vous créez le premier contrôleur de domaine dans une nouvelle forêt Active Directory, ce DC reçoit tous les cinq rôles FSMO par défaut.
	- Ces rôles incluent les deux rôles de forêt (Schema Master et Domain Naming Master) et les trois rôles de domaine (RID Master, PDC Emulator, Infrastructure Master).
1. **Ajout de Domaines Supplémentaires** :
	- Lorsque de nouveaux domaines sont ajoutés à la forêt, le premier DC de chaque nouveau domaine reçoit automatiquement les trois rôles de domaine (RID Master, PDC Emulator, Infrastructure Master) pour ce domaine spécifique.
	- Les rôles de forêt (Schema Master et Domain Naming Master) restent avec le premier DC de la forêt entière.
2. **Gestion et Transfert des Rôles** :
	- Les administrateurs peuvent transférer manuellement les rôles FSMO entre les DCs en fonction des besoins organisationnels, de la planification de la redondance, ou de la performance.
	- Il est possible de centraliser tous les rôles sur un seul DC ou de les répartir entre plusieurs DCs pour une meilleure répartition des charges et une redondance.
3. **En Cas de Pannes** :
	- Si un DC tenant un rôle FSMO tombe en panne, l'administrateur peut transférer le rôle à un autre DC. Si le DC original ne peut être restauré, un processus appelé "Seizing" (prise de force) peut être utilisé pour assigner le rôle à un autre DC.

En résumé, les rôles FSMO ne sont pas attribués automatiquement à chaque contrôleur de domaine par le serveur central AD, mais sont plutôt assignés lors de la configuration initiale de la forêt et des domaines, puis gérés manuellement par les administrateurs. Cette gestion comprend le transfert des rôles entre les DCs pour maintenir l'équilibre et la redondance au sein de l'environnement Active Directory.

# 8) Lien de confiance 
Les liens de confiance dans Active Directory (AD) sont des relations établies entre deux domaines ou forêts qui permettent aux utilisateurs d'un domaine de s'authentifier et d'accéder aux ressources d'un autre domaine. Ces liens de confiance peuvent être classés en différents types, chacun ayant des caractéristiques et des utilisations spécifiques.
## 1. Parent-Child Trust
- **Description** : C'est le type de lien de confiance le plus courant dans Active Directory. Il se forme automatiquement entre un domaine parent et un nouveau domaine enfant lors de la création de ce dernier.
- **Caractéristique** : Transitive, c'est-à-dire que la confiance s'étend au-delà des deux domaines à d'autres domaines dans la même hiérarchie.
- **Usage** : Utilisé dans une structure hiérarchique de domaine, où chaque domaine enfant hérite de la confiance du domaine parent.
## 2. Cross-Link Trust
- **Description** : Un lien de confiance créé manuellement entre deux domaines dans la même forêt, mais qui ne sont pas dans une relation parent-enfant immédiate.
- **Caractéristique** : Transitive.
- **Usage** : Optimise l'authentification entre domaines et améliore les performances en réduisant les chemins de confiance à parcourir.
## 3. External Trust
- **Description** : Un lien de confiance non transitive créé manuellement entre un domaine AD et un domaine dans une forêt externe ou un domaine non-AD (comme Windows NT).
- **Caractéristique** : Non-transitive, limitée aux deux domaines spécifiques.
- **Usage** : Utilisé pour fournir l'accès à des ressources entre organisations ou entre une forêt AD et un système d'annuaire non-AD.
## 4. Tree-Root Trust
- **Description** : Un lien de confiance qui se forme automatiquement entre le domaine racine d'un nouvel arbre et le domaine racine de la forêt dans Active Directory.
- **Caractéristique** : Transitive.
- **Usage** : Permet aux utilisateurs de différents arbres au sein d'une même forêt de s'authentifier et d'accéder aux ressources.
## 5. Forest Trust
- **Description** : Un lien de confiance créé entre les domaines racines de deux forêts différentes.
- **Caractéristique** : Peut être transitive ou non-transitive, selon la configuration.
- **Usage** : Permet l'authentification et l'accès aux ressources entre différentes forêts AD.

## 6. Transitive vs Non-Transitive Trust
- **Transitive** : La confiance s'étend au-delà des deux domaines initiaux à d'autres domaines dans la même hiérarchie.
- **Non-Transitive** : La confiance est limitée aux deux domaines spécifiques dans le lien de confiance.
## Tableau récapitulatif 

| Type de Lien de Confiance | Caractéristique | Description et Usage                                                                                      |
|---------------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| Parent-Child Trust        | Transitive      | Automatiquement établi entre un domaine parent et son domaine enfant. Hérite de la confiance du parent.   |
| Cross-Link Trust          | Transitive      | Créé manuellement entre deux domaines dans la même forêt qui ne sont pas directement en relation parent-enfant. Optimise l'authentification. |
| External Trust            | Non-Transitive  | Lien manuel entre un domaine AD et un domaine externe ou non-AD. Utilisé pour l'accès entre organisations ou systèmes différents.     |
| Tree-Root Trust           | Transitive      | Automatiquement établi entre le domaine racine d'un nouvel arbre et le domaine racine de la forêt AD. Permet l'authentification entre arbres.  |
| Forest Trust              | Transitive ou Non-Transitive | Créé entre les domaines racines de deux forêts AD différentes. Permet l'authentification et l'accès entre forêts. |
| Transitive Trust          | Transitive      | La confiance s'étend au-delà des deux domaines initiaux à d'autres domaines dans la même hiérarchie.     |
| Non-Transitive Trust      | Non-Transitive  | La confiance est limitée aux deux domaines spécifiques dans le lien de confiance.                         |



# 9) Authentification des services 

## LM
LM, qui signifie "LAN Manager," est un ancien protocole d'authentification développé par Microsoft et IBM. Il a été conçu initialement pour les réseaux LAN Manager, mais a ensuite été utilisé dans les premières versions de Windows. Voici quelques points clés sur LM :

### Caractéristiques de LM
1. **Méthode de Hashage Faible** :
   - LM utilise une méthode de hashage du mot de passe relativement faible. Le mot de passe est divisé en deux parties de 7 caractères chacune, complétées avec des caractères nuls si nécessaire, puis chaque partie est hashée séparément.
   - Cette approche est vulnérable aux attaques par force brute car chaque moitié du mot de passe peut être craquée indépendamment.

2. **Stockage des Hashes** :
   - Les hashes LM sont stockés sur le système ou le contrôleur de domaine, ce qui représente un risque de sécurité si ces données sont compromises.

3. **Manque de Sécurité Moderne** :
   - LM ne prend pas en charge des fonctionnalités de sécurité modernes telles que le salage (ajout d'une donnée aléatoire au mot de passe avant le hashage) ou des algorithmes de hashage plus robustes.
### Utilisation et Limitations
- **Anciens Systèmes Windows** : LM était utilisé dans les versions plus anciennes de Windows, comme Windows NT et Windows 95.
- **Compatibilité** : LM a été conservé dans les versions ultérieures de Windows pour des raisons de compatibilité avec les anciens systèmes, mais il est souvent désactivé par défaut pour des raisons de sécurité.
- **Vulnérabilités** : En raison de ses faiblesses en matière de sécurité, LM est considéré comme obsolète et vulnérable aux attaques modernes.
### Remplacement par NTLM et Kerberos
- **NTLM** : NT LAN Manager (NTLM) a été introduit comme une amélioration de LM, offrant une meilleure sécurité, bien qu'il soit lui-même moins sécurisé que les protocoles plus modernes.
- **Kerberos** : Dans les environnements Active Directory actuels, Kerberos est le protocole d'authentification standard, remplaçant NTLM et LM en raison de ses fonctionnalités de sécurité supérieures.

## NTLM (v1,v2,v3)

NTLM (NT LAN Manager) est un ancien protocole d'authentification utilisé par Microsoft avant l'adoption de Kerberos comme standard dans les environnements Active Directory. Voici une présentation structurée de NTLM, similaire à votre leçon sur Kerberos :
### Les Acteurs de NTLM
1. **Client** : L'utilisateur ou l'ordinateur qui demande l'accès à une ressource.
2. **Serveur/Ressource** : Le serveur qui héberge le service ou la ressource à laquelle l'utilisateur souhaite accéder.
3. **Domain Controller (DC)** : Le contrôleur de domaine qui valide l'authentification NTLM. Contrairement à Kerberos, il n'y a pas de serveur d'authentification ou de serveur de distribution de tickets séparés.
### Processus d'Authentification NTLM
1. **Demande d'Accès** :
   - Le client tente d'accéder à une ressource et envoie une demande au serveur.
2. **Challenge du Serveur** :
   - Le serveur envoie un challenge au client. Ce challenge est un nombre aléatoire qui sera utilisé dans la suite du processus d'authentification.
3. **Réponse du Client** :
   - Le client répond au challenge. Cette réponse inclut un hash du mot de passe de l'utilisateur, mélangé avec le challenge du serveur.
4. **Validation par le Domain Controller (DC)** :
   - Le serveur envoie la réponse du client au DC pour validation.
   - Le DC vérifie le hash en utilisant le mot de passe stocké dans Active Directory. Si le hash correspond, l'authentification est réussie.
5. **Accès Autorisé** :
   - Si l'authentification est réussie, le serveur accorde l'accès au client.
### Particularités de NTLM
- **Moins Sécurisé que Kerberos** : NTLM est considéré comme moins sécurisé que Kerberos car il repose sur des mécanismes de hash de mot de passe, ce qui le rend plus vulnérable aux attaques.
- **Pas de Billets/Tickets** : Contrairement à Kerberos, NTLM n'utilise pas de système de tickets. L'authentification repose sur un échange de challenge-réponse.
- **Moins d'Interopérabilité** : NTLM a des limitations en termes d'interopérabilité et d'évolutivité par rapport à Kerberos.
- **Utilisation dans les Anciens Systèmes** : NTLM est souvent utilisé dans des systèmes plus anciens ou dans des cas où Kerberos n'est pas disponible ou applicable.

### Conclusion
NTLM est un protocole d'authentification plus ancien utilisé dans les réseaux Microsoft. Bien qu'il soit toujours pris en charge pour des raisons de compatibilité, Kerberos est préféré dans les environnements modernes en raison de sa meilleure sécurité et de sa plus grande efficacité. NTLM reste pertinent dans certains contextes, en particulier dans les systèmes plus anciens ou les situations où Kerberos ne peut être déployé.

## Kerberos 
* Kerberos est un protocole d'authentification par défaut pour les utilisateurs et ressources AD
* Kerberos utilise un système de ticket plutot que de mot de passe
### Les acteurs de Kerberos 
1. **Client** : L'utilisateur ou l'ordinateur qui demande l'accès à une ressource.
2. **Ressource (ou Service)** : Le serveur qui héberge le service ou la ressource à laquelle l'utilisateur souhaite accéder.
3. **Serveur d'Authentification (AS) et Serveur de Distribution de Tickets (TGS)** : Ces composants, souvent situés sur la même machine, forment le Key Distribution Center (KDC). C'est le cœur de l'infrastructure Kerberos, responsable de l'authentification des clients et de la délivrance des tickets d'accès pour les ressources.
### Processus d'authentification
1. Le client tente d'accéder à une ressource.
2. La ressource indique que l'authentification Kerberos est nécessaire.
3. Le client communique avec le AS (Authentication Service) du KDC (Serveur Kerberos).
	1. Le client envoie une demande de Ticket Granting Ticket (TGT) au AS.
	2. Le AS vérifie si le client est enregistré dans Active Directory. Si c'est le cas, il génère un TGT, chiffré avec la clé secrète du TGS (Ticket Granting Service, une composante du KDC).
	3. Le client reçoit le TGT chiffré. Pour accéder à une ressource spécifique, le client présente ce TGT au TGS et demande un Service Ticket (ST) pour cette ressource.
	4. Le TGS déchiffre le TGT pour s'assurer de l'authenticité du client. Si le TGT est valide, le TGS génère un ST pour le client, chiffré avec la clé secrète de la ressource/service désiré.
4. Le client présente ce ST à la ressource pour demander l'accès.
5. La ressource déchiffre le ST avec sa propre clé secrète. Si le déchiffrement est réussi et que le ticket est valide, l'accès est accordé selon les conditions du ST.
### Précisions sur le ST :
* Le Service Ticket (ST) contient des informations telles que :
	- le nom de l'utilisateur
	- la durée de validité du ticket
	- une clé de session pour chiffrer la communication entre la ressource et le client.
### Précisions sur le chiffrement
- Il n'y a pas de concept de "clé publique" et "clé privée" pour Kerberos comme dans les systèmes basés sur RSA. Kerberos utilise des clés secrètes symétriques. Donc, lorsque l'on dit "chiffré avec la clé de X", c'est une clé secrète unique à X.
- Le client ne déchiffre jamais le TGT. Seul le TGS peut le faire. C'est une des sécurités fondamentales de Kerberos : le client prouve son identité sans jamais connaître la clé secrète du TGS.
