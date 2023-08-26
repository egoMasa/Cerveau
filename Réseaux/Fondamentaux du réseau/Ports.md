# Guide des Ports

## I) Introduction

- Un **port** en informatique peut avoir deux significations principales, liées soit au matériel (hardware), soit au logiciel (software). Le **port matériel** sert à la connexion physique de périphériques, tandis que le **port logiciel** est utilisé pour permettre aux applications de communiquer via des protocoles réseau.

## II) Ports matériels

### Ports internes (généralement présents sur la carte mère) :

- **PCI (Peripheral Component Interconnect)** : Utilisé pour connecter des cartes d'extension comme des cartes graphiques, des cartes son, etc.
- **SATA (Serial Advanced Technology Attachment)** : Utilisé pour connecter des disques durs, des SSDs et des lecteurs optiques.
- **ISA (Industry Standard Architecture)** : Ancien standard pour les cartes d'extension, maintenant largement dépassé.

### Ports externes (pour la connexion de périphériques externes) :

- **USB (Universal Serial Bus)** : Port polyvalent pour la connexion de nombreux périphériques tels que clés USB, souris, claviers, etc.
- **Série (ou port RS-232)** : Ancien standard pour la connexion de périphériques comme les modems.
- **SATA** : Peut aussi être utilisé pour connecter des périphériques externes comme des disques durs externes.

### Ports audio/vidéo :

- **DisplayPort, DVI, HDMI, VGA** : Ports utilisés pour connecter des écrans.
- **Jack** : Port audio pour casques, écouteurs ou haut-parleurs.

### Ports réseaux :

- **RJ45 (Ethernet)** : Utilisé pour la connexion de câbles réseau.

## III) Ports logiciels

- Les ports logiciels sont associés à la **couche de transport (4)** du modèle OSI.
- Ils utilisent principalement deux protocoles : **TCP (Transmission Control Protocol)** et **UDP (User Datagram Protocol)**.
- Chaque port a un numéro unique codé sur **16 bits**, permettant d'avoir _**65 536**_ ports différents. Ces ports sont classés en trois catégories :
    - _**0 à 1 023**_ : Ports "bien-connus" (well-known ports) définis pour les services réseaux standards.
    - _**1 024 à 49 151**_ : Ports enregistrés (registered ports) utilisés pour diverses applications logicielles.
    - _**49 152 à 65 535**_ : Ports dynamiques ou privés, généralement utilisés pour des communications temporaires.

### Quelques ports well-known :

- **20/21** : **FTP (File Transfer Protocol)** pour l'échange de fichiers.
- **22** : **SSH (Secure Shell)** pour les connexions sécurisées et **SFTP** pour le transfert de fichiers sécurisé.
- **23** : **Telnet** pour les connexions non sécurisées à distance.
- **25** : **SMTP (Simple Mail Transfer Protocol)** pour l'envoi d'e-mails.
- **53** : **DNS (Domain Name System)** pour la résolution des noms de domaine.
- **67/68** : **DHCP (Dynamic Host Configuration Protocol)** pour l'attribution d'adresses IP.
- **69** : **TFTP (Trivial File Transfer Protocol)** pour le transfert de fichiers simple.
- **80** : **HTTP (HyperText Transfer Protocol)** pour le web.
- **443** : **HTTPS (HTTP Secure)** pour les requêtes web sécurisées avec SSL/TLS.
- **500** : **IPsec** pour les connexions VPN sécurisées.