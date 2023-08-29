# RFID (Radio Frequency Identification)

## 1. C'est quoi le protocole?
La RFID est une technologie de communication sans fil qui utilise des ondes radio pour identifier automatiquement et de manière unique des objets, des animaux ou des personnes. Elle repose sur un système où un lecteur envoie un signal à une étiquette (ou "tag") qui répond ensuite avec ses informations.

## 2. C'est quoi le but et l'intérêt du protocole?
Le principal objectif de la RFID est de permettre une identification rapide, automatisée et sans contact d'éléments. Elle offre une efficacité accrue dans la gestion des stocks, la traçabilité des objets, et simplifie les processus d'identification.

## 3. Quels sont les cas courants d'utilisation du protocole?
* **Gestion des stocks**: suivi des marchandises dans les entrepôts.
* **Traçabilité**: suivi des articles tout au long de la chaîne d'approvisionnement.
* **Contrôle d'accès**: badges d'employés pour entrer dans des bâtiments sécurisés.
* **Transport**: tickets sans contact pour les transports publics.
* **Médecine**: traçabilité des médicaments et équipements.
* **Paiement**: cartes de paiement sans contact.

## 4. Comment fonctionne le protocole?
Un système RFID se compose de deux éléments principaux: un tag (ou étiquette) et un lecteur. Le lecteur émet une onde radio. Lorsqu'un tag RFID se trouve à portée, il capte cette onde, l'utilise pour alimenter son circuit interne et renvoie son information stockée au lecteur.

## 5. Quels sont les versions et les caractéristiques?
La RFID peut être catégorisée selon différentes fréquences:
* **RFID basse fréquence (LF)**: 125 à 134 kHz. Portée courte.
* **RFID haute fréquence (HF)**: 13,56 MHz. Utilisé pour le paiement mobile et les billets de transport.
* **RFID ultra haute fréquence (UHF)**: de 856 MHz à 960 MHz. Portée plus longue, souvent utilisée pour la gestion des stocks.
* **RFID micro-onde**: 2,4 GHz ou plus. Portée la plus longue, mais consomme plus d'énergie.

## 6. Y a-t-il différents types?
Oui. Il existe principalement deux types de tags:
* **Actif**: Possède une source d'énergie interne, portée plus grande.
* **Passif**: N'a pas de source d'énergie propre. Il est activé par le signal du lecteur.

## 7. Comment une communication qui utilise ce protocole s'établit?
1. **Interrogation**: Le lecteur émet une onde radio à une fréquence spécifique.
2. **Activation**: Si un tag passif est à portée, il est alimenté par cette onde.
3. **Réponse**: Le tag envoie ses informations (souvent un identifiant unique) au lecteur.
4. **Traitement**: Le lecteur reçoit l'information et la traite, souvent en la relayant à une base de données ou un système centralisé.

## 8. Quels sont les failles de sécurité du protocole?
* **Eavesdropping**: Interception des données lors de la communication entre le tag et le lecteur.
* **Skiimming**: Lecture non autorisée d'un tag par un lecteur malveillant.
* **Spoofing**: Envoi de fausses informations à un lecteur.
* **Replay attacks**: Capture et retransmission d'une requête valide.

## 9. Comment sécuriser le protocole?
* **Cryptage**: Les données stockées sur le tag peuvent être cryptées.
* **Authentification mutuelle**: Assure que le tag et le lecteur sont authentiques avant d'échanger des informations.
* **Distance de fonctionnement réduite**: Réduire la portée pour minimiser la possibilité d'interceptions non autorisées.
* **Utilisation de tags protégés**: Certains tags peuvent être configurés pour devenir muets ou pour nécessiter une "clé" spécifique pour être lus.

En conclusion, la RFID est une technologie puissante et polyvalente avec une vaste gamme d'applications. Cependant, comme pour toute technologie, il est crucial d'en comprendre les avantages et les inconvénients, en particulier en matière de sécurité.