# Sommaire 
- [ ] Principe de la cryptographie
- [ ]  Notion de cléfs, passphrase
- [ ] Chiffrement symétrique : AES
	- [ ] Processus de chiffrement et de déchiffrement
	- [ ] Processus de controle d'intégrité
	- [ ] Processus d'authentification
- [ ] Chiffrement asymétrique : RSA
	- [ ] Processus de chiffrement et de déchiffrement
	- [ ] Processus de controle d'intégrité
	- [ ] Processus d'authentification
- [ ] Hashage : SHA
- [ ] Empreinte et signature et certificat
- [ ] Confidentialité, Intégrité et Authentification
- [ ] PKI

# 1) Principe de la cryptographie
## Définition, histoire, et importance
- **Définition** : La cryptographie est l'art et la science de sécuriser les communications, permettant à deux parties de communiquer de manière sécurisée en présence d'adversaires. Elle utilise des techniques mathématiques pour chiffrer et déchiffrer l'information.
- **Histoire** : Les origines de la cryptographie remontent à l'antiquité, avec des exemples comme le chiffre de César utilisé par les Romains. Au fil des siècles, la cryptographie s'est développée, passant de méthodes simples à des algorithmes complexes rendus possibles par l'avènement de l'informatique.
- **Importance** : Aujourd'hui, la cryptographie est essentielle pour sécuriser les transactions en ligne, protéger les données stockées et assurer la confidentialité des communications électroniques. Elle est au cœur des technologies modernes comme le commerce électronique, les réseaux sécurisés et la protection de la vie privée.
## Objectifs : confidentialité, intégrité, authentification, et non-répudiation
- **Confidentialité** : Assure que les informations ne sont accessibles qu'aux parties autorisées. Le chiffrement joue un rôle clé en transformant les données en un format illisible sans la clé de déchiffrement appropriée.
- **Intégrité** : Garantit que les informations n'ont pas été altérées pendant le transfert ou le stockage. Les fonctions de hachage et les codes de vérification d'intégrité (MAC) sont couramment utilisés pour vérifier l'intégrité des données.
- **Authentification** : Confirme l'identité des parties impliquées dans une communication. Cela peut être réalisé par des mots de passe, des clés numériques, ou des certificats.
- **Non-répudiation** : Empêche une partie de nier la véracité d'un message qu'elle a envoyé ou reçu. Les signatures numériques sont un moyen courant d'assurer la non-répudiation.
## Terminologie de base : cryptographie, cryptanalyse, cryptologie
- **Cryptographie** : Comme mentionné, c'est l'étude des techniques de sécurisation de la communication et de l'information. Elle englobe le chiffrement, le déchiffrement, et les méthodes de sécurisation des données.
- **Cryptanalyse** : C'est l'étude des méthodes pour casser ou analyser les systèmes cryptographiques dans le but de découvrir des failles ou de récupérer les informations cachées sans avoir nécessairement accès à la clé secrète.
- **Cryptologie** : C'est le terme général qui englobe à la fois la cryptographie et la cryptanalyse. La cryptologie est donc l'étude globale des codes et des chiffres, couvrant la création, l'analyse et la brisure des systèmes cryptographiques.

# 2) Notion de clés, passphrase
## Clés cryptographiques : définition, types (publique, privée), et utilisation
- **Définition** : Une clé cryptographique est une information utilisée par un algorithme de chiffrement ou de déchiffrement pour convertir le texte clair en texte chiffré ou inversement. Sa complexité et sa longueur déterminent la facilité avec laquelle un adversaire pourrait craquer le chiffrement.
- **Types** :
    - **Clé publique** : Dans le chiffrement asymétrique, la clé publique est distribuée librement et utilisée pour chiffrer les messages. Toutefois, seul le détenteur de la clé privée correspondante peut les déchiffrer.
    - **Clé privée** : Elle reste secrète et est utilisée pour déchiffrer les messages chiffrés avec la clé publique correspondante ou pour signer numériquement les messages, garantissant ainsi l'authenticité et l'intégrité.
- **Utilisation** : Les clés publiques et privées sont utilisées pour sécuriser les communications, authentifier les parties impliquées, et garantir l'intégrité des données.

## Passphrases : importance, bonnes pratiques pour la création de passphrases sécurisées
- **Importance** : Les passphrases sont souvent utilisées pour protéger l'accès aux clés privées ou comme un moyen d'authentification. Une passphrase forte augmente considérablement la sécurité d'une clé cryptographique.
- **Bonnes pratiques** :
    - Utiliser des phrases longues et complexes, mélangeant caractères alphanumériques, symboles, et majuscules/minuscules.
    - Éviter les mots et phrases courantes, prévisibles ou facilement devinables.
    - Considérer l'utilisation de gestionnaires de mots de passe pour générer et stocker des passphrases complexes.

## Gestion des clés : stockage, distribution, et renouvellement
- **Stockage** : Les clés cryptographiques doivent être stockées en toute sécurité, souvent dans des modules matériels sécurisés (HSM) ou des coffres-forts numériques, pour prévenir l'accès non autorisé ou la fuite d'informations.
- **Distribution** : La distribution des clés, notamment des clés publiques, doit être effectuée de manière sécurisée pour éviter les interceptions. Des protocoles de distribution de clés sécurisés doivent être utilisés.
- **Renouvellement** : Les clés doivent être régulièrement renouvelées pour limiter les fenêtres d'opportunité pour les attaquants. Les politiques de renouvellement dépendent de la sensibilité des données protégées et de l'environnement opérationnel.

# 3) Chiffrement symétrique : AES
## Introduction à AES : historique, pourquoi AES a été choisi comme standard
- **Historique** : AES a été développé pour remplacer l'ancien standard de chiffrement, le Data Encryption Standard (DES), qui était devenu vulnérable aux attaques par force brute en raison de sa clé relativement courte. AES a été officiellement publié par l'Institut National des Standards et de la Technologie (NIST) des États-Unis en 2001, après un processus de sélection rigoureux.
- **Pourquoi AES a été choisi** : AES offre un niveau de sécurité élevé, est efficace dans de nombreuses plates-formes hardware et software, y compris celles avec des ressources limitées. Il supporte plusieurs longueurs de clé (128, 192 et 256 bits), ce qui le rend adaptable à différents niveaux de sécurité et performances.
## Processus de chiffrement et de déchiffrement : fonctionnement, modes d'opération (CBC, GCM, etc.)
- **Fonctionnement** : AES chiffre les données en blocs de 128 bits en utilisant des clés de 128, 192 ou 256 bits à travers plusieurs tours de transformation. Le processus exact dépend de la longueur de la clé, mais chaque tour inclut des étapes de substitution, de permutation, de mixage des colonnes et d'ajout de clé.
- **Modes d'opération** :
    - **CBC (Cipher Block Chaining)** : Chaque bloc de texte clair est XOR avec le bloc chiffré précédent avant d'être chiffré. Cela lie chaque bloc au précédent pour une sécurité accrue.
    - **GCM (Galois/Counter Mode)** : Un mode qui fournit à la fois le chiffrement et l'authentification des messages, offrant ainsi une protection contre les altérations des données chiffrées.
## Processus de contrôle d'intégrité : importance, comment AES contribue à l'intégrité des données
- **Importance** : Le contrôle d'intégrité garantit que les données n'ont pas été altérées, intentionnellement ou accidentellement, pendant le stockage ou le transfert.
- **Contribution d'AES** : Bien qu'AES en lui-même ne fournisse pas directement un contrôle d'intégrité, des modes comme GCM intègrent le chiffrement et la vérification de l'intégrité dans un seul processus. Cela permet de détecter toute modification des données chiffrées.
## Processus d'authentification : utilisation d'AES dans les protocoles d'authentification
- **Utilisation d'AES** : Dans le contexte de l'authentification, AES peut être utilisé pour sécuriser les échanges d'informations d'authentification entre un client et un serveur. Par exemple, dans les protocoles de tunneling sécurisé, AES peut chiffrer les données d'authentification, garantissant que seules les parties authentifiées peuvent accéder et déchiffrer ces informations.
- **Protocoles d'authentification** : AES est souvent intégré dans des protocoles d'authentification plus larges, offrant une couche de sécurité supplémentaire. Par exemple, dans les systèmes de VPN ou les connexions Wi-Fi sécurisées (WPA2, WPA3), AES est utilisé pour protéger les informations d'identification des utilisateurs ainsi que les données échangées sur le réseau.

# 4) Chiffrement asymétrique : RSA
- Introduction à RSA : principe, utilisation, avantages par rapport au chiffrement symétrique.
- **Processus de chiffrement et de déchiffrement** : fonctionnement, utilisation des clés publique et privée.
- **Processus de contrôle d'intégrité** et **d'authentification** : signature numérique, son rôle dans l'authentification et le contrôle d'intégrité.
# 5) Hashage : SHA
Le hashage est une technique fondamentale en cryptographie, utilisée pour sécuriser les données et vérifier leur intégrité. La famille de fonctions de hachage sécurisé SHA (Secure Hash Algorithm) est parmi les plus utilisées et reconnues dans ce domaine.
## Présentation du hashage : définition, utilité
- **Définition** : Le hashage transforme une quantité arbitraire de données en une sortie de taille fixe (appelée hash ou empreinte numérique) à travers une fonction de hachage. Cette transformation est unidirectionnelle, ce qui signifie qu'il est pratiquement impossible de retrouver les données d'origine à partir de l'empreinte.
- **Utilité** : Les fonctions de hachage sont utilisées pour de nombreuses applications, y compris la vérification de l'intégrité des données, l'authentification des messages, et le stockage sécurisé des mots de passe. En générant une empreinte numérique des données, on peut facilement détecter toute altération de ces dernières.

## Introduction à SHA : versions (SHA-1, SHA-2, SHA-3), applications
- **SHA-1** : Bien qu'historiquement largement utilisé, SHA-1 est maintenant considéré comme vulnérable aux attaques par collision. Cela signifie que deux ensembles de données différents peuvent produire le même hash, compromettant l'intégrité des données.
- **SHA-2** : Inclut plusieurs variantes (SHA-224, SHA-256, SHA-384, SHA-512) offrant une meilleure sécurité que SHA-1. SHA-2 est largement utilisé dans des protocoles de sécurité comme SSL/TLS et dans des standards de signature numérique.
- **SHA-3** : Le plus récent membre de la famille, introduit pour répondre aux inquiétudes concernant les techniques d'attaque potentielles qui pourraient compromettre SHA-2. SHA-3 est basé sur une structure différente (Keccak) et offre une alternative robuste.
## Propriétés des fonctions de hachage : résistance aux collisions, effet avalanche
- **Résistance aux collisions** : Une fonction de hachage sécurisée doit garantir qu'il est extrêmement difficile de trouver deux ensembles de données différents produisant le même hash. Cette propriété est cruciale pour prévenir les attaques et assurer l'unicité des empreintes numériques des données.
- **Effet avalanche** : Une petite modification dans les données d'entrée doit entraîner un changement important et imprévisible dans le hash de sortie. Cette propriété assure qu'il est impossible de déduire les données d'entrée ou de prédire le hash de sortie, renforçant ainsi la sécurité.

# 6) Empreinte et signature et certificat
Ces concepts jouent un rôle central dans la sécurisation des échanges numériques, en assurant l'intégrité des données, l'authentification des parties impliquées, et la confiance dans les communications électroniques.
## Empreintes numériques : définition, utilisation
- **Définition** : Une empreinte numérique est le résultat d'une fonction de hachage appliquée à un ensemble de données ou à un document. Elle produit une valeur unique de taille fixe qui résume l'information originale.
- **Utilisation** : Les empreintes numériques sont utilisées pour vérifier l'intégrité des données. En comparant l'empreinte d'un ensemble de données à une empreinte précédemment calculée, on peut détecter si des modifications ont été apportées aux données originales. Cette technique est couramment employée dans la vérification de l'intégrité des téléchargements de logiciels et dans les systèmes de contrôle de version.

## Signatures numériques : fonctionnement, importance dans la cryptographie
- **Fonctionnement** : Une signature numérique est créée en appliquant une fonction de hachage aux données d'un document, puis en chiffrant l'empreinte résultante avec la clé privée de l'émetteur. Pour vérifier la signature, le destinataire déchiffre l'empreinte avec la clé publique de l'émetteur et la compare à l'empreinte du document reçu.
- **Importance dans la cryptographie** : Les signatures numériques fournissent une preuve irréfutable de l'origine et de l'intégrité des données, offrant ainsi une authentification et une non-répudiation. Elles sont essentielles dans les transactions électroniques, les documents légaux numériques, et les systèmes de gestion de la confiance.

## Certificats numériques : rôle, structure, et comment ils facilitent la gestion des clés publiques
- **Rôle** : Un certificat numérique, souvent émis par une autorité de certification (CA), atteste de l'identité du détenteur de la clé publique. Il lie une clé publique à l'identité d'une personne, d'une entreprise ou d'un dispositif, établissant ainsi un niveau de confiance dans les échanges électroniques.
- **Structure** : Un certificat numérique contient l'identité du propriétaire, la clé publique, l'identité de l'autorité de certification qui l'émet, une période de validité, et une signature numérique de l'autorité de certification. La structure la plus commune est basée sur le standard X.509.
- **Gestion des clés publiques** : Les certificats facilitent la gestion des clés publiques en offrant un mécanisme fiable pour distribuer, authentifier et révoquer les clés publiques. Les utilisateurs et les systèmes peuvent se fier à un certificat pour s'assurer que la clé publique appartient bien à l'entité revendiquée, simplifiant ainsi la mise en place de communications sécurisées et authentifiées.

# 7) Confidentialité, Intégrité et Authentification
Ces trois principes forment le pilier de la sécurité des informations, chacun jouant un rôle crucial dans la protection des données et la sécurisation des communications dans un environnement numérique.
## Définition et importance de chaque concept dans la sécurité des informations
- **Confidentialité** : La confidentialité assure que les informations sont accessibles uniquement aux personnes autorisées. Elle protège les données contre les accès non autorisés, garantissant que seuls les destinataires prévus peuvent les voir ou les utiliser. La confidentialité est essentielle pour protéger la vie privée des individus et la propriété intellectuelle des entreprises.
- **Intégrité** : L'intégrité des données garantit que les informations sont exactes et complètes, et qu'elles n'ont pas été modifiées de manière non autorisée. Cela inclut la protection contre les altérations, les suppressions ou les ajouts frauduleux. L'intégrité est cruciale pour assurer la fiabilité et la confiance dans les données échangées ou stockées.
- **Authentification** : L'authentification confirme l'identité des parties impliquées dans une communication ou un accès aux données. Elle permet de vérifier que les individus ou les systèmes sont bien ceux qu'ils prétendent être, empêchant les accès non autorisés et les usurpations d'identité.
## Méthodes et protocoles garantissant ces principes dans la cryptographie moderne
- **Pour la Confidentialité** :
    - **Chiffrement** : L'utilisation de techniques de chiffrement telles que AES (Advanced Encryption Standard) pour les communications symétriques et RSA ou ECC (Elliptic Curve Cryptography) pour les communications asymétriques. Les VPNs (Virtual Private Networks) et les protocoles comme SSL/TLS pour les communications sécurisées sur Internet en sont des exemples.
- **Pour l'Intégrité** :
    - **Fonctions de hachage cryptographiques** : L'emploi de SHA (Secure Hash Algorithm) et d'autres fonctions de hachage pour créer une empreinte numérique des données, permettant de vérifier leur intégrité lors de la transmission ou du stockage.
    - **Codes de vérification de l'intégrité des messages (MAC)** et **signatures numériques** : Ces techniques fournissent une assurance que les données n'ont pas été modifiées depuis leur création ou envoi par la source légitime.
- **Pour l'Authentification** :
    - **Protocoles d'authentification** : Des mécanismes comme les échanges de clés Diffie-Hellman pour l'authentification mutuelle dans les communications, ou l'utilisation de systèmes basés sur des certificats numériques et PKI (Public Key Infrastructure) pour authentifier les identités.
    - **Authentification à deux facteurs (2FA)** et **authentification multifacteur (MFA)** : Ces méthodes combinent plusieurs types de preuves d'identité (ce que l'utilisateur sait, possède, ou est) pour renforcer la sécurité de l'authentification.

# 8) PKI (Public Key Infrastructure)
La Public Key Infrastructure (PKI) est un cadre essentiel pour la gestion des clés cryptographiques et des certificats numériques dans un environnement sécurisé. Elle joue un rôle central dans l'établissement et la maintenance de la sécurité des informations numériques.
## Définition et composants d'une PKI
- **Définition** : Une PKI est un ensemble de rôles, de politiques, de logiciels, d'équipements et de procédures nécessaires pour créer, gérer, distribuer, utiliser, stocker et révoquer les certificats numériques. Elle permet d'établir et de maintenir un niveau de confiance dans le monde numérique.
- **Composants d'une PKI** :
    - **CA (Certificate Authority)** : L'autorité de certification est l'entité responsable de l'émission et de la gestion des certificats numériques. Elle atteste de l'identité du détenteur du certificat et de sa clé publique associée.
    - **RA (Registration Authority)** : L'autorité d'enregistrement vérifie l'identité des entités demandant un certificat avant que le CA n'émette le certificat. La RA sert de tampon de vérification pour le CA.
    - **Révocation de certificat** : Les certificats peuvent être révoqués avant leur expiration si la clé privée est compromise ou si l'information dans le certificat n'est plus valide. Les CAs publient des listes de révocation de certificats (CRL) ou utilisent le protocole OCSP (Online Certificate Status Protocol) pour fournir cette information.
## Fonctionnement d'une PKI
- **Émission de certificats** : Après vérification par la RA, le CA émet un certificat numérique à l'entité demandant. Ce certificat lie une clé publique à l'identité de son détenteur et est signé numériquement par le CA.
- **Chaîne de confiance** : Les certificats peuvent être émis par des CAs intermédiaires qui sont eux-mêmes certifiés par un CA racine de confiance. Cette hiérarchie crée une chaîne de confiance qui permet aux utilisateurs de vérifier l'authenticité des certificats numériques.
## Applications de la PKI
- **Sécurisation des communications** : La PKI est fondamentale pour sécuriser les communications sur des réseaux non sécurisés. Elle est utilisée dans les protocoles SSL/TLS pour sécuriser les connexions Internet, garantissant la confidentialité et l'intégrité des données échangées.
- **Authentification des utilisateurs et des dispositifs** : Les certificats numériques permettent l'authentification forte des utilisateurs et des dispositifs dans divers systèmes et applications, y compris les réseaux d'entreprise, les services en ligne et les communications sécurisées.
- **Signature numérique de documents** : La PKI permet également la signature numérique de documents, assurant l'authenticité, l'intégrité et la non-répudiation des documents électroniques.