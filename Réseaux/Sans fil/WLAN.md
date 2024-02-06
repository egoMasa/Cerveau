# Sommaire 
- [x] Authentification basique d'un terminal à un point d'accès
	- [ ] Authentification
	- [ ] Association
	- [ ] Echange de données
- [x] Contrainte de sécurité
	- [ ] Authentification
	- [ ] Chiffrement
	- [ ] Intégrité
- [x] Type de trames 
	- [ ] Trames de données
	- [ ] Trames de controle d'accès au support
		- [ ] RTS/CTS
		- [ ] ACK
	- [ ] Trame de gestion
		- [ ] Authentification, Association, Synchronisation
- [x] Open Authentification
	- [ ] Sans sécurité
	- [ ] Via filtrage MAC
	- [ ] Via portail captif
- [ ] Protocoles de sécurité WLAN
	- [ ] 802.11
	- [ ] WAP1,WAP2,WAP3
	- [ ] 802.11i
- [ ] Protocoles de chiffrement
	- [ ] WEP,TKIP,AES (128-256bits)
- [ ] Méthode d'utilisation des cléfs
	- [ ] Meme clefs, changement périodique, cléf unique par paquet et par personne
- [ ] Méthode de controle d'intégrité
	- [ ] CRC, Michael, AES
- [ ] Méthode d'authentification et gestion des cléfs
	- [ ] Personnel
		- [ ] PSK,PSK-SAE 802.1X
	- [ ] Entreprise
		- [ ] EAP, EAP-TLS,EAP-TTLS, EAP-PEAP
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
Les trames de données sont les unités de base utilisées pour transporter les données de l'utilisateur (telles que les fichiers, les pages web, les e-mails, etc.) à travers le réseau sans fil. Elles contiennent non seulement le payload (les données utiles), mais aussi les adresses du destinataire et de l'expéditeur, ainsi qu'un champ de contrôle de séquence pour assurer l'ordonnancement correct des trames arrivant au destinataire. La fiabilité de la transmission est assurée par des accusés de réception (ACKs) et des mécanismes de retransmission en cas de perte de trames.
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

# 4) Protocoles WLAN

### Méthode de transport
- **802.11a** : Effectivement, c'est une méthode de transport qui spécifie les modalités de communication dans la bande des 5 GHz avec une vitesse maximale de 54 Mbps. Cependant, le terme "méthode de transport" peut être généralisé pour inclure toutes les variantes de 802.11 (b, g, n, ac, ax) qui définissent différentes méthodes de transmission des données via des bandes de fréquence spécifiques et avec différentes technologies (comme MIMO pour 802.11n, ou OFDMA pour 802.11ax).
### Méthode de sécurité
- **802.11** : Ce terme désigne en réalité la famille de standards pour les réseaux sans fil, et inclut des aspects de sécurité, mais n'est pas spécifiquement une méthode de sécurité. Il serait plus précis de le mentionner comme le standard de base pour les réseaux WLAN.
- **802.11i / WPA2** : C'est le standard qui spécifie les méthodes de sécurité pour les réseaux sans fil, offrant une base pour WPA2 avec un chiffrement renforcé par AES.
- **WPA / WPA2 / WPA3** : Ces termes désignent les différentes versions des protocoles de sécurité Wi-Fi, avec WPA2 basé sur 802.11i et WPA3 offrant des améliorations de sécurité supplémentaires par rapport à WPA2.
#### Méthode d'encryption des méthodes de sécurité
- **WEP, TKIP, AES** : Ces termes sont correctement classifiés comme des méthodes d'encryption. WEP est le plus ancien et considéré comme obsolète en raison de ses faiblesses de sécurité. TKIP a été introduit avec WPA comme une amélioration par rapport à WEP, mais a également été remplacé par AES, qui est la méthode d'encryption la plus sécurisée utilisée par WPA2 et WPA3.
### Méthode de contrôle d'accès
- **802.1X** : Correctement identifié comme une méthode de contrôle d'accès, 802.1X fournit un cadre d'authentification pour les réseaux, utilisé en conjonction avec WPA et WPA2 dans les environnements d'entreprise pour sécuriser l'accès au réseau.


