## **Protocole de Contrôle de Transmission (TCP)**

### **Introduction**:
TCP est l'un des principaux protocoles de communication utilisés dans les réseaux IP d'Internet. Il appartient à la couche de transport du modèle OSI et permet une communication fiable entre deux hôtes.

### **Caractéristiques principales**:

1. **Orienté connexion**: Avant que la communication ne commence, une connexion est établie entre les deux hôtes.
2. **Fiable**: TCP fournit des mécanismes pour assurer la livraison sans erreur des données.
3. **Flux orienté**: TCP considère les données comme un flux continu de bytes, et non comme des messages distincts.
4. **Contrôle de flux**: Il emploie le mécanisme de fenêtrage pour éviter la congestion.

### **Composants clés**:

1. **Segments**: Les unités de transmission dans TCP sont appelées segments.
2. **Ports**: Les applications sont identifiées par des ports TCP pour assurer la livraison des données à la bonne application.

### **Processus de connexion (3-way handshake)**:

1. **SYN**: Le client veut établir une connexion et envoie un segment avec le drapeau SYN activé.
2. **SYN, ACK**: Le serveur répond avec un segment ayant à la fois les drapeaux SYN et ACK activés.
3. **ACK**: Le client reconnaît la réponse du serveur et la connexion est établie.

### **Fermeture de la connexion (4 étapes)**:

1. Le client ou le serveur envoie un segment avec le drapeau FIN.
2. L'autre partie accuse réception de la fin avec un ACK.
3. Cette autre partie envoie ensuite son propre segment FIN.
4. La première partie accuse réception du FIN avec un ACK, terminant ainsi la connexion.

### **Contrôle de flux**:

TCP utilise un mécanisme de fenêtrage pour contrôler le flux de données. La "taille de fenêtre" détermine combien de données peuvent être envoyées avant de nécessiter un accusé de réception.

### **Contrôle de la congestion**:

TCP utilise plusieurs algorithmes (tels que Slow Start, Congestion Avoidance) pour éviter ou traiter la congestion dans le réseau.

### **Erreurs et retransmissions**:

Si un segment n'est pas accusé réception dans un certain délai (timeout), TCP le retransmet.

### **Numéros de séquence et accusés de réception**:

Chaque byte de données a un numéro de séquence. Les accusés de réception (ACKs) sont utilisés pour confirmer la réception de segments.

### **Options TCP**:
TCP a plusieurs options qui peuvent être utilisées pour ajuster le comportement par défaut. Par exemple, le "Maximum Segment Size" (MSS) est une option qui spécifie la plus grande quantité de données que peut contenir un segment.

### **Commandes utiles pour diagnostiquer et monitorer TCP (sur Unix-like systèmes)**:
- `netstat`: Affiche les connexions réseau, tables de routage, statistiques d'interface, connexions masquées, et états des membres multicast.
- `tcpdump`: Un analyseur de paquets pour capturer et afficher le trafic TCP/IP.

### **Détails des En-têtes TCP**:

- **Numéros de Port**: Le port source (16 bits) et le port de destination (16 bits) identifient les processus d'extrémité de la communication.
- **Numéros de Séquence**: Utilisé pour organiser et ordonner les paquets reçus.
- **Numéro d'Accusé de Réception**: Spécifie le prochain numéro de séquence que l'expéditeur du segment attend.
- **Longueur de l'En-tête**: Indique la longueur de l'en-tête TCP en mots de 32 bits.
- **Drapeaux (Flags)**: Ces bits spécifient certaines fonctions à effectuer (SYN, ACK, FIN, RST, URG, PSH).
- **Taille de la Fenêtre**: Spécifie le nombre de bytes que le récepteur est actuellement prêt à recevoir.
### **Sécurité avec TCP**:
- **TCP SYN Flood Attack**: Une attaque où le demandeur envoie une succession de demandes de connexion SYN, mais n'envoie jamais les accusés de réception ACK. Cela peut saturer les ressources de la victime.
- **Séquence Number Prediction Attack**: Un attaquant peut intercepter la communication si les numéros de séquence peuvent être prédits.
### **Nuances et Aspects Particuliers**:

- **Time_Wait**: Lorsqu'une connexion est fermée, elle reste dans l'état `TIME_WAIT` pendant un certain temps pour s'assurer que tous les paquets sont reçus et que l'autre extrémité est informée de la fermeture.
- **Sélection de la Taille Maximale des Segments (MSS)**: Permet à TCP d'indiquer la taille maximale des paquets qu'il souhaite recevoir.
- **TCP Timestamps**: Utilisé pour améliorer le calcul du délai d'attente pour la retransmission.
- **Options TCP Window Scale**: Permet d'utiliser une fenêtre plus grande que ce qui est autorisé par le champ de la fenêtre de 16 bits.

### **Optimisations et Algorithmes**:

1. **Fast Retransmit**: Au lieu d'attendre un délai d'expiration pour retransmettre un paquet perdu, TCP peut le faire si trois accusés de réception dupliqués sont reçus.
2. **Fast Recovery**: Après une retransmission rapide, évite de réduire la fenêtre de congestion à une seule MSS.
3. **Algorithmes de Contrôle de la Congestion**:
    - **Slow Start**: Augmente la fenêtre de congestion de manière exponentielle jusqu'à un seuil.
    - **Congestion Avoidance**: Augmente la fenêtre de congestion de manière linéaire après avoir atteint le seuil.
    - **Tail Drop**: Lorsque la file d'attente est pleine, les paquets suivants sont supprimés.
    - **Random Early Detection (RED)**: Supprime les paquets de manière aléatoire avant que la file d'attente ne soit pleine pour signaler la congestion.
    - **Explicit Congestion Notification (ECN)**: Permet aux routeurs d'indiquer la congestion sans supprimer de paquets.
### **Résumé**:
TCP est un protocole essentiel pour Internet, fournissant une communication fiable entre deux hôtes. Il a des mécanismes pour contrôler le flux de données, éviter la congestion, et garantir que les données sont livrées sans erreur. En comprenant les détails de son fonctionnement, on peut mieux concevoir, dépanner, et optimiser les réseaux.
