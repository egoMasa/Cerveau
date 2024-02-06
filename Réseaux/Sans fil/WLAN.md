# Sommaire 

- [ ] Protocole de controle d'accès 802.1X
	- [ ] Différentes phases d'authentification
	- [ ] 2 ports logique, serveur radius
	- [ ] Trame EAPoL
- [ ] Protocole WAP2
	- [ ] Processus de gestion des cléfs(4Way HandShake Protocol)
	- [ ] Elements d'échange
	- [ ] Limitation de sécurité : Meme PMK pour tous le monde
- [ ] Protocole WAP3
	- [ ] Processus de gestion des cléfs
	- [ ] Elements d'échange

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


# 3) Open Authentification
L'authentification ouverte (Open Authentication) dans les réseaux WLAN permet aux appareils de se connecter à un point d'accès sans nécessiter de mot de passe spécifique pour l'accès au réseau. Cependant, cela ne signifie pas nécessairement que le réseau est dépourvu de toute mesure de sécurité. Voici comment l'authentification ouverte peut être mise en œuvre, avec ou sans mesures de sécurité supplémentaires :
## Sans sécurité
* Aucun mécanisme de sécurité n'est appliqué après l'authentification. 
* Les données transmises entre les clients et le point d'accès ne sont pas chiffrées, ce qui les rend vulnérables aux écoutes et aux attaques par des tiers non autorisés.
## Via filtrage MAC
* Le filtrage MAC permet au point d'accès de contrôler l'accès au réseau en vérifiant l'adresse MAC de chaque appareil tentant de se connecter. 
* Seuls les appareils dont les adresses MAC sont préalablement enregistrées dans la liste de contrôle d'accès du point d'accès seront autorisés à se connecter. 
* Les adresses MAC peuvent être usurpées (spoofed) par des attaquants, ce qui réduit l'efficacité de cette méthode comme unique mesure de sécurité.
## Via portail captif
* Avant d'accéder à Internet, l'utilisateur doit s'authentifier ou accepter les termes et conditions d'utilisation du réseau. 
* Ils ne chiffreront pas les données transmises sur le réseau et ne doivent pas être considérés comme une mesure de sécurité pour protéger les données transmises.


# 4) Méthode d'authentification et chiffrement WPA2

## 4.1) AES via PSK

### Principe de chiffrement AES utilisant la PTK générée à partir de la PMK dérivée de la PSK
* AES est un algorithme de chiffrement symétrique qui utilise une clé préétablie pour chiffrer (coder) et déchiffrer (décoder) les informations
* PSK est juste un passphrase pour initier la création de la PKT necessaire à AES pour chiffrer
* Dans WPA2 AES chiffre la communication entre le PA et client, pour ca il utilise la clef d'authentification créer PKT entre le client et le PA
### Eléments cléfs de AES via PSK
1. **PMK (Pairwise Master Key)**:
    - Générée à partir de passphrase (PSK), le SSID comme sel, et le nombre d'itérations (4096 pour WPA/WPA2) pour produire la PMK.
    - Considérée comme une clé de niveau supérieur à partir de laquelle d'autres clés sont générées.
2. **PTK (Pairwise Transient Key)**:
    - Générée à partir de la PMK lors du 4-Way Handshake
    - Utilisée pour chiffrer les données échangées entre un dispositif client et le PA.
3. **GTK (Group Temporal Key)**:
    - Utilisée pour chiffrer le trafic multicast et broadcast dans le réseau WLAN.
    - Distribuée par le PA aux clients après une authentification réussie pour assurer que tout le trafic de groupe est également sécurisé.
## Processus d'authentification et chiffrement AES via PSK
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
## 4.2) AES via PSK-SAE
* Introduit avec WPA3-Personnel pour fournir une méthode d'authentification plus robuste que le PSK traditionnel, offrant une protection contre les attaques offline et les tentatives de devinage du mot de passe.
## 4.3) EAP
* Un framework/cadre d'authentification flexible utilisé dans les configurations d'entreprise pour permettre différentes méthodes d'authentification, telles que les certificats, les mots de passe, ou les tokens.
* **Sécurité renforcée** : EAP fournit une authentification individuelle, permettant une gestion plus fine des accès et une traçabilité des utilisateurs.
- **Scalabilité** : Parfaitement adapté aux grands réseaux d'entreprise avec de nombreux utilisateurs, EAP s'intègre à des systèmes d'authentification existants comme RADIUS ou LDAP.
- **Flexibilité** : EAP supporte plusieurs méthodes d'authentification, permettant aux entreprises de choisir la méthode la plus adaptée à leur politique de sécurité.
- **Gestion des utilisateurs** : Les changements de mots de passe ou les révocations d'accès se gèrent facilement sans affecter tous les utilisateurs du réseau.
### EAP-TLS
### EAP-TTLS
### EAP-PEAP

# 6) Protocoles WLAN

### 6.1) Méthode de transport
| Standard      | Année de publication | Bande de fréquence  | Débit maximal théorique | Caractéristiques clés                                |
|---------------|----------------------|---------------------|-------------------------|-----------------------------------------------------|
| 802.11a       | 1999                 | 5 GHz               | 54 Mbps                 | Première norme à utiliser la bande des 5 GHz        |
| 802.11b       | 1999                 | 2,4 GHz             | 11 Mbps                 | Introduit la bande des 2,4 GHz pour une plus grande portée |
| 802.11g       | 2003                 | 2,4 GHz             | 54 Mbps                 | Combine les bandes de 2,4 GHz avec des vitesses plus élevées |
| 802.11n (Wi-Fi 4) | 2009            | 2,4 GHz et 5 GHz    | 600 Mbps                | Introduit la technologie MIMO pour augmenter le débit |
| 802.11ac (Wi-Fi 5) | 2013           | 5 GHz               | Plusieurs Gbps          | Successeur de 802.11n, avec des débits nettement améliorés |
| 802.11ax (Wi-Fi 6) | 2019           | 2,4 GHz, 5 GHz , 6 GHz | Encore plus élevés que le 802.11ac | Améliorations majeures en termes de capacité, de couverture et de performances |
### 6.2) Méthode de sécurité
| Standard | Année d'apparition | Description et Niveau de sécurité | Chiffrement | Intégrité | Authentification |
| ---- | ---- | ---- | ---- | ---- | :--- |
| 802.11 | 1997 | Introduction des standards WLAN, sécurité initiale via WEP (faible) | WEP | CRC (non sécurisé) | - Open<br>- Filtrage MAC<br>- Portail Captif |
| WPA1 | 2003 | Amélioration de la sécurité avec TKIP (meilleure que WEP) | TKIP | Michael | - Personnel : PSK<br>- Entreprise : EAP |
| 802.11i / WPA2 | 2004 | Introduction d'AES, nette amélioration de la sécurité (élevée) | AES 128 Bits | CCMP (basé sur AES) | - Personnel : PSK <br>- Entreprise : EAP-TLS, EAP-TTLS, EAP-PEAP  |
| WPA3 | 2018 | Améliorations de sécurité supplémentaires, la plus sécurisée | AES 192 bits | GCMP (basé sur AES) | - Personnel : PSK-SAE<br>- Entreprise : EAP-TLS, EAP-TTLS, EAP-PEAP |
### 6.3) Méthode de contrôle d'accès
- **802.1X** : Correctement identifié comme une méthode de contrôle d'accès, 802.1X fournit un cadre d'authentification pour les réseaux, utilisé en conjonction avec WPA et WPA2 dans les environnements d'entreprise pour sécuriser l'accès au réseau.
