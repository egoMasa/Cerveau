
# 1) Authentification basique d'un terminal à un point d'accès

## Etape 1 : Authentification
* ***Authentification ouverte :*** Le terminal demande simplement l'accès au réseau sans fournir de preuve d'identité. Bien que cela puisse sembler peu sécurisé, l'authentification ouverte est souvent suivie d'une étape de sécurisation supplémentaire, comme le chiffrement WPA/WPA2, pour protéger la communication.
* **Authentification par clé partagée (WEP) :** Un processus légèrement plus sécurisé, où le terminal et le point d'accès partagent une clé WEP (Wired Equivalent Privacy) préconfigurée. Le terminal doit prouver qu'il connaît la clé WEP pour s'authentifier. Cependant, WEP est considéré comme obsolète et facilement piratable en raison de ses vulnérabilités bien documentées.
## Etape 2 : Association du client
* Le terminal demande à être associé à un point d'accès spécifique. 
* Cette étape implique la négociation des capacités du terminal et du point d'accès, comme 
	* Les taux de données
	* Les canaux de fréquence utilisés. 
* L'association assure que le terminal et le point d'accès sont compatibles et prêts à communiquer efficacement. 
* Si l'association réussit, le point d'accès inscrit le terminal dans sa table d'association, permettant au terminal d'accéder aux ressources du réseau.
## Etape 3 : Echange de données
* Le terminal est prêt à échanger des données avec le réseau. 
* À ce stade, des mesures de sécurité supplémentaires sont souvent mises en place pour protéger la communication
	* Protocole WPA (Wi-Fi Protected Access) 
	* Protocole WPA2,WPA3
		* Chiffrement des données transmises entre le terminal et le point d'accès, assurant ainsi la confidentialité et l'intégrité des données.

# 2) Type de trames 
## Trames de données
* Transporte les données de l'utilisateur (telles que les fichiers, les pages web, les e-mails, etc.) à travers le réseau sans fil. 
* Elles contiennent non seulement le payload (les données utiles), mais aussi les adresses du destinataire et de l'expéditeur, ainsi qu'un champ de contrôle de séquence pour assurer l'ordonnancement correct des trames arrivant au destinataire. 
* La fiabilité de la transmission est assurée par des accusés de réception (ACKs) et des mécanismes de retransmission en cas de perte de trames.
## Trames de controle d'accès au support
Les trames de contrôle d'accès au support sont utilisées pour faciliter la livraison fiable des trames de données dans un environnement sans fil, où les collisions peuvent se produire en raison du partage du médium. Voici deux exemples principaux :
- **RTS/CTS (Request To Send/Clear To Send) :** Ce mécanisme aide à réduire les collisions de trames dans des environnements WLAN denses. Un terminal envoie une trame RTS pour annoncer son intention d'envoyer des données. Le point d'accès répond par une trame CTS après avoir vérifié que le canal est libre, donnant ainsi la permission à l'émetteur de commencer la transmission. Ce processus aide à réserver le canal et à informer les autres terminaux d'éviter les transmissions pendant cette période.
- **ACK (Acknowledgment) :** Après la réception réussie d'une trame de données, le destinataire envoie une trame d'accusé de réception (ACK) à l'expéditeur pour confirmer la réception. Si l'expéditeur ne reçoit pas d'ACK dans un délai spécifié, il peut supposer que la trame a été perdue et la retransmet.
## Trame de gestion
Les trames de gestion sont essentielles pour établir et maintenir la communication entre les terminaux et les points d'accès. Elles couvrent une variété de fonctions, dont :
- **Authentification :** Ces trames sont utilisées dans la phase initiale de connexion pour vérifier l'identité du terminal cherchant à se joindre au réseau. C'est la première étape du processus d'association.
- **Association :** Une fois l'authentification réussie, les trames d'association sont échangées pour permettre au terminal de devenir un membre actif du réseau, lui permettant ainsi d'envoyer et de recevoir des trames de données.
- **Synchronisation :** Ces trames aident à synchroniser les horloges des terminaux avec celle du point d'accès pour assurer une coordination dans l'utilisation du canal de communication.



# 3) Protocoles WLAN

### 3.1) Méthode de transport
| Standard      | Année de publication | Bande de fréquence  | Débit maximal théorique | Caractéristiques clés                                |
|---------------|----------------------|---------------------|-------------------------|-----------------------------------------------------|
| 802.11a       | 1999                 | 5 GHz               | 54 Mbps                 | Première norme à utiliser la bande des 5 GHz        |
| 802.11b       | 1999                 | 2,4 GHz             | 11 Mbps                 | Introduit la bande des 2,4 GHz pour une plus grande portée |
| 802.11g       | 2003                 | 2,4 GHz             | 54 Mbps                 | Combine les bandes de 2,4 GHz avec des vitesses plus élevées |
| 802.11n (Wi-Fi 4) | 2009            | 2,4 GHz et 5 GHz    | 600 Mbps                | Introduit la technologie MIMO pour augmenter le débit |
| 802.11ac (Wi-Fi 5) | 2013           | 5 GHz               | Plusieurs Gbps          | Successeur de 802.11n, avec des débits nettement améliorés |
| 802.11ax (Wi-Fi 6) | 2019           | 2,4 GHz, 5 GHz , 6 GHz | Encore plus élevés que le 802.11ac | Améliorations majeures en termes de capacité, de couverture et de performances |
### 3.2) Méthode de sécurité
| Norme Wi-Fi | Méthode d'authentification | Méthode de chiffrement | Algorithme de chiffrement |
|-------------|----------------------------|------------------------|---------------------------|
| Aucune      | Open System ou Shared Key  | WEP                    | RC4                       |
| WPA Personal| PSK                    | TKIP                   | RC4                       |
| WPA Enterprise| 802.1X/EAP               | TKIP                   | RC4                       |
| WPA2 Personal| PSK                  | CCMP | AES |
| WPA2 Enterprise| 802.1X/EAP              | CCMP | AES |
| WPA3 Personal| Simultaneous Authentication of Equals (SAE) avec forward secrecy (FS/PFS) | GCMP | AES |
| WPA3 Enterprise| 802.1X/EAP              | GCMP                   | AES                       |
### 3.3) Méthode de contrôle d'accès
- **802.1X** : Correctement identifié comme une méthode de contrôle d'accès, 802.1X fournit un cadre d'authentification pour les réseaux, utilisé en conjonction avec WPA et WPA2 dans les environnements d'entreprise pour sécuriser l'accès au réseau.
- EAP : Cadre (framework) d’authentification dans les réseaux sans-fil qui permet le transport sécurisé de matériel d’authentification dans un environnement non sécurisé par définition via des méthodes : TLS, TTLS, PEAP
# 4) Open Authentification
L'authentification ouverte (Open Authentication) dans les réseaux WLAN permet aux appareils de se connecter à un point d'accès sans nécessiter de mot de passe spécifique pour l'accès au réseau. Cependant, cela ne signifie pas nécessairement que le réseau est dépourvu de toute mesure de sécurité. Voici comment l'authentification ouverte peut être mise en œuvre, avec ou sans mesures de sécurité supplémentaires :
## 4.1) Sans sécurité
* Aucun mécanisme de sécurité n'est appliqué après l'authentification. 
* Les données transmises entre les clients et le point d'accès ne sont pas chiffrées, ce qui les rend vulnérables aux écoutes et aux attaques par des tiers non autorisés.
## 4.2) Via filtrage MAC
* Le filtrage MAC permet au point d'accès de contrôler l'accès au réseau en vérifiant l'adresse MAC de chaque appareil tentant de se connecter. 
* Seuls les appareils dont les adresses MAC sont préalablement enregistrées dans la liste de contrôle d'accès du point d'accès seront autorisés à se connecter. 
* Les adresses MAC peuvent être usurpées (spoofed) par des attaquants, ce qui réduit l'efficacité de cette méthode comme unique mesure de sécurité.
## 4.3) Via portail captif
* Avant d'accéder à Internet, l'utilisateur doit s'authentifier ou accepter les termes et conditions d'utilisation du réseau. 
* Ils ne chiffreront pas les données transmises sur le réseau et ne doivent pas être considérés comme une mesure de sécurité pour protéger les données transmises.


# 5) Méthode d'authentification et chiffrement WPA

## 5.1) Mode personnel/domestique (PSK)

### 5.1) AES via PSK (WPA2)

#### Principe de chiffrement AES utilisant la PTK générée à partir de la PMK dérivée de la PSK
* AES est un algorithme de chiffrement symétrique qui utilise une clé préétablie pour chiffrer (coder) et déchiffrer (décoder) les informations
* PSK est juste un passphrase pour initier la création de la PKT necessaire à AES pour chiffrer
* Dans WPA2 AES chiffre la communication entre le PA et client, pour ca il utilise la clef d'authentification créer PKT entre le client et le PA
#### Eléments cléfs de AES via PSK
1. **PMK (Pairwise Master Key)**:
    - Générée à partir de passphrase (PSK), le SSID comme sel, et le nombre d'itérations (4096 pour WPA/WPA2) pour produire la PMK.
    - Considérée comme une clé de niveau supérieur à partir de laquelle d'autres clés sont générées.
2. **PTK (Pairwise Transient Key)**:
    - Générée à partir de la PMK lors du 4-Way Handshake
    - Utilisée pour chiffrer les données échangées entre un dispositif client et le PA.
3. **GTK (Group Temporal Key)**:
    - Utilisée pour chiffrer le trafic multicast et broadcast dans le réseau WLAN.
    - Distribuée par le PA aux clients après une authentification réussie pour assurer que tout le trafic de groupe est également sécurisé.
#### Processus d'authentification et chiffrement AES via PSK
0. **Point d'accès (PA) et Dispositifs Clients** : La PSK est configurée sur le PA et doit être entrée sur chaque dispositif client souhaitant se connecter au réseau.
1. **Demande de Connexion** : Un dispositif client tente de se connecter au réseau WLAN en spécifiant le SSID du PA.
2. **Authentification** : Le dispositif et le PA s'authentifient mutuellement en utilisant la PSK. Cette étape s'assure que le client connaît la PSK.
3. **Génération de la PMK** : Le dispositif client et le PA génèrent indépendamment la PMK à partir de la PSK en utilisant le SSID comme sel et une fonction de dérivation de clé (comme PBKDF2).
4. **4-Way Handshake** : Processus d'établissent d'une clé de session temporaire PTK et de distribution de la GTK pour le trafic multicast/broadcast
    - **Message 1** : Le PA envoie un nombre au client.
    - **Message 2** : Le client génère un PTK et envoi un nombre au PA
    - **Message 3** : Le PA génère une PTK et envoie la GTK au client
    - **Message 4** : Le client confirme la réception de la GTK et que le 4-Way Handshake est complet.
5. ***Utilisation de PTK et GTK*** : La PTK est utilisée pour chiffrer les données un-à-un entre le client et le PA, tandis que la GTK est utilisée pour chiffrer le trafic multicast et broadcast dans le réseau.
6. **Chiffrement des Données** : Toutes les données échangées entre le client et le PA sont chiffrées avec AES en utilisant la clé de chiffrement issue de la PTK. Le trafic de groupe est sécurisé avec la GTK.
### 5.2) AES via PSK-SAE (WPA3)

A FAIRE 
## 5.2) Mode entreprise (802.1X via EAP)

### 5.2.1) Controle d'accès 802.1X 
* Mécanisme d’authentification pour les périphériques attachés à un WLAN/LAN
* 3 roles distincts 
	- Le ***Supplicant*** est le client (l’ordinateur terminal) qui veut se connecter à la facilité de couche 2 (L2) LAN ou WLAN.
	- L’***Authenticator*** : Périphérique qui contrôle l’accès au réseau, dans les technologies sans fil, le point d’accès (AP) ou le commutateur Ethernet pour un accès filaire.
	- L’***Authentication Server*** : Serveur d’authentification Radius qui rend un avis (Radius Accept/Radius Reject) en se fondant sur une source d’utilisateurs qui peut être par exemple un annuaire LDAP.
- Processus d'authentification : 
1. **Requête d'Accès** :
    - Le poste utilisateur (supplicant) demande l'accès au réseau en envoyant ses identifiants (login et mot de passe) au client RADIUS (souvent le point d'accès, le commutateur ou le routeur).
2. **Génération de l'Access-Request** :
    - L'authenticator (le client RADIUS) crée une requête Access-Request contenant les informations d'authentification fournies par le supplicant.
3. **Traitement par le Serveur RADIUS** :
    - Le serveur RADIUS reçoit l'Access-Request. Il peut soit traiter directement la demande d'authentification si toutes les informations nécessaires sont présentes, soit agir en tant que proxy et transférer la requête à un autre serveur RADIUS (Home Radius).
4. **Échanges de Paquets** :
    - Si le serveur RADIUS (Home Radius) nécessite des informations supplémentaires pour l'authentification, il envoie un paquet Access-Challenge au supplicant.
    - Le supplicant répond à ce challenge avec un autre Access-Request contenant les informations demandées.
5. **Échanges Inter-Serveurs** :
    - Si la requête est traitée par des serveurs RADIUS intermédiaires (proxy), les échanges entre le supplicant et le serveur d'authentification final sont relayés par ces serveurs proxy.
6. **Validation ou Refus** :
    - Après avoir obtenu toutes les informations nécessaires et avoir effectué les vérifications appropriées (ce qui peut nécessiter plusieurs échanges, surtout avec des protocoles complexes comme EAP), le serveur RADIUS finalise le processus.
    - Si les identifiants sont valides et que l'authentification est réussie, le serveur RADIUS envoie un paquet Access-Accept au supplicant via l'authenticator.
    - Si l'authentification échoue, le serveur envoie un paquet Access-Reject.
7. **Établissement de la Connexion** :
    - À réception d'un Access-Accept, l'authenticator autorise l'accès au réseau pour le supplicant.
    - En cas de réception d'un Access-Reject, l'accès au réseau est refusé au supplicant.

![authentification802.1x_radius](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/authentification802.1x_radius.png)
### 5.2.2)  EAP
* Cadre (framework) d’authentification couramment utilisé dans les réseaux sans-fil et les connexions point à point
* Composant fondamental et toujours présent du standard 802.1X 
* Permet de transporter les messages d'authentification nécessaires entre le supplicant et le serveur RADIUS en utilisant des méthodes spécifiques (EAP-TLS, EAP-TTLS, et PEAP) afin de déterminer comment l'authentification est réalisée et quelles informations sont échangées pour vérifier l'identité du supplicant
* Articulation des Composants
	- Le **supplicant** commence par demander l'accès au réseau.
	- L'**authenticator** (point d'accès ou commutateur) relaie cette demande au **serveur RADIUS** en utilisant EAP encapsulé dans des paquets RADIUS.
	- Le **serveur RADIUS** utilise la méthode EAP appropriée pour demander les informations d'authentification nécessaires au supplicant.
	- Le supplicant répond, et le serveur RADIUS vérifie ces informations. Si elles sont correctes, le serveur RADIUS envoie un message de succès (via l'authenticator) au supplicant, qui est alors autorisé à accéder au réseau.

[![Authentification 802.1X EAP](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/authentification802.1x_eap.png)](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/authentification802.1x_eap.png)
##### EAP-TLS
* Utilise des certificats numériques à la fois sur le serveur et sur le client pour l'authentification.
* C'est l'une des méthodes les plus sûres car elle fournit une authentification mutuelle.
##### EAP-TTLS
* Permet au client de s'authentifier en utilisant diverses méthodes après avoir établi un canal sécurisé basé sur le certificat du serveur. 
* Cela permet d'utiliser des mots de passe stockés de manière sécurisée sans avoir besoin de certificats côté client.
##### EAP-PEAP
* Comme EAP-TTLS, PEAP crée un tunnel sécurisé pour protéger l'échange d'informations d'authentification. 
* À l'intérieur du tunnel, le client peut s'authentifier avec un nom d'utilisateur et un mot de passe.
#### Tableau récapitulatif EAP
| Fonctionnalité | EAP-TLS | EAP-TTLS | PEAPv0 (EAP-MSCHAPv2) | PEAPv0 (EAP-TLS) | PEAPv1 (EAP-GTC) |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Type de solution | RFC 5216 | RFC 5281 | IETF draft | IETF draft | RFC 4851 |
| Certificats numériques — Client | Oui | Optionnel | Non | Oui | Optionnel |
| Certificats numériques — Serveur | Oui | Oui | Oui | Oui | Non |
| Authentification Client par mot de passe | indisponible | Oui | Oui | Non | Oui |
| PACs — Client | Non | Non | Non | Non | Oui |
| PACs — Serveur | Non | Non | Non | Non | Oui |
| Sécurité des crédits | Fort | Fort | Fort | Fort | Fort (si la Phase 0 est sécurisée) |
| Gestion des clés de chiffrement | Oui | Oui | Oui | Oui | Oui |
| Authentification Mutuelle | Oui | Oui | Oui | Oui | Oui |
| Authentification dans un tunnel | Optionnel | Oui | Oui | Oui | Oui |
| Normalisé Wi-Fi Alliance | Oui | Oui | Non | Oui | Oui |




