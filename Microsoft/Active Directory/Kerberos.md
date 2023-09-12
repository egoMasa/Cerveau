
* Kerberos est un protocole d'authentification par défaut pour les utilisateurs et ressources AD
* Kerberos utilise un système de ticket plutot que de mot de passe

# Les acteurs de Kerberos 
1. **Client** : L'utilisateur ou l'ordinateur qui demande l'accès à une ressource.
2. **Ressource (ou Service)** : Le serveur qui héberge le service ou la ressource à laquelle l'utilisateur souhaite accéder.
3. **Serveur d'Authentification (AS) et Serveur de Distribution de Tickets (TGS)** : Ces composants, souvent situés sur la même machine, forment le Key Distribution Center (KDC). C'est le cœur de l'infrastructure Kerberos, responsable de l'authentification des clients et de la délivrance des tickets d'accès pour les ressources.

# Exemple d'un utilisateur qui veut accéder à une ressource protégé Kerberos
1. Le client tente d'accéder à une ressource.
2. La ressource indique que l'authentification Kerberos est nécessaire.
3. Le client communique avec le AS (Authentication Service) du KDC (Serveur Kerberos).
	1. Le client envoie une demande de Ticket Granting Ticket (TGT) au AS.
	2. Le AS vérifie si le client est enregistré dans Active Directory. Si c'est le cas, il génère un TGT, chiffré avec la clé secrète du TGS (Ticket Granting Service, une composante du KDC).
	3. Le client reçoit le TGT chiffré. Pour accéder à une ressource spécifique, le client présente ce TGT au TGS et demande un Service Ticket (ST) pour cette ressource.
	4. Le TGS déchiffre le TGT pour s'assurer de l'authenticité du client. Si le TGT est valide, le TGS génère un ST pour le client, chiffré avec la clé secrète de la ressource/service désiré.
4. Le client présente ce ST à la ressource pour demander l'accès.
5. La ressource déchiffre le ST avec sa propre clé secrète. Si le déchiffrement est réussi et que le ticket est valide, l'accès est accordé selon les conditions du ST.
## Précisions sur le ST :
* Le Service Ticket (ST) contient des informations telles que :
	- le nom de l'utilisateur
	- la durée de validité du ticket
	- une clé de session pour chiffrer la communication entre la ressource et le client.
## Précisions sur le chiffrement
- Il n'y a pas de concept de "clé publique" et "clé privée" pour Kerberos comme dans les systèmes basés sur RSA. Kerberos utilise des clés secrètes symétriques. Donc, lorsque l'on dit "chiffré avec la clé de X", c'est une clé secrète unique à X.
- Le client ne déchiffre jamais le TGT. Seul le TGS peut le faire. C'est une des sécurités fondamentales de Kerberos : le client prouve son identité sans jamais connaître la clé secrète du TGS.