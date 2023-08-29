### 1. C'est quoi le protocole

* ***Kerberos** est un protocole d'authentification réseau développé par le Massachusetts Institute of Technology (MIT). 
* Kerberos a été conçu pour protéger les informations sensibles des utilisateurs et garantir qu'elles ne tombent pas entre de mauvaises mains.

### 2. C'est quoi le but et l'intérêt du protocole

Le but principal de Kerberos est de fournir une **authentification forte** dans un environnement réseau, c'est-à-dire de vérifier l'identité d'un utilisateur ou d'un service sur un réseau de manière sécurisée.

L'intérêt de Kerberos réside dans ses caractéristiques principales :

- **Sécurité** : Il utilise un mécanisme de billets (tickets) pour prouver l'identité sans avoir à transmettre le mot de passe réel sur le réseau, réduisant ainsi la probabilité d'interception.
    
- **Fonctionnement basé sur des billets** : Une fois qu'un utilisateur s'est authentifié auprès du service d'authentification Kerberos, il reçoit un "ticket-granting ticket (TGT)". Ce TGT peut ensuite être utilisé pour obtenir des billets pour d'autres services sans nécessiter de nouvelles authentifications pendant une période donnée.
    
- **Confidentialité et intégrité** : Les données échangées sont chiffrées pour garantir la confidentialité et l'intégrité des informations.

### 3. Quels sont les cas courants d'utilisation du protocole

- **Systèmes d'exploitation** : De nombreux systèmes d'exploitation, tels que Windows, Linux et macOS, intègrent Kerberos pour l'authentification des utilisateurs et des services.
    
- **Applications d'entreprise** : Des applications telles que les bases de données, les serveurs de messagerie et d'autres applications critiques utilisent Kerberos pour authentifier les utilisateurs avant de leur permettre d'accéder à des ressources sensibles.
    
- **Réseaux d'entreprise** : Dans les grands réseaux d'entreprise, l'authentification est essentielle pour garantir que seuls les utilisateurs autorisés ont accès aux ressources. Kerberos est souvent utilisé dans ces scénarios pour sa robustesse et son efficacité.
    
- **Fédérations d'identités et SSO (Single Sign-On)** : Kerberos peut être utilisé comme mécanisme d'authentification sous-jacent pour les solutions de SSO, permettant aux utilisateurs de s'authentifier une seule fois pour accéder à plusieurs applications et services.
    
- **Protocoles et solutions de sécurité supplémentaires** : D'autres protocoles et solutions, tels que LDAP, peuvent être configurés pour utiliser Kerberos comme mécanisme d'authentification.

### 4. Quels sont les éléments du protocole

Pour comprendre le fonctionnement de Kerberos, il est essentiel de connaître ses éléments clés:

- **Centre de distribution des clés (KDC)** : Comme mentionné précédemment, le KDC est le tiers de confiance au cœur de Kerberos. Il est composé de deux parties principales :

  - **Serveur d'authentification (AS)** : Il fournit des "Ticket Granting Tickets (TGT)" aux clients lorsqu'ils s'authentifient initialement.
  
  - **Serveur d'accès aux tickets (TGS)** : Il fournit des billets pour accéder à des services spécifiques après avoir reçu un TGT valide.
  
- **Tickets (Billets)** : Ce sont des messages chiffrés contenant différentes informations telles que l'identité du client, l'identité du service, la durée de validité du ticket et une clé de session. Les tickets sont utilisés pour prouver l'identité sans avoir à retransmettre le mot de passe.

- **Clé de session** : Une clé temporaire générée par le KDC et utilisée pour chiffrer la communication entre le client et le service pendant une session.

### 6. Quels sont les versions et les caractéristiques

- **Kerberos V4** : C'est la première version largement adoptée de Kerberos. Elle offre des services d'authentification de base, mais présente des limitations en termes de sécurité et de fonctionnalité.

- **Kerberos V5** : C'est la version actuelle et la plus utilisée de Kerberos. Elle a été conçue pour surmonter les limitations de la V4. Voici quelques-unes de ses caractéristiques :

  - **Améliorations en matière de sécurité** : Elle offre une meilleure résistance aux attaques et supporte une variété d'algorithmes cryptographiques.
  
  - **Interopérabilité** : Elle est conçue pour fonctionner avec différents systèmes et applications.
  
  - **Support des délégations** : Elle permet aux services de s'authentifier en tant qu'utilisateurs pour accéder à d'autres services, facilitant ainsi les scénarios complexes tels que les services web.
  
  - **Passage de tickets entre différents domaines Kerberos** : Il s'agit d'une caractéristique essentielle pour les grandes organisations avec de nombreux domaines.

### 7. Comment fonctionne Kerberos

* Kerberos s'appuie sur un tiers de confiance appelé Centre de distribution de clés (KDC). Le KDC maintient une base de données de clés secrètes pour chaque utilisateur et service du réseau. Le protocole utilise la cryptographie à clé symétrique, ce qui signifie que le client et le serveur connaissent la même clé de cryptage partagée.

* L'objectif principal de Kerberos est de prouver l'identité du client et du serveur l'un à l'autre afin qu'ils puissent échanger des informations en toute sécurité. Pour ce faire, le protocole utilise des tickets - des messages cryptés contenant des informations sur l'identité du client, l'identité du serveur et une clé de session partagée.

Voici un résumé de haut niveau du processus d'authentification Kerberos :

1. Le client demande un ticket au KDC en fournissant son nom d'utilisateur.
2. Le KDC génère un ticket, le crypte à l'aide de la clé secrète du client et le renvoie au client.
3. Le client déchiffre le ticket et obtient une clé de session qu'il utilisera pour communiquer en toute sécurité avec le serveur.
4. Pour accéder à un service spécifique, le client demande un ticket de service au KDC. La demande comprend son ticket et l'identifiant du serveur cible.
5. Le KDC génère un ticket de service, le chiffre à l'aide de la clé secrète du serveur et le renvoie au client.
6. Le client envoie le ticket de service au serveur accompagné d'un message chiffré à l'aide de la clé de session, afin d'établir son identité.
7. Le serveur déchiffre le ticket de service, extrait la clé de session et l'utilise pour déchiffrer le message du client.

### 9. Quels sont les failles de sécurité du protocole Kerberos?

Bien que Kerberos soit considéré comme un mécanisme d'authentification robuste et sécurisé, aucun système n'est à l'abri des vulnérabilités. Voici quelques-unes des failles et des préoccupations associées à Kerberos:

1. **Attaques par force brute** : Bien que Kerberos utilise le chiffrement pour sécuriser les informations, il reste vulnérable aux attaques par force brute, en particulier si des mots de passe faibles sont employés. Les attaquants peuvent tenter de déchiffrer les tickets en essayant un grand nombre de combinaisons jusqu'à trouver le bon mot de passe.

2. **Vulnérabilité des billets à longue durée** : Le Ticket Granting Ticket (TGT) est généralement valable pendant 10 heures par défaut. Si un attaquant parvient à voler un TGT, il pourrait potentiellement l'utiliser pour obtenir des tickets de service pendant la durée de vie du TGT.

3. **Attaques de l'homme du milieu (MITM)** : Si un attaquant parvient à intercepter la communication entre le client et le serveur, il pourrait essayer de s'insérer comme un intermédiaire et manipuler les messages échangés.

4. **Compromission du KDC** : Le KDC est le cœur de l'infrastructure Kerberos. Si un attaquant parvient à compromettre le KDC, il pourrait potentiellement accéder à toutes les clés secrètes et compromettre l'ensemble du système.

5. **Attaques de renouvellement de ticket** : Ces attaques impliquent la capture d'un ticket Kerberos et son utilisation après l'expiration du ticket pour demander un nouveau ticket.

6. **Vulnérabilité à l'horodatage** : Comme Kerberos repose sur l'horodatage pour la validité des tickets, si un attaquant parvient à manipuler l'horloge d'un système, il pourrait essayer d'abuser du mécanisme d'authentification.

7. **Poisoning du cache de tickets** : Si un attaquant parvient à accéder localement à une machine, il pourrait essayer de remplacer le cache de tickets Kerberos avec des tickets malveillants, compromettant ainsi les sessions futures.
