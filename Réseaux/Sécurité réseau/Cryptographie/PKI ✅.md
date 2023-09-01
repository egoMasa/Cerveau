# Guide PKI (Infrastructure à Clés Publiques)**

---

# **1. C'est quoi une PKI:**

La PKI, ou Infrastructure à Clés Publiques, est un ensemble de rôles, de politiques, de logiciels, d'équipements et de procédures de travail qui permettent de créer, gérer, distribuer, utiliser, stocker et révoquer des certificats numériques. Elle repose sur un système de cryptographie asymétrique, où deux clés sont utilisées: une clé publique (connue de tous) et une clé privée (connue uniquement de son détenteur).

**Comparaison**: Imaginez une boîte aux lettres publique (la clé publique) où n'importe qui peut déposer un message, mais seule une personne ayant la clé unique (la clé privée) peut ouvrir cette boîte et lire le message.

# **2. C'est quoi le but et l'intérêt d'une PKI:**

**But**: Le but principal de la PKI est de faciliter l'utilisation sécurisée de technologies et de services qui reposent sur la cryptographie, tels que les certificats numériques, le chiffrement, la signature électronique et l'authentification.

**Intérêt**:
- **Confidentialité**: Seuls les détenteurs des clés appropriées peuvent déchiffrer un message.
- **Intégrité**: On peut vérifier si un message a été modifié en transit.
- **Authentification**: On peut s'assurer de l'identité de la personne ou de l'entité qui a envoyé un message.
- **Non-répudiation**: L'expéditeur ne peut nier avoir envoyé un message.

**Comparaison**: C'est comme avoir un cachet de cire avec un sceau unique sur une lettre. Si le sceau est intact, vous savez que la lettre n'a pas été ouverte (intégrité), et vous reconnaissez le sceau de l'expéditeur (authentification).

# **3. Quels sont les cas courants d'utilisation d'une PKI:**

- **Authentification SSL/TLS**: Lorsque vous visitez un site Web sécurisé (HTTPS), la PKI permet d'authentifier le site Web et d'établir une connexion sécurisée.
  
- **Signature électronique**: Pour garantir qu'un document numérique provient d'une source spécifique et n'a pas été modifié.

- **Chiffrement des emails**: Pour envoyer des e-mails sécurisés où seuls l'expéditeur et le destinataire peuvent lire le contenu.

- **Authentification de VPN**: Lors de l'établissement d'une connexion VPN, la PKI peut être utilisée pour authentifier les utilisateurs et les serveurs.

- **Émission de cartes d'identité électroniques**: Dans certains pays, les cartes d'identité comportent des certificats numériques pour l'authentification électronique.

**Comparaison**: C'est comme utiliser différents types de verrous et de clés pour différentes portes et coffres. Certains sont pour les portes principales (sites Web SSL), d'autres pour des coffres sécurisés (emails chiffrés), et d'autres encore pour des pièces spécifiques (VPN).

# **4. Quels sont les éléments de la PKI:**

1. **Certificat numérique**: C'est un fichier électronique servant d'identité numérique. Il contient notamment une clé publique et est signé par une autorité de certification (CA) pour confirmer son authenticité.

2. **Autorité de Certification (CA)**: C'est l'entité de confiance responsable de l'émission, de la gestion, de la distribution, du renouvellement et de la révocation des certificats numériques.

3. **Autorité d'Enregistrement (RA)**: C'est l'intermédiaire entre la CA et les utilisateurs finaux. Elle vérifie les informations fournies par l'utilisateur avant que la CA n'émette un certificat.

4. **Base de révocation des certificats (CRL)**: Il s'agit d'une liste de certificats qui ont été révoqués avant leur date d'expiration.

5. **Clé privée et publique**: La paire de clés utilisée dans la cryptographie asymétrique. La clé publique est partagée avec tout le monde, tandis que la clé privée reste secrète.

6. **Point de distribution de certificats (CDP)**: Emplacement (souvent un URL) où les CRL peuvent être récupérées.

7. **Infrastructure logicielle et matérielle**: Serveurs, modules de sécurité matérielle (HSM), stockages, etc., utilisés pour gérer et stocker les éléments de la PKI.

**Comparaison**: Imaginez la PKI comme une mairie. La CA est comme le bureau d'état civil émettant des actes de naissance (certificats). L'RA est le guichet où vous fournissez vos informations initiales. La CRL est comme une liste de documents invalidés ou retirés.

# **5. Quels sont les versions et les caractéristiques de la PKI:**

En réalité, la notion de "versions" n'est pas strictement applicable à la PKI elle-même. Cependant, les protocoles et normes associés à la PKI, comme X.509 (standard pour les certificats), peuvent avoir différentes versions. 

**X.509** est le standard le plus utilisé pour définir la structure des certificats numériques:
- **v1**: La version initiale.
- **v2**: Ajoute des identifiants uniques pour distinguer les certificats.
- **v3**: Introduit les extensions qui permettent aux utilisateurs d'ajouter des informations supplémentaires aux certificats, comme les restrictions d'utilisation.

**Caractéristiques**:
- **Inter-opérabilité**: La PKI est conçue pour fonctionner sur différentes plateformes et systèmes.
- **Scalabilité**: Elle peut être déployée à petite ou grande échelle, de quelques utilisateurs à plusieurs millions.
- **Gestion du cycle de vie**: La PKI prend en charge toutes les étapes du cycle de vie d'un certificat, de sa création à sa révocation.
- **Sécurité**: Elle utilise des méthodes de cryptographie robustes pour garantir la sécurité des communications.

**Comparaison**: Pensez à la PKI comme à un système d'identité numérique. Tout comme votre passeport a différentes versions et mises à jour, les standards tels que X.509 ont été mis à jour pour répondre aux besoins changeants de la sécurité numérique.

# Scénario d'illustration

**Scénario**: Alice, une employée d'une grande entreprise, doit accéder à distance à des ressources sécurisées de l'entreprise. Elle utilisera un VPN sécurisé par un certificat pour s'authentifier. L'entreprise utilise une PKI pour gérer ces certificats.

**Étapes et échanges avec la PKI**:

1. **Demande de certificat**:
    - **Alice** contacte l'**Autorité d'Enregistrement (RA)** pour demander un certificat numérique.
    - Alice fournit des informations d'identité et, dans certains cas, une paire de clés (clé publique et privée). Souvent, la clé privée reste avec Alice et n'est jamais partagée.

2. **Vérification d'identité**:
    - L'**RA** vérifie les informations d'Alice pour s'assurer qu'elle est bien qui elle prétend être. Cela peut impliquer des vérifications manuelles ou automatisées.
  
3. **Émission de certificat**:
    - Une fois l'identité d'Alice vérifiée, l'**RA** transmet la demande à l'**Autorité de Certification (CA)**.
    - La **CA** génère un certificat pour Alice. Ce certificat inclut la clé publique d'Alice, ses informations d'identité, la signature de la CA, et d'autres détails pertinents.
    - Alice reçoit son certificat numérique et le stocke dans un endroit sécurisé.

4. **Utilisation du certificat pour l'authentification**:
    - Alice tente de se connecter au VPN de l'entreprise.
    - Le serveur VPN demande à Alice son certificat pour prouver son identité.
    - Alice envoie son certificat au serveur VPN.
    - Le serveur VPN vérifie le certificat d'Alice. Il utilise la clé publique de la CA (qu'il fait déjà confiance et possède) pour vérifier la signature sur le certificat d'Alice.
    - Si la signature est valide, cela prouve que le certificat d'Alice a bien été émis par la CA de confiance, et donc Alice est authentifiée.

5. **Révocation du certificat** (si nécessaire):
    - Si, pour une raison quelconque, le certificat d'Alice doit être invalidé (par exemple, si elle perd son dispositif ou si elle quitte l'entreprise), l'entreprise ajoutera le certificat d'Alice à la **Liste de Révocation de Certificats (CRL)**.
    - À l'avenir, si Alice tente d'utiliser son certificat, le serveur VPN vérifiera la CRL et verra que le certificat d'Alice a été révoqué. Elle ne sera donc pas authentifiée.

**Comparaison**: Imaginez la PKI comme un système de délivrance de passeports. L'**RA** est le guichet où vous postulez pour un passeport. La **CA** est l'organisme gouvernemental qui vérifie et approuve votre demande, puis émet le passeport. Lorsque vous voyagez (vous connecter au VPN), les douaniers (serveur VPN) vérifient votre passeport pour s'assurer qu'il est valide et a été délivré par une autorité reconnue (signature de la CA).

# 9. Quels sont les failles de sécurité d'une PKI utilisable pour un attaquant

La PKI, bien que considérée comme robuste lorsqu'elle est correctement mise en œuvre, présente néanmoins des vulnérabilités que les attaquants peuvent exploiter. Voici quelques-unes des failles et vulnérabilités les plus courantes liées à la PKI :

1. **Compromission de clé privée**:
   - Si un attaquant parvient à obtenir une clé privée, il peut usurper l'identité du titulaire du certificat.
   - **Comparaison** : C'est comme voler la carte d'identité d'une personne et la présenter comme la vôtre.
  
2. **CA de confiance non fiable** :
   - Si une Autorité de Certification n'est pas digne de confiance ou a été compromise, elle peut émettre des certificats frauduleux.
   - **Comparaison** : C'est comme si une entreprise de fabrication de passeports était corrompue et émettait de faux passeports.

3. **Révocation de certificat inefficace**:
   - Si la Liste de Révocation de Certificats (CRL) ou le protocole OCSP (Online Certificate Status Protocol) ne fonctionne pas correctement, des certificats révoqués pourraient toujours être utilisés.
   - **Comparaison** : C'est comme utiliser un passeport périmé dans un aéroport qui ne vérifie pas les dates d'expiration.

4. **Vulnérabilités logicielles**:
   - Les logiciels qui implémentent la PKI peuvent avoir des vulnérabilités, permettant à un attaquant d'exploiter la PKI.
   - **Comparaison** : C'est comme avoir une serrure défectueuse sur une porte sécurisée.

5. **Attaques de l'homme du milieu (MitM)** :
   - Si un attaquant peut intercepter et modifier les communications entre deux parties utilisant des certificats, il peut manipuler ou usurper l'identité d'une des parties.
   - **Comparaison** : C'est comme si quelqu'un interceptait votre courrier, le lisait, puis l'envoyait comme si rien ne s'était passé.

6. **Expiration des certificats** :
   - Les certificats ont une durée de vie, et leur expiration peut interrompre des services ou permettre des attaques si des certificats périmés sont encore acceptés.
   - **Comparaison** : C'est comme utiliser un billet de train périmé qui n'a pas été vérifié par le contrôleur.

7. **Attaques d'anniversaire et de collision** :
   - Ces attaques exploitent les faiblesses des fonctions de hachage utilisées dans la PKI. Si un attaquant peut créer un autre certificat ayant la même valeur de hachage qu'un certificat valide, il peut potentiellement usurper des identités.
   - **Comparaison** : C'est comme si deux personnes différentes avaient le même numéro de sécurité sociale.

Sécuriser la PKI nécessite une mise en œuvre soignée, des mises à jour régulières, une surveillance continue, et des pratiques rigoureuses en matière de gestion des clés.