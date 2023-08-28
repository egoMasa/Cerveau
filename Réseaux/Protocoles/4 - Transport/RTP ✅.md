## **1. Introduction :**

* **RTP (Real-time Transport Protocol)** est un protocole de la couche de transport conçu spécifiquement pour les applications nécessitant la livraison en temps réel de données, comme l'audio et la vidéo.
* RTP est une norme établie par l'IETF (Internet Engineering Task Force) pour la transmission efficace de données audio et vidéo sur les réseaux IP. En plus de gérer les données en temps réel, il gère également les problèmes tels que la perte de paquets, le décalage et l'ordre des paquets.
## **2. Architecture :**

- **RTP** : Transporte des flux de données en temps réel.
	- Il gère la séquence de paquets, le moment où ils sont générés, l'identification des flux de médias, etc.
- **RTCP (Real-time Transport Control Protocol)** : Partenaire de surveillance d'RTP
	- Fournit des statistiques sur la qualité du transfert et des informations sur la session.
		- **Rapports sur la qualité de la réception**.
		- **Identification de la source**.
		- **Association de plusieurs flux**.
		- **Estimation de la bande passante pour RTCP**.
	- Il n'est pas obligatoire, mais fortement recommandé pour améliorer la qualité de la session

## Différence entre TCP/UDP/RTP
- **TCP** est comme un service postal qui garantit la livraison et assure que les lettres (paquets) sont lues dans l'ordre d'arrivée.
- **UDP** est comme jeter un message en bouteille dans l'océan. Il n'y a aucune garantie qu'il sera reçu, mais c'est rapide.
- **RTP** est comme une chaîne de télévision en direct. Si vous manquez une seconde de l'émission (perte de paquet), vous ne pouvez pas la récupérer, mais l'émission (flux) continue.
## **3. Structure de l'en-tête RTP :**

- **Version (2 bits)** : Indique la version du protocole.
- **Padding (P) (1 bit)** : Indique si des octets de bourrage sont ajoutés à la fin du paquet RTP.
- **Extension (X) (1 bit)** : Indique la présence d'un en-tête d'extension.
- **CSRC Count (CC) (4 bits)** : Nombre d'identifiants CSRC suivant l'en-tête fixe.
- **Marker (M) (1 bit)** : Interprétation spécifique au profil.
- **Payload Type (PT) (7 bits)** : Identifie le format du contenu RTP et détermine son interprétation par l'application.
- **Sequence Number (16 bits)** : Numéro de séquence incrémenté de un pour chaque paquet RTP envoyé.
- **Timestamp (32 bits)** : Donnée propre à chaque paquet, reflétant l'instant de génération ou d'échantillonnage du premier octet du paquet.
- **SSRC (32 bits)** : Identifie la source de la synchronisation.
- **CSRC (32 bits, optionnel)** : Identifie les sources contributrices pour le payload mélangé.

## **4. Caractéristiques :**

- **Multiplexage** : RTP supporte le multiplexage de plusieurs flux de données sur une seule connexion de transport.
- **Payload Type Identification** : Pour identifier le type de codage des médias.
- **Numérotation de Séquence** : Permet la détection des paquets perdus.
- **Synchronisation temporelle** : Pour la synchronisation des flux de données parallèles.
- **Rapports sur la qualité de la réception**: Informations sur la qualité des données reçues, y compris la fraction de paquets perdus et le délai de transmission.
- **Identification de la source**: Les rapports RTCP incluent également des informations sur l'expéditeur, y compris le SSRC et d'autres informations pouvant être utilisées pour identifier la source.
- **Association de plusieurs flux**: Par exemple, un flux vidéo peut être associé à plusieurs flux audio dans une conférence.
- **Estimation de la bande passante pour RTCP**: Pour éviter de surcharger le réseau, RTCP utilise généralement un faible pourcentage (typiquement 5%) de la bande passante totale.

## **6. Sécurité avec RTP :**

- **SRTP (Secure Real-time Transport Protocol)** : Une variante qui offre un chiffrement pour protéger les données, ainsi qu'une authentification pour assurer l'intégrité des paquets.
- **Négociation des clés**: Avant de pouvoir chiffrer les données, les participants doivent convenir d'une clé. Cette négociation se fait généralement en dehors de RTP/RTCP, par exemple avec le protocole SIP (Session Initiation Protocol) utilisant des mécanismes comme DTLS (Datagram Transport Layer Security).

## **7. Applications courantes :**

- **Téléphonie sur IP (VoIP)** : Pour le transport de la voix sur des réseaux IP.
- **Vidéoconférence** : La combinaison d'audio, de vidéo et parfois de données partagées.
- **Streaming média** : Où le contenu est diffusé en temps réel, comme les actualités ou les événements sportifs.

## **8. Problèmes et défis :**

- **Latence** : La livraison en temps réel signifie que les données doivent être livrées rapidement. Toute latence excessive peut rendre le contenu inutilisable.
- **Perte de paquets** : Les paquets perdus peuvent provoquer des artefacts audibles ou visibles. Certains codecs peuvent compenser, mais une perte excessive peut être problématique.

## **9. Optimisations :**

- **Buffering** : Les tampons peuvent aider à gérer les délais, mais augmentent également la latence.
- **FEC (Forward Error Correction)** : En envoyant des données redondantes, vous pouvez permettre la reconstruction de paquets perdus.
- **Adaptation du débit** : En ajustant la qualité (et donc le débit) du média, vous pouvez adapter le flux aux conditions actuelles du réseau.

## **10. Conclusion :**

RTP est essentiel pour la livraison en temps réel de contenus multimédias. Comprendre sa structure, son fonctionnement et ses défis est crucial pour implémenter des applications de communication en temps réel efficaces. Alors que RTP se charge de la livraison, RTCP fournit des retours importants sur la qualité, faisant des deux un duo puissant pour gérer les médias en temps réel.

