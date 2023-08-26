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

* Lorsque qu'on communique sur un réseau, les données que vous envoyez ne sont pas simplement transmises telles quelles. Elles sont traitées, emballées et transmises à travers les différentes couches du modèle OSI ou TCP/IP. Ce processus d'emballage s'appelle l'encapsulation. À l'arrivée, le processus inverse a lieu : la décapsulation.
* L'encapsulation et la décapsulation permettent une **modularité** dans les réseaux. Si une technologie évolue dans une couche, elle peut être mise à jour sans affecter les autres couches.
- Cela garantit également une **séparation des responsabilités**, où chaque couche se concentre sur une fonction spécifique sans se préoccuper des détails des autres couches.
- Cela facilite le **dépannage**. Si un problème survient, les administrateurs réseau peuvent déterminer rapidement à quelle couche du modèle OSI ou TCP/IP il appartient.
## Encapsulation
* L'encapsulation est le processus par lequel une couche du modèle OSI ou TCP/IP ajoute son propre en-tête (et éventuellement un pied de page) aux données qu'elle reçoit de la couche supérieure. Cette opération s'effectue de la couche applicative jusqu'à la couche physique lors de l'envoi d'informations.

* ***Étapes de l'encapsulation** :
1. **Couche Applicative** : Les données sont créées et prêtes à être envoyées.
2. **Couche Transport** : L'en-tête de transport est ajouté (comme TCP ou UDP) transformant les données en segments.
3. **Couche Réseau** : L'en-tête IP est ajouté, transformant les segments en paquets.
4. **Couche Liaison de Données** : L'en-tête de la liaison de données est ajouté, et les paquets deviennent des trames.
5. **Couche Physique** : Les trames sont converties en bits pour être envoyées sur le média.

## Décapsulation

* La décapsulation est le processus inverse de l'encapsulation. Lorsque les données encapsulées atteignent leur destination, chaque couche du modèle OSI ou TCP/IP retire son en-tête (et pied de page si nécessaire) pour récupérer les données originales. Cette opération se déroule de la couche physique à la couche applicative lors de la réception d'informations.

* ***Étapes de la décapsulation** :
1. **Couche Physique** : Les bits sont reçus.
2. **Couche Liaison de Données** : Les en-têtes de la liaison de données sont retirés, transformant les bits en paquets.
3. **Couche Réseau** : L'en-tête IP est retiré, transformant les paquets en segments.
4. **Couche Transport** : L'en-tête de transport est retiré, transformant les segments en données.
5. **Couche Applicative** : Les données sont présentées à l'application utilisateur.