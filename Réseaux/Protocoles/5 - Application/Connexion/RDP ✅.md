# Guide RDP

Le Protocole de Bureau à Distance (RDP), développé par Microsoft, est un protocole propriétaire qui permet aux utilisateurs de se connecter à un ordinateur distant via un réseau et d'accéder à ses ressources et de les contrôler comme s'ils étaient physiquement devant cet ordinateur. Ceci est particulièrement utile pour les personnes qui travaillent à distance, gèrent des serveurs ou résolvent des problèmes sur un autre ordinateur.

### **Comment fonctionne RDP**

RDP utilise une architecture client-serveur. L'ordinateur distant auquel on accède agit comme un serveur, tandis que l'ordinateur de l'utilisateur agit comme un client. Le client établit une connexion avec le serveur pour accéder à ses ressources, telles que l'affichage, le clavier, la souris et autres périphériques.

Le protocole fonctionne principalement sur le port standard du Protocole de Contrôle de Transmission (TCP) 3389, bien que cela puisse être personnalisé. Il utilise aussi le Protocole de Datagramme Utilisateur (UDP) pour fournir un canal de communication plus robuste et tolérant aux erreurs.

### **Caractéristiques de RDP**

- **Support multiplateforme** : Bien que développé par Microsoft, des clients RDP sont disponibles pour diverses plateformes, notamment Windows, macOS, Linux, et même des appareils mobiles tels qu'Android et iOS.

- **Connexion sécurisée** : RDP peut offrir un chiffrement et une authentification pour sécuriser la connexion entre le client et le serveur, garantissant ainsi que les données transmises sur le réseau restent confidentielles et protégées contre les accès non autorisés.

- **Ajustement dynamique de la résolution** : RDP peut adapter la résolution d'écran de l'ordinateur distant pour l'adapter à l'écran du client, offrant ainsi une meilleure expérience utilisateur.

- **Partage du presse-papiers** : RDP permet de copier et coller du contenu entre l'ordinateur local et l'ordinateur distant.

- **Partage d'imprimantes et de fichiers** : Les utilisateurs peuvent accéder et imprimer des fichiers de leur ordinateur local vers l'ordinateur distant et vice versa.

### **Considérations de sécurité**

Bien que RDP soit populaire et utile, il présente certaines préoccupations en matière de sécurité. Les risques courants comprennent :

- **Accès non autorisé** : Si un attaquant réussit à accéder à une session RDP, il pourrait compromettre et contrôler l'ordinateur distant.

- **Attaques par force brute** : Les attaquants peuvent utiliser des techniques de force brute pour deviner les identifiants de connexion, surtout si le serveur a une politique de mot de passe faible.

- **Vulnérabilités** : Étant un protocole propriétaire, RDP peut être sujet à des vulnérabilités pouvant conduire à des violations de système.

Pour atténuer ces risques, vous devriez :

- Utiliser des mots de passe forts et uniques pour les comptes RDP et envisager de mettre en œuvre une authentification à deux facteurs.
  
- Limiter l'accès RDP à des adresses IP spécifiques ou à des Réseaux Privés Virtuels (VPN) pour réduire l'exposition.
  
- Appliquer régulièrement des correctifs de sécurité pour garder RDP à jour et minimiser le risque d'exploits.

- Utiliser l'authentification au niveau du réseau (NLA) pour offrir une couche de sécurité supplémentaire.