# Le Wi-Fi

## 1. C'est quoi le protocole?
Le Wi-Fi (Wireless Fidelity) est une technologie qui permet la transmission de données sans fil entre des dispositifs à l'aide d'ondes radio. Il repose sur un ensemble de normes définies par l'IEEE sous la série 802.11, qui spécifie comment les données sont encodées et transmises sur des canaux radio spécifiques.

## 2. C'est quoi le but et l'intérêt du protocole?
Le but principal du Wi-Fi est de fournir un accès à Internet ou à un réseau local sans avoir besoin de câbles, offrant ainsi une grande flexibilité et mobilité aux utilisateurs. L'intérêt du Wi-Fi réside dans sa simplicité de déploiement, sa portabilité, et sa capacité à connecter un grand nombre d'appareils dans des environnements variés, qu'il s'agisse de maisons, de bureaux, d'aéroports, de cafés ou de lieux publics.

Les avantages du Wi-Fi incluent :
* **Mobilité** : Les utilisateurs peuvent se déplacer librement tout en restant connectés.
* **Facilité d'installation**: Pas besoin de tirer des câbles.
* **Évolutivité**: Facile d'ajouter des dispositifs supplémentaires à un réseau Wi-Fi.
* **Connexion multiple**: Plusieurs dispositifs peuvent se connecter à un même point d'accès.

## 3. Quels sont les cas courants d'utilisation du protocole?
Le Wi-Fi est omniprésent dans de nombreux scénarios d'utilisation, parmi lesquels :
* **Ménages**: Pour connecter ordinateurs, smartphones, tablettes, téléviseurs intelligents, consoles de jeux, et autres appareils domestiques à Internet.
* **Bureaux et entreprises**: Pour fournir un accès Internet aux employés, visiteurs, ou pour connecter des équipements d'entreprise.
* **Lieux publics**: Aéroports, hôtels, cafés, bibliothèques et universités offrent souvent un accès Wi-Fi gratuit ou payant à leurs visiteurs.
* **Villes intelligentes**: Pour offrir un accès Internet dans des espaces publics comme les parcs ou les places.
* **Transport**: Dans les trains, bus ou avions, pour offrir une connectivité pendant le voyage.
* **Événements**: Dans les conventions, salons ou festivals pour connecter les participants.
## 4. Comment fonctionne le protocole?
Le Wi-Fi opère principalement dans les bandes de fréquences 2,4 GHz et 5 GHz. Les points d'accès (routeurs sans fil) diffusent un identifiant de réseau, appelé SSID (Service Set Identifier). Lorsqu'un appareil souhaite se connecter à un réseau Wi-Fi, il scanne les ondes radio à la recherche de SSID disponibles, puis établit une connexion en utilisant un protocole d'échange appelé "handshake", qui inclut généralement une forme d'authentification comme un mot de passe.

Les données sont transmises sous forme de paquets entre le dispositif et le point d'accès. Ces paquets sont encodés et modulés en ondes radio, qui sont ensuite démodulées et décodées par le dispositif récepteur.

## 5. Quels sont les éléments du protocole?
Les principaux éléments impliqués dans une communication Wi-Fi comprennent:
* **Point d'accès (AP)** : Appareil qui diffuse le signal Wi-Fi et fait le lien entre le réseau sans fil et le réseau filaire (par exemple, Internet).
* **SSID (Service Set Identifier)** : Nom du réseau Wi-Fi.
* **Stations**: Tout dispositif qui se connecte au réseau Wi-Fi, comme les smartphones, ordinateurs, tablettes, etc.
* **Protocole de chiffrement**: Pour sécuriser la communication, comme WEP (obsolète et non sécurisé), WPA, WPA2 ou WPA3.
* **Canal**: Une sous-division spécifique de la bande de fréquences utilisée pour éviter les interférences.

## 6. Quels sont les versions et les caractéristiques?
Le Wi-Fi a connu plusieurs versions au fil des années, chacune avec ses propres améliorations et caractéristiques:

* **802.11a** (1999) : Opère sur la bande des 5 GHz, débit maximal de 54 Mbps.
* **802.11b** (1999) : Opère sur la bande des 2,4 GHz, débit maximal de 11 Mbps.
* **802.11g** (2003) : Opère sur la bande des 2,4 GHz, débit maximal de 54 Mbps.
* **802.11n (Wi-Fi 4)** (2009) : Peut opérer sur les bandes 2,4 GHz et 5 GHz. Introduit la technologie MIMO (Multiple Input Multiple Output). Débit maximal théorique de 600 Mbps.
* **802.11ac (Wi-Fi 5)** (2013) : Opère principalement sur la bande des 5 GHz. Successeur de 802.11n avec des débits allant jusqu'à plusieurs Gbps en théorie.
* **802.11ax (Wi-Fi 6)** (2019) : Opère sur les bandes 2,4 GHz, 5 GHz, et potentiellement d'autres. Améliorations majeures en termes de capacité, de couverture et de performances. Débits théoriques encore plus élevés que le 802.11ac.
## 7. Il y a-t-il différents types?
Oui, le Wi-Fi ne se limite pas seulement aux réseaux domestiques ou d'entreprise. Voici quelques types de configurations Wi-Fi:

* **Wi-Fi Domestique**: Le type le plus courant, utilisé pour connecter des appareils dans un foyer.
* **Wi-Fi Entreprise**: Utilise des fonctionnalités de sécurité supplémentaires et des capacités pour gérer un grand nombre d'appareils.
* **Hotspots publics**: Points d'accès Wi-Fi offerts dans des lieux publics comme des cafés, hôtels ou aéroports.
* **Wi-Fi Direct**: Permet la communication directe entre appareils sans avoir besoin d'un point d'accès central.
* **Ad-hoc**: Réseau sans fil temporaire entre plusieurs appareils sans utiliser un point d'accès.

## 8. Comment une communication qui utilise ce protocole s'établit?
L'établissement d'une communication Wi-Fi suit généralement ces étapes:

1. **Diffusion de SSID**: Le point d'accès diffuse régulièrement son SSID pour signaler sa présence aux dispositifs à proximité.
2. **Demande de connexion**: L'appareil, après avoir détecté un SSID, envoie une demande de connexion au point d'accès.
3. **Authentification**: Si le réseau est sécurisé, l'appareil doit fournir les informations d'authentification requises (généralement un mot de passe).
4. **Établissement de la connexion**: Une fois authentifié, un échange d'informations a lieu pour établir la connexion. Cela inclut l'assignation d'une adresse IP à l'appareil par le point d'accès.
5. **Communication**: Les données peuvent maintenant être échangées entre l'appareil et le réseau, que ce soit pour accéder à Internet, partager des fichiers ou d'autres activités.

## 9. Quels sont les failles de sécurité du protocole?
Le Wi-Fi, malgré ses nombreux avantages, a également été sujet à diverses failles de sécurité au fil des ans:

* **WEP (Wired Equivalent Privacy)**: Ce protocole de sécurité obsolète est facilement piratable et ne devrait plus être utilisé.
* **Attaques "man-in-the-middle"**: Des attaquants peuvent se placer entre un appareil et un point d'accès pour intercepter le trafic.
* **Attaques par force brute**: Des tentatives répétées pour deviner le mot de passe d'un réseau.
* **KRACK (Key Reinstallation Attacks)**: Une vulnérabilité dans le protocole WPA2 qui permet à des attaquants de décrypter le trafic entre un appareil et un point d'accès.
* **Rogue APs (Points d'accès malveillants)**: Des points d'accès illégitimes qui se font passer pour des réseaux légitimes pour intercepter le trafic des utilisateurs.


## 10. Sécurité Wi-Fi : Évolution des protocoles

### WPA (Wi-Fi Protected Access)
Le **WPA** a été introduit comme une amélioration par rapport à WEP (Wired Equivalent Privacy) qui présentait des failles de sécurité importantes. Il a introduit le protocole TKIP (Temporal Key Integrity Protocol) pour le chiffrement, qui était plus sûr que le chiffrement WEP.

**Avantages**:
* Utilise TKIP pour améliorer la sécurité.
* Implémentation du protocole 802.1X pour l'authentification.

**Inconvénients**:
* Même si le WPA était une amélioration par rapport au WEP, il était toujours vulnérable à certaines attaques, notamment celles exploitant des faiblesses dans TKIP.

### WPA2 (Wi-Fi Protected Access II)
**WPA2** est la deuxième version de WPA et est devenue la norme pour la sécurité Wi-Fi. Il a remplacé TKIP par le protocole de chiffrement AES (Advanced Encryption Standard), beaucoup plus robuste.

**Avantages**:
* Utilise le chiffrement AES, largement reconnu comme étant très sûr.
* Prend en charge 802.1X pour une meilleure authentification.

**Inconvénients**:
* Malgré sa sécurité renforcée, WPA2 a été compromis par la vulnérabilité KRACK, ce qui a conduit au développement de WPA3.

### WPA3 (Wi-Fi Protected Access III)
**WPA3** est la dernière version de ce protocole de sécurité et vise à améliorer plusieurs des faiblesses de WPA2.

**Avantages**:
* Chiffrement plus robuste et résistance renforcée contre les attaques par force brute.
* Simplification du processus de configuration pour les appareils sans écran.
* Protection accrue contre les attaques "man-in-the-middle".

**Inconvénients**:
* Bien que WPA3 soit actuellement considéré comme le protocole de sécurité Wi-Fi le plus sûr, aucun protocole n'est à l'abri des futures vulnérabilités. Il est donc essentiel de toujours rester informé et à jour.

### WPS (Wi-Fi Protected Setup)
**WPS** est une méthode introduite pour simplifier la connexion d'appareils à un réseau Wi-Fi. Au lieu d'entrer un mot de passe, les utilisateurs peuvent appuyer sur un bouton sur le routeur ou entrer un PIN pour se connecter.

**Avantages**:
* Facilite la connexion d'appareils au Wi-Fi, en particulier pour les personnes non technophiles.

**Inconvénients**:
* Le mécanisme basé sur le PIN est vulnérable aux attaques par force brute.
* De nombreux experts en sécurité recommandent de désactiver WPS si possible pour éviter les risques potentiels.

En résumé, la sécurité Wi-Fi a évolué au fil des ans pour répondre à un éventail toujours croissant de menaces. Il est crucial pour les utilisateurs et les administrateurs de réseau de comprendre ces protocoles et de s'assurer que leurs réseaux sont configurés aussi sûrement que possible.