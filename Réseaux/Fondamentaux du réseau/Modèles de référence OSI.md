# Guide OSI/TCP 

# I) Modèle OSI et TCP/IP

* Afin de bien comprendre comment nos systèmes communiquent entre eux, on a défini plusieurs modèles qui se ressemblent pour mettre chaque système de communication sur la même logique de connexion et de transport d’information.
# II) Rôles des couches 

## 1) Couche physique 
* Objectif : Définit les spécifications électriques et physiques de la connexion des données
* Exemple :
	* disposition des broches du connecteur, 
	* les tensions de fonctionnement d'un câble électrique, 
	* les spécifications des câbles (cuivre, fibre)
	* la fréquence des appareils sans fil
* Responsable de la transmission et de la réception de données brutes non structurées sur un support physique et du contrôle du débit binaire
* Composants : Câbles (cuivre, fibre),Sans fil, Concentrateur, répéteur
* Fonction : Définit comment les signaux électriques, optiques ou radio sont convertis en bits et vice-versa
## 2) Couche liaison de données
* Objectif : 
	* Assurer le transfert de données entre deux noeuds directement connectés
	* Définit le protocole d'établissement de connexion entre 2 appareils connectés physiquement
		* PPP pour les réseaux WAN
		* Ethernet Pour les réseaux LAN
	* Etablit et assure la communication entre 2 noeuds sur un support
	* Définit les procédures d’exploitation du lien de communication
	- Fournit un cadrage et un séquençage
* Divisé en 2 sous couches 
	* **Logical Link Control – LLC**
		* Identifie les protocoles réseau, effectue une vérification des erreurs et synchronise les cadres
		* Responsable de l'identification et de l'encapsulation des protocoles de la couche réseau, et contrôle la vérification des erreurs et la synchronisation des trame
	* **Media Access Control – MAC**
		* Utilise des adresses MAC pour connecter les périphériques et définir les autorisations pour transmettre et recevoir des données
		* Contrôle la façon dont les appareils d'un réseau accèdent à un support et sont autorisés à transmettre des données
* Composants : Switch (commutateur), MAC
## 3) Couche réseau
* Objectif : 
	* Router des paquets en découvrant le meilleur chemin à travers un réseau physique
	* Briser les segments en paquets de réseau et à réassembler les paquets à l’extrémité de réception
* Composants : Routeurs, MLS, IP
* Fonction : Routage des paquets entre les sous-réseaux, fragmentation et désassemblage des paquets.
* Exemple : Protocole de routage dynamique, routage statique, table de routage
## 4) Couche transport 
* Objectif : 
	* Transférer des séquences de données d'une source à un hôte de destination via un ou plusieurs réseaux, tout en conservant les fonctions de qualité de service (QoS) et en assurant la livraison complète des données.
	* Établir, gérer et terminer les connexions (ou sessions) entre deux machines communicantes.
* Composants : TCP, UDP
* Fonction : Contrôle de flux, multiplexage, détection d'erreurs, séquençage.
## 5) Couche session 
* Objectif : 
	* Contrôle les dialogues (connexions) entre les ordinateurs. 
	* Etablit, gère, entretient et met fin aux connexions entre l'application locale et l'application distante.
	*  Gère les fonctions d'authentification et d'autorisation.
* Composants : RPC, SIP, RTP, 
* Fonction : Contrôle de dialogue, gestion de session.
## 6) Couche présentation 
* Objectif : 
	* Vérifie les données pour s'assurer qu'elles sont compatibles avec les ressources de communication.
	* Responsable de tout formatage de données, conversion de code, compression et le cryptage des données
	*  Gère les fonctions d'authentification et d'autorisation.
## 7) Couche application
* Objectif : 
	* Responsable des applications logicielles pour fournir des fonctions de communication
* Composants : HTTP, FTP, SMTP, DNS , DHCP, ... 
* Gestion des services réseau : e-mail, transfert de fichiers, accès à distance, gestion de réseau.

# III) Encapsulation et décapsulation

* Lors d’une communication, chaque donnée suit une route identique où l’on va ajouter différentes informations de chaque couche dans l’autre afin que les données arrivent à destination et soit lisible.

* Chaque paquet IP contient l’IP source et l’IP destination  Les routeurs acheminent donc les paquets vers leur destination, de proche en proche.

# IV) Encapsulation et décapsulation

* Lors d’une communication, chaque donnée suit une route identique où l’on va ajouter différentes informations de chaque couche dans l’autre afin que les données arrivent à destination et soit lisible.