# Guide sur TACACS+

# 1. C'est quoi le protocole?

**TACACS+** est un protocole d'authentification développé par Cisco Systems. Il s'agit d'une évolution du protocole TACACS original. TACACS+ est distinct et ne doit pas être confondu avec RADIUS, un autre protocole d'authentification.

# 2. C'est quoi le but et l'intérêt du protocole?

**But** : TACACS+ a été conçu pour fournir un service centralisé d'authentification, d'autorisation et de comptabilité (AAA) pour les réseaux.

**Intérêt** : 
- **Authentification** : Il vérifie qui a le droit d'accéder au réseau.
- **Autorisation** : Une fois authentifié, il détermine ce qu'un utilisateur est autorisé à faire. Par exemple, quelles commandes il peut exécuter sur un routeur.
- **Comptabilité** : Il enregistre ce que l'utilisateur fait, par exemple, les commandes exécutées ou les heures de connexion et de déconnexion.
  
Autres avantages de TACACS+:
- **Sécurité** : Les échanges entre le client (généralement un équipement réseau comme un commutateur ou un routeur) et le serveur TACACS+ sont chiffrés.
- **Flexibilité** : Il offre un contrôle granulaire des utilisateurs. Vous pouvez attribuer des droits à des utilisateurs ou des groupes spécifiques.
- **Évolutivité** : Convient aux grands réseaux où de nombreux équipements nécessitent un contrôle d'accès centralisé.

# 3. Quels sont les cas courants d'utilisation du protocole?

TACACS+ est couramment utilisé dans des scénarios où un accès sécurisé et centralisé à des équipements réseau est essentiel. Voici quelques cas courants d'utilisation :

1. **Gestion des équipements réseau** : Dans les grands réseaux, il peut y avoir des centaines voire des milliers d'équipements (routeurs, commutateurs, pare-feu, etc.). Au lieu de gérer les identifiants pour chaque appareil individuellement, TACACS+ permet une gestion centralisée.

2. **ISPs et grandes entreprises** : Les fournisseurs de services Internet peuvent avoir une multitude d'équipements répartis géographiquement. TACACS+ leur permet de gérer efficacement l'accès à ces équipements.

3. **Conformité réglementaire** : Dans certains secteurs, les réglementations exigent une traçabilité de qui a accédé à quel équipement et quand. La fonctionnalité de comptabilité de TACACS+ aide à répondre à ces exigences.

4. **Contrôle granulaire de l'accès** : Dans un environnement où différents administrateurs ont différents niveaux de responsabilité (par exemple, certains peuvent uniquement consulter la configuration, tandis que d'autres peuvent la modifier), TACACS+ peut attribuer des droits d'accès spécifiques en fonction des rôles.

5. **Mise en réseau à distance et VPN** : Lors de l'établissement de connexions VPN, TACACS+ peut être utilisé pour authentifier les utilisateurs avant d'accorder l'accès au réseau interne.

En résumé, TACACS+ est essentiel pour fournir un contrôle d'accès sécurisé et centralisé aux équipements et aux ressources du réseau.

# 4. Quels sont les éléments du protocole TACACS+?

**TACACS+** est un protocole riche qui fonctionne en utilisant une architecture client-serveur. Voici les éléments clés du protocole :

1. **Client TACACS+** : Il s'agit généralement d'un équipement réseau, comme un commutateur, un routeur ou un pare-feu, qui demande une authentification, une autorisation ou une comptabilité pour un utilisateur.

2. **Serveur TACACS+** : C'est l'entité qui répond aux demandes du client. Le serveur contient les bases de données d'utilisateurs et effectue l'authentification, l'autorisation et la comptabilité en fonction des demandes des clients.

3. **Paquets** : TACACS+ utilise différents types de paquets pour communiquer entre le client et le serveur, notamment :
   - **Paquet d'authentification** : Utilisé pour authentifier un utilisateur.
   - **Paquet d'autorisation** : Demande ou fournit des attributs d'autorisation.
   - **Paquet de comptabilité** : Enregistre les activités des utilisateurs.

4. **Session TCP** : TACACS+ utilise TCP (plutôt qu'UDP, utilisé par RADIUS) pour ses communications, ce qui fournit un mécanisme de transport fiable.

5. **Chiffrement** : TACACS+ chiffre l'intégralité du paquet de payload, contrairement à RADIUS qui chiffre seulement le mot de passe. Cela offre une sécurité accrue pour les informations sensibles.

# 5. Quels sont les versions et les caractéristiques?

**TACACS+** est en réalité une évolution des versions précédentes du protocole TACACS. 

1. **TACACS** : Il s'agit de la version initiale du protocole. Il était basé sur UDP et avait des limitations en matière de sécurité et de fonctionnalité.

2. **XTACACS (Extended TACACS)** : Une extension de TACACS qui a introduit des fonctionnalités supplémentaires, notamment l'autorisation et la comptabilité séparées de l'authentification. Cependant, il ne chiffrait pas tout le paquet, laissant certaines informations en clair.

3. **TACACS+** : La dernière version, qui est un protocole distinct des deux précédentes. Contrairement à ses prédécesseurs, TACACS+ offre une sécurité améliorée grâce au chiffrement de l'intégralité du contenu du paquet. Il utilise également TCP au lieu d'UDP, offrant une communication plus fiable.

**Caractéristiques clés de TACACS+** :
- **Chiffrement intégral** : Toute l'information est chiffrée pour une meilleure sécurité.
- **Authentification, autorisation et comptabilité séparées** : Cette séparation permet une plus grande flexibilité et un contrôle granulaire.
- **Architecture extensible** : Le protocole peut être étendu pour répondre à des besoins spécifiques sans rompre la compatibilité avec les versions précédentes.
- **Flexibilité** : Il permet une personnalisation détaillée des droits d'accès des utilisateurs.
- **Interopérabilité** : Bien qu'il ait été développé par Cisco, TACACS+ est utilisé par de nombreux autres fabricants d'équipements réseau.

En somme, TACACS+ est une évolution majeure par rapport à ses versions antérieures, offrant une flexibilité, une sécurité et une fonctionnalité nettement supérieures.

# 6. Comment une communication qui utilise le protocole TACACS+ s'établit

La communication TACACS+ se déroule entre un client (généralement un équipement réseau comme un commutateur ou un routeur) et un serveur TACACS+. Cette communication est basée sur une session TCP. Voici les étapes typiques et les échanges impliqués dans la communication TACACS+:

1. **Établissement de la session TCP**:
   - Le client initie une connexion TCP vers le serveur TACACS+ sur le port 49.
   - Une fois la connexion établie, les paquets TACACS+ peuvent être échangés entre le client et le serveur.

2. **Demande d'authentification**:
   - L'utilisateur essaie de se connecter à l'équipement client (par exemple, via SSH).
   - Le client envoie un paquet d'authentification au serveur TACACS+ contenant les informations d'identification fournies par l'utilisateur.
  
3. **Réponse d'authentification**:
   - Le serveur TACACS+ traite la demande et renvoie soit une réponse d'authentification réussie, soit un défi demandant des informations supplémentaires (par exemple, un mot de passe à usage unique), soit une réponse d'échec.
  
4. **Demande d'autorisation** (si l'authentification est réussie):
   - Après une authentification réussie, le client peut demander une autorisation pour des services ou des commandes spécifiques pour l'utilisateur.
   - Le client envoie un paquet d'autorisation au serveur TACACS+ avec la requête.
  
5. **Réponse d'autorisation**:
   - Le serveur évalue la demande en fonction de sa politique et renvoie une réponse d'autorisation autorisant ou refusant la demande.

6. **Comptabilité**:
   - Une fois les étapes d'authentification et d'autorisation terminées, le client peut envoyer des informations de comptabilité au serveur TACACS+ pour enregistrer les activités de l'utilisateur.
   - Ces informations peuvent inclure le moment de la connexion, la durée, les commandes exécutées, etc.
  
7. **Termination de la session**:
   - Après l'échange de paquets nécessaire (authentification, autorisation, comptabilité), la session TCP est généralement terminée.

8. **Chiffrement**:
   - Il est important de noter que tout le contenu du paquet TACACS+ est chiffré entre le client et le serveur pour assurer la confidentialité et la sécurité des données échangées.
