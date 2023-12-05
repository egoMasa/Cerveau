Fonctionnement réseau AD 

## 1. Windows Serveur Active Directory
-  **Annuaire d'Entreprise** : AD sur Windows Server agit comme un annuaire centralisé listant les utilisateurs, les groupes, les machines, et les ressources. Il stocke également des attributs pour chaque objet, qui définissent les droits d'accès et d'autres propriétés.
- **Politiques de Groupe** : Configurer des politiques (GPOs) dans AD pour appliquer divers paramètres aux ordinateurs et utilisateurs du domaine, comme les fonds d'écran, les scripts de démarrage, les paramètres de sécurité, etc.
## 2. Contrôleurs de Domaine/Serveurs LDAP
-  **Réplication d'AD** : Les contrôleurs de domaine contiennent une réplique complète de la base de données AD. Ils gèrent l'authentification et les requêtes d'annuaire pour les utilisateurs et les machines du domaine.
- **Serveurs LDAP** : Les contrôleurs de domaine utilisent le protocole LDAP pour communiquer avec les applications et services qui requièrent l'accès aux données de l'annuaire.
### Scénarios Classiques de Communication

1. **Authentification de l'Utilisateur** :
    - **Demande** : Le poste client envoie une demande d'authentification au serveur LDAP lorsqu'un utilisateur essaie de se connecter.
    - **Réponse** : Le serveur LDAP vérifie les informations d'authentification (nom d'utilisateur et mot de passe) contre la base de données AD et renvoie une réponse indiquant si l'authentification est réussie ou non.
2. **Accès aux Ressources Réseau** :
    - **Demande** : Lorsqu'un utilisateur tente d'accéder à une ressource partagée sur le réseau (comme un dossier partagé ou une imprimante), le poste client peut interroger le serveur LDAP pour vérifier les droits d'accès de l'utilisateur.
    - **Réponse** : Le serveur LDAP renvoie les informations relatives aux droits de l'utilisateur, permettant ou refusant l'accès à la ressource.
3. **Recherche d'Informations dans l'Annuaire** :
    - **Demande** : Les applications sur le poste client peuvent effectuer des requêtes LDAP pour obtenir des informations sur d'autres utilisateurs, groupes ou objets dans AD.
    - **Réponse** : Le serveur LDAP renvoie les informations demandées, telles que les adresses e-mail, les numéros de téléphone, les appartenances à des groupes, etc.
4. **Application des Politiques de Groupe (GPOs)** :
    - **Demande** : À l'ouverture de session ou périodiquement, le poste client peut interroger le serveur LDAP pour les dernières politiques de groupe applicables.
    - **Réponse** : Le serveur LDAP fournit les détails des GPOs, qui sont ensuite appliqués sur le poste client (par exemple, les paramètres de sécurité, les scripts de démarrage, etc.).
5. **Mise à Jour des Informations Utilisateur ou Machine** :
    - **Demande** : Le poste client peut envoyer des mises à jour au serveur LDAP, comme un changement de mot de passe ou la mise à jour des informations de l'utilisateur.
    - **Réponse** : Le serveur LDAP traite ces demandes et met à jour les informations dans AD en conséquence.
### Protocole LDAP
Les messages LDAP (Lightweight Directory Access Protocol) sont structurés de manière à faciliter les interactions avec un service d'annuaire, tel qu'Active Directory. Les éléments clés de ces messages varient selon le type d'opération (authentification, recherche, mise à jour, etc.), mais certains composants sont couramment utilisés. Voici une explication de la logique de ces messages :

#### Composants Essentiels des Messages LDAP

1. **Opération (Type de Message)** :
   - **Importance** : Détermine le type d'action demandée, par exemple, une opération de liaison (bind) pour l'authentification, une opération de recherche, une mise à jour, etc.
   - **Exemple** : `Bind Request`, `Search Request`.

2. **DN (Distinguished Name)** :
   - **Importance** : Sert à identifier de manière unique un objet dans l'annuaire. Dans une requête de liaison, il s'agit souvent du DN de l'utilisateur qui se connecte.
   - **Exemple** : `CN=John Doe,OU=Users,DC=example,DC=com`.

3. **Attributs et Filtres (Pour les Requêtes de Recherche)** :
   - **Importance** : Spécifient les critères de recherche et les attributs à retourner.
   - **Exemple** : `(objectClass=user)`, `sAMAccountName=jdoe`, attributs comme `cn`, `mail`.

4. **Base DN (Pour les Recherches)** :
   - **Importance** : Indique le point de départ dans la hiérarchie de l'annuaire pour la recherche.
   - **Exemple** : `DC=example,DC=com`.

5. **Scope (Pour les Recherches)** :
   - **Importance** : Détermine l'étendue de la recherche (par exemple, un seul objet, un niveau ou toute la sous-arborescence).
   - **Exemple** : `Subtree`, `OneLevel`.

6. **Credentials (Pour Bind Request)** :
   - **Importance** : Les informations d'authentification, comme le mot de passe.
   - **Exemple** : [Mot de passe crypté].
#### Composants Facultatifs ou Contextuels

1. **Port** :
   - Utilisé pour spécifier le port de communication (par défaut, 389 pour LDAP, 636 pour LDAPS).
2. **Version du Protocole** :
   - Généralement la version 3 est utilisée.
3. **Attributs Additionnels (Pour les Mises à Jour)** :
   - Pour des opérations telles que la modification ou la suppression, des attributs spécifiques à modifier ou supprimer.
4. **Paging Controls** :
   - Utilisés pour gérer les résultats de recherche volumineux en plusieurs segments.
5. **Security Controls** :
   - Comme StartTLS, pour initier une connexion sécurisée sur un canal LDAP standard.

## 3. ADFS pour l'Accès aux Ressources Externes
- **Authentification et Fédération d'Identités** : ADFS sert de système d'authentification pour accéder aux ressources externes. Il permet l'authentification unique (SSO) pour les utilisateurs en dehors du réseau local, souvent pour des services cloud.
- **Rôle de Passerelle** : ADFS agit comme une passerelle entre le réseau interne de l'entreprise et les fournisseurs de services externes, permettant aux utilisateurs de conserver les mêmes identifiants (nom d'utilisateur et mot de passe) sur les deux réseaux.

### Scénario d'Authentification Unique (SSO)

1. **Accès à une Application Fédérée**
   - **Action de l'Utilisateur** : L'utilisateur tente d'accéder à une application fédérée (par exemple, une application cloud).
   - **Redirection** : L'application redirige la demande d'authentification vers ADFS.

2. **Demande d'Authentification auprès d'ADFS**
   - **Contenu de la Demande** :
 ```
 GET /adfs/ls/ 
 SAMLRequest=<Encodé-SAML-AuthnRequest>
 RelayState=<État-Relais>
 ```

- **Explication** : La demande contient une `AuthnRequest` SAML encodée, indiquant que l'utilisateur souhaite s'authentifier.

3. **Authentification et Réponse d'ADFS**
   - **Contenu de la Réponse** :
     ```xml
     <samlp:Response>
       <Assertion>
         <Subject>
           <NameID>john.doe@example.com</NameID>
         </Subject>
         <Conditions>
           <AudienceRestriction>
             <Audience>Identifiant-Audience-Application</Audience>
           </AudienceRestriction>
         </Conditions>
         <AuthnStatement>...</AuthnStatement>
         <AttributeStatement>...</AttributeStatement>
       </Assertion>
     </samlp:Response>
     ```
   - **Explication** : ADFS renvoie une réponse SAML contenant une `Assertion`, qui inclut l'identité de l'utilisateur (`NameID`), les conditions de validité de l'assertion, et des déclarations sur l'authentification et les attributs.

### Scénario de Fédération d'Identités

1. **Accès à une Ressource Partenaire**
   - **Action de l'Utilisateur** : L'utilisateur tente d'accéder à une ressource offerte par un partenaire fédéré.
   - **Redirection** : La demande est redirigée vers ADFS pour l'authentification.

2. **Demande d'Authentification et Assertion SAML**
   - **Contenu de la Demande** : Similaire à ci-dessus, une `AuthnRequest` SAML.
   - **Réponse d'ADFS** : ADFS renvoie une `Assertion` SAML après l'authentification réussie.

3. **Utilisation de l'Assertion pour Accéder à la Ressource**
   - **Action de l'Utilisateur** : L'utilisateur présente l'assertion SAML au service partenaire.
   - **Validation par le Partenaire** : Le partenaire valide l'assertion SAML et accorde l'accès basé sur les claims fournis.

### Notes Importantes

- **Format des Échanges** : Les échanges dans ADFS sont souvent basés sur XML et suivent les standards SAML pour l'authentification et les assertions.
- **Sécurité** : Les assertions SAML sont généralement signées numériquement et, dans certains cas, chiffrées pour assurer la sécurité et l'intégrité des données.
- **Redirections et Communications Web** : Ces interactions impliquent souvent des redirections Web et des échanges de messages HTTP/HTTPS.

### Résumé

En résumé, les communications dans ADFS impliquent des interactions entre l'utilisateur, ADFS, et les applications ou services fédérés, souvent en utilisant le protocole SAML pour les authentifications et les échanges d'informations d'identité. Les scénarios d'authentification unique et de fédération d'identités sont typiques, où ADFS sert de point central pour authentifier les utilisateurs et fournir des informations sécurisées sur l'identité et les droits d'accès.
# 1) Pourquoi AD
* Service d'annuaire pour les environnements Windows
* Organisé via une structure hiérachique
* Permet de centralisé la gestion des ressources d'un organisations 
	* Utilisateurs
	* Ordinateurs
	* Groupes
	* Partages
	* Stratégies de groupe
	* Approbation
* Fournit des systèmes d'authentification et d'autorisation sur le réseau
* On peut imaginer AD comme une base de données accessible à tous les utilisateurs et équipements mais uniquement en droit de lecture
* N'importe qui peut énumérer la plupart des objets AD meme sans droits particuliers, comme : 

|   |   |
|---|---|
|Ordinateurs du domaine|Utilisateurs du domaine|
|Informations sur le groupe de domaine|Unités organisationnelles (UO)|
|Politique de domaine par défaut|Niveaux de domaine fonctionnel|
|Politique de mot de passe|Objets de stratégie de groupe (GPO)|
|Fiducies de domaine|Listes de contrôle d'accès (ACL)|

# 2) Fondamentaux AD
## 1. Structure d'annuaire actif
* AD FS 
	* Stocke des informations telles que les noms d'utilisateur et les mots de passe et gère les droits nécessaires aux utilisateurs autorisés pour accéder à ces informations.
* Structure hiérarchique 
	* Foret : Contient plusieurs domaines
		* Domaine
			* Utiliateurs 
			* Groupes
			* Equipements
			* Partage
```shell-session
INLANEFREIGHT.LOCAL/
├── ADMIN.INLANEFREIGHT.LOCAL
│   ├── GPOs
│   └── OU
│       └── EMPLOYEES
│           ├── COMPUTERS
│           │   └── FILE01
│           ├── GROUPS
│           │   └── HQ Staff
│           └── USERS
│               └── barbara.jones
├── CORP.INLANEFREIGHT.LOCAL
└── DEV.INLANEFREIGHT.LOCAL
```
* Dans une foret qui est un conteneur de domaine on peut avoir un ensemble de domaine parent qui eux meme possède des sous sous domaine 

## 2. Terminologie AD 
* Objet
	* Défini une ressource, peut importe laquelle (Unité d'organisation UO (bloc), Equipements, utilisateurs, controleur de domaine)
* Attribut
	* Chaque objets possède des attributs qui le caratérise (nom)
	* Tous les attributs ont un nom associé qu'utilise LDAP pour faire des requêtes comme displayName, Full Name, given name, First Name
* Schema 
	* C'est un modèle AD (template), d'environnement d'entreprise
	* Définit les types d'objets qui peuvent exister la BDD AD et les attributs possible, en gros ca définit que qui peut exister les informations necessaires à leur existance
* Domaine 
	* Un domaine est une zone qui englobe un nombre d'objets comme des utilisateurs, groupes, ressources, équipement
	* On peut comparer un domaine AD à une ville, une ville qui est englobé dans une région (foret)
* Foret
	* Une foret est une ensemble de domaine AD, il englobe tout en jouant le role de conteneur, on peut le considérer comme la racine
	* Une foret englobe un ensemble d'arbre (domaine) AD
* Arbre 
	* Un arbre est un regroupement de sous domaines relié à une racine
	* Exemple : exemple.com est la racine, admin.exemple.com est un sous domaine et il peut y avoir X sous domaines tout ce qui est relié à un domaine racine est un arbre
* GUID
	* Valeur de 128bits attribué à un utilisateur/groupe/domaine
	* Correspond à une adresse MAC, ce GUID est unique 
	* C'est son identifiant au sein de AD
	* Stocké ans l'attribut : ObjectGUID
* Principes de sécurité
	* Objets qui peuvent gérer l'accès à d'autre ressources au sein du domaine
* SID (Identifiant de sécurité)
	* Identifiant unique pour une entité(groupe) de sécurité au sein de AD
	* Cette SID dis quelles sont les actions possibles par l'utilisateurs
	* Permet de vérifier les droits chaque fois que l'utilisateur effectue une action
* Nom distinctif (DN) : 
	* C'est comme l'adresse complète d'une maison. Le DN fournit le chemin complet pour localiser un objet dans l'Active Directory (AD), en commençant par le nom le plus spécifique (comme le nom d'une personne) et en remontant jusqu'au domaine le plus général. C'est un identifiant unique pour chaque objet dans AD. Pensez-y comme si vous donniez à quelqu'un les directives étape par étape pour se rendre à votre domicile depuis une grande ville.
	* _Exemple :_ `cn=bjones, ou=IT, ou=Employees, dc=inlanefreight, dc=local`
* Nom distinctif relatif (RDN) : 
	* C'est comme le nom d'une maison ou le numéro sur une rue. Le RDN est simplement la partie du DN qui est unique à un niveau spécifique de l'AD. C'est comme si vous disiez à quelqu'un comment trouver votre maison sur une rue spécifique, sans donner toute l'adresse.
	* _Exemple :_ `bjones` (en référence à l'exemple du DN ci-dessus)
* Catalogue global 
	* Centre d'information global sur l'annuaire AD
	* Liste les informations de chaque domaines
	* A une vue d'ensemble sur chaque objets et attributs
	* Quand on sait pas exactement l'emplacement d'un objet, le catalogue le sait
* Read-Only Domain Controller (RODC)
	* possède une base de données Active Directory en lecture seule. 
	* Aucun mot de passe de compte AD n'est mis en cache sur un RODC (à l'exception des mots de passe du compte d'ordinateur RODC et du KRBTGT RODC). 
	* Aucune modification n'est transmise via la base de données AD, SYSVOL ou DNS d'un RODC. 
	* Les RODC comprennent également un serveur DNS en lecture seule, permettent la séparation des rôles d'administrateur, réduisent le trafic de réplication dans l'environnement et empêchent les modifications de SYSVOL d'être répliquées vers d'autres DC.
* Replication
	* Permet d'assurer que chaque controleur de domaine possède les memes informations
* SPN 
	* Identifiant unique d'un service
* GPO (Group Policy Object)
	* Ensemble de règles et de contraintes appliqués au membres d'un groupe
* ACL 
	* Liste qui dit qui à accès à quels services
* ACE 
	* Liste les parties accessibles du service pour l'utilisateur
* DACL 
	* Système qui détermine qui peut accéder au service et quelle actions il peut faire

* SACL
	* Système qui enregistre les authentifications et actions
* FQDN 
	* Le chemin complet de la racine jusqu'au bout pour déterminer un ordinateur ou un host `DC01.INLANEFREIGHT.LOCAL

* Tombstone
	* Container avec les objets supprimés
	* Garde la possibilité de le récupérer 
* AD Recycle Bin 
	* Pareil mais en améliorer
* SYSVOL
	* Contient des directives, des scripts, et des règles (policies) qui doivent être respectées par les ordinateurs et les utilisateurs
	* Ce répertoire est répliqué sur chaques  DC via FRS File Replication Services
* AdminSDHoler
	* Objet utilisé pour gérer les ACL pour les personnes avec des privilèges
	* Conteneur qui contient une descripteur de sécurité appliqué aux membres des groupes protégés.
* dsHeuristics
	* L'attribut dsHeuristics est une valeur de chaîne définie sur l'objet Directory Service utilisé pour définir plusieurs paramètres de configuration à l'échelle de la forêt. 
	* L'un de ces paramètres consiste à exclure les groupes intégrés de la liste des groupes protégés. 
	* Les groupes de cette liste sont protégés contre les modifications par l'objet AdminSDHolder. 
	* Si un groupe est exclu via l'attribut dsHeuristics, les modifications qui l'affectent ne seront pas annulées lors de l'exécution du processus SDProp.
* adminCount
	* L'attribut adminCount détermine si le processus SDProp protège ou non un utilisateur. 
	* Si la valeur est fixée à 0 ou n'est pas spécifiée, l'utilisateur n'est pas protégé. 
	* Si la valeur de l'attribut est fixée à value, l'utilisateur est protégé. Dans un environnement interne, les attaquants recherchent souvent des comptes dont l'attribut adminCount est défini sur 1.
	* Il s'agit souvent de comptes privilégiés qui peuvent donner lieu à d'autres accès ou à la compromission totale du domaine.
* Utilisateurs et ordinateurs d'Active Directory (ADUC)
	* ADUC est une console GUI couramment utilisée pour gérer les utilisateurs, les groupes, les ordinateurs et les contacts dans AD. 
	* Les modifications apportées dans ADUC peuvent également être effectuées via PowerShell.
* ADSI Edit
	* Outil GUI utilisé pour gérer les objets dans AD. 
	* Il permet d'accéder à bien plus d'informations que celles disponibles dans ADUC et peut être utilisé pour définir ou supprimer n'importe quel attribut disponible sur un objet, ainsi que pour ajouter, supprimer et déplacer des objets.
	* Il s'agit d'un outil puissant qui permet à l'utilisateur d'accéder à AD à un niveau beaucoup plus profond.
	* Il convient d'être très prudent lors de l'utilisation de cet outil, car des modifications peuvent entraîner des problèmes majeurs dans AD.

* sIDHistory
	* Cet attribut contient tous les SID attribués précédemment à un objet. 
	* Il est généralement utilisé dans les migrations afin qu'un utilisateur puisse conserver le même niveau d'accès lorsqu'il migre d'un domaine à un autre.
	* Cet attribut peut être utilisé de manière abusive s'il n'est pas sécurisé, ce qui permet à un attaquant d'obtenir l'accès élevé qu'un compte avait avant une migration si le filtrage des SID (ou la suppression des SID d'un autre domaine du jeton d'accès d'un utilisateur qui pourrait être utilisé pour l'accès élevé) n'est pas activé.
* NTDS.DIT
	* Le fichier NTDS.DIT peut être considéré comme le cœur d'Active Directory. 
	* Il est stocké sur un contrôleur de domaine à l'emplacement C:\NWindowsTMNTDS\ 
	* Constitue une base de données qui stocke les données AD telles que les informations sur les objets utilisateurs et groupes, l'appartenance à un groupe et, ce qui est le plus important pour les attaquants et les testeurs de pénétration, les hachages de mots de passe de tous les utilisateurs du domaine. 
	* Une fois le domaine entièrement compromis, un attaquant peut récupérer ce fichier, extraire les hachages et les utiliser pour effectuer une attaque de type "pass-the-hash" ou les craquer hors ligne à l'aide d'un outil tel que Hashcat afin d'accéder à d'autres ressources du domaine. 
	* Si le paramètre Stocker le mot de passe avec un cryptage réversible est activé, le NTDS.DIT stockera également les mots de passe en clair pour tous les utilisateurs créés ou qui ont modifié leur mot de passe après que cette politique a été définie. 
	* Bien que cela soit rare, certaines organisations peuvent activer ce paramètre si elles utilisent des applications ou des protocoles qui ont besoin d'utiliser le mot de passe existant d'un utilisateur (et non Kerberos) pour l'authentification.



## 3. Objets AD

1. **Computer** : Il représente un ordinateur ou un serveur dans le réseau. Il contient des informations spécifiques à cet appareil.
2. **OU (Container)** : L'Unité organisationnelle (OU) est une subdivision d'un domaine AD qui peut contenir tous types d'objets comme des utilisateurs, des groupes, et même d'autres OUs. C'est principalement utilisé pour organiser et déléguer des droits administratifs.
3. **User** : Il représente un compte d'utilisateur. Il contient des informations spécifiques à cet utilisateur, comme son nom, son mot de passe, et d'autres attributs.
4. **Domain** : Un domaine est une limite administrative et de sécurité dans AD. Il contient un ensemble d'objets et offre une base pour la stratégie de sécurité et la gestion des noms.
5. **Groups** : Les groupes servent à rassembler des utilisateurs, des ordinateurs, et d'autres groupes pour des besoins d'administration et de sécurité. Ils facilitent la gestion des droits d'accès.
6. **Printers** : Il représente une imprimante partagée dans le réseau. Cet objet contient des informations sur l'imprimante et comment y accéder.
7. **Contacts** : Un contact est un objet qui représente une personne mais qui n'a pas les droits et permissions d'un objet utilisateur. C'est comme une fiche d'informations.
8. **Shared Folders** : Cet objet représente un dossier partagé sur le réseau. Il contient des informations sur le partage et les droits d'accès.
9. **Sites** : Un site représente un emplacement physique ou une partie du réseau. Dans AD, les sites aident à gérer la réplication et le trafic réseau.
10. **Built-in** : Il s'agit d'une OU par défaut qui contient des groupes préconfigurés avec des permissions spéciales, comme les administrateurs du domaine.


## 4. Fonctionnalités AD 

### FSMO
**FSMO** (Flexible Single Master Operations) fait référence à des rôles spécifiques dans un environnement Active Directory (AD) qui ne doivent être détenus que par un seul contrôleur de domaine (DC) à la fois pour éviter les conflits de données.

Voici une explication simplifiée des différents rôles FSMO:
1. **Schema Master** :
    - **Description**: Il gère une copie en lecture/écriture du schéma AD. Le schéma détermine tous les types d'attributs qu'un objet peut avoir dans AD.
2. **Domain Naming Master** :
    - **Description**: Son rôle est de superviser les noms de domaine dans une forêt AD. Il garantit que deux domaines ne portent pas le même nom.
3. **Relative ID (RID) Master** :
    - **Description**: Chaque objet dans AD a un identificateur unique appelé SID. Le RID Master donne des "paquets" de RIDs à d'autres DCs, qui les utilisent ensuite pour créer de nouveaux objets. Ce processus garantit que chaque objet a un SID unique.
4. **PDC Emulator** :
    - **Description**: Dans un domaine, le DC avec le rôle de PDC Emulator est le DC "principal". Il répond aux demandes d'authentification, gère les changements de mot de passe et est responsable des Group Policy Objects (GPOs). De plus, il synchronise l'heure dans le domaine.
5. **Infrastructure Master** :
    - **Description**: Il travaille dans des environnements avec plusieurs domaines. L'Infrastructure Master est comme un traducteur pour les identifiants uniques utilisés dans AD. Si ce rôle ne fonctionne pas correctement, au lieu de voir des noms d'utilisateur ou de groupe, vous pourriez voir de longues chaînes de caractères incompréhensibles.


### **Domain and Forest Functional Levels**
* Définit les fonctionnalités disponibles dans un domaine ou une forêt Active Directory (AD). Plus le niveau fonctionnel est élevé, plus les fonctionnalités disponibles sont avancées. Le niveau fonctionnel est déterminé par la version la plus ancienne du système d'exploitation de vos contrôleurs de domaine (DC).

- **Domain Functional Level (DFL)** : Il s'applique à toutes les domaines et détermine les fonctionnalités disponibles au sein de ce domaine.
    
- **Forest Functional Level (FFL)** : Il s'applique à toute la forêt AD et détermine les fonctionnalités qui sont activées à travers tous les domaines dans cette forêt.

Maintenant, regardons les niveaux fonctionnels de domaine que vous avez listés:
1. **Windows 2000 native**:
    - **Fonctionnalités**: Groupes universels, emboîtement de groupes, conversion de groupes, historique SID.
    - **DCs supportés**: De Windows 2000 à Windows Server 2008 R2.
2. **Windows Server 2003**:
    - **Fonctionnalités**: Outil Netdom.exe, attribut lastLogonTimestamp, conteneurs pour utilisateurs/computers, délégation contrainte, authentification sélective.
    - **DCs supportés**: De Windows Server 2003 à Windows Server 2012 R2.
3. **Windows Server 2008**:
    - **Fonctionnalités**: Support DFS en réplication, support AES pour Kerberos, politiques de mot de passe à grain fin.
    - **DCs supportés**: De Windows Server 2008 à Windows Server 2012 R2.
4. **Windows Server 2008 R2**:
    - **Fonctionnalités**: Assurance du mécanisme d'authentification, comptes de service gérés.
    - **DCs supportés**: De Windows Server 2008 R2 à Windows Server 2012 R2.
5. **Windows Server 2012**:
    - **Fonctionnalités**: Support KDC pour les revendications, l'authentification composée et le blindage Kerberos.
    - **DCs supportés**: Windows Server 2012 et 2012 R2.
6. **Windows Server 2012 R2**:
    - **Fonctionnalités**: Protections supplémentaires pour les membres du groupe "Protected Users", politiques d'authentification.
    - **DCs supportés**: Windows Server 2012 R2.
7. **Windows Server 2016**:
    - **Fonctionnalités**: Exigence de carte à puce pour la connexion interactive, nouvelles fonctionnalités Kerberos.
    - **DCs supportés**: Windows Server 2016 et 2019.

En élevant le niveau fonctionnel, vous déverrouillez ces fonctionnalités, mais cela signifie également que vous ne pouvez pas faire fonctionner des DCs avec des versions de système d'exploitation antérieures à celles spécifiées.


### Trusts 
Le concept de **Trusts** dans Active Directory (AD) concerne la manière dont différents domaines ou forêts établissent des relations d'authentification. Ces relations permettent à des utilisateurs d'un domaine d'accéder à des ressources ou d'administrer un autre domaine. En d'autres termes, un trust crée un pont sécurisé à travers lequel deux domaines peuvent partager des informations d'authentification.

Les Trusts sont essentiels pour déterminer comment l'authentification et l'autorisation sont gérées entre des domaines ou des forêts distincts. Examinons les différents types de Trusts:

1. **Parent-child (Parent-enfant)**:
   - **Description**: Il s'agit du type de trust le plus courant. Lorsqu'un domaine enfant est créé dans un domaine parent, un trust bidirectionnel et transitif est automatiquement établi entre eux. Cela signifie que les deux domaines peuvent se faire confiance mutuellement pour l'authentification.
2. **Cross-link (Liaison croisée)**:
   - **Description**: Il s'agit d'une liaison créée pour accélérer le processus d'authentification entre deux domaines enfants dans des arbres différents d'une même forêt, sans passer par leurs domaines racine respectifs.
3. **External (Externe)**:
   - **Description**: Ce type de trust est utilisé pour établir une relation entre deux domaines situés dans des forêts différentes et qui ne sont pas déjà liés par un trust de forêt. Il s'agit d'un trust non-transitif, ce qui signifie qu'il n'est pas hérité par d'autres domaines dans la forêt. Le filtrage SID est utilisé pour garantir la sécurité.
4. **Tree-root (Racine de l'arbre)**:
   - **Description**: Lorsqu'une nouvelle racine d'arbre est ajoutée à une forêt, un trust bidirectionnel et transitif est automatiquement établi entre la racine de cette forêt et la nouvelle racine d'arbre.
5. **Forest (Forêt)**:
   - **Description**: C'est un trust transitif entre deux racines de forêts distinctes. Il permet à toutes les entités de chaque forêt de s'authentifier mutuellement. Il est souvent utilisé pour fusionner deux entreprises possédant chacune sa propre forêt AD.

En comprenant comment fonctionnent ces trusts, les administrateurs peuvent efficacement gérer et sécuriser l'accès entre différents domaines et forêts, tout en fournissant la flexibilité nécessaire pour répondre aux besoins changeants de l'entreprise.

Les "Trusts" dans Active Directory permettent à deux domaines de s'authentifier mutuellement. Ces Trusts peuvent avoir différentes propriétés :

1. **Transitivité**:
   - **Transitif**: Si un domaine A fait confiance à un domaine B, et que le domaine B fait confiance à un domaine C, alors, de manière transitive, le domaine A fait également confiance au domaine C.
   - **Non-transitif**: La confiance est limitée uniquement aux deux domaines concernés. Dans l'exemple précédent, le domaine A ne ferait pas automatiquement confiance au domaine C.

2. **Directionnalité**:
   - **Bidirectionnel (deux voies)**: Les utilisateurs des deux domaines peuvent accéder aux ressources de l'autre. Si le domaine A et le domaine B ont une confiance bidirectionnelle, les utilisateurs des deux domaines peuvent partager des ressources.
   - **Unidirectionnel (une voie)**: Seuls les utilisateurs du domaine qui est "confiant" peuvent accéder aux ressources de l'autre domaine. Si le domaine A fait confiance au domaine B, seulement les utilisateurs du domaine B peuvent accéder aux ressources du domaine A, et non l'inverse.

En résumé, les "Trusts" définissent comment les domaines interagissent et partagent des ressources dans Active Directory. La nature transitive ou non-transitive détermine la portée de cette confiance, tandis que la directionnalité détermine qui peut accéder à quoi.

