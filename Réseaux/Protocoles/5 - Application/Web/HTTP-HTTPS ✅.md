
# Guide HTTP-HTTPS

# I) Généralités
* Protocole de communication entre un navigateur et un serveur web
* Fonctionnement du protocole
	1. Connexion TCP du client vers le serveur sur port 80 ou 443
	2. Requête HTTP avec toutes les options
		* l'URL, 
		* la méthode 
			* GET : Obtenir l'information
			* POST : Envoyer l'information
			* PUT :  Mettre à jour l'information
			* DELETE : Supprimer de l'information
		* version du protocole 
		* en-têtes supplémentaires
	3. Réponse du serveur avec code correpondant au résultat + contenu si code 200
		* 200 : OK
		* 201 : Created
		* 401 : **Not Authorised**
		* 403 : **Forbidden**
		* 404 : **Page Not Found**
		* 503 : **Service Unavailable**
	1. Fermeture de la connexion de la part du client 
	2. Traitement du corps recu via le navigateur et affichage

# II) Exemple d'une communication
* Requête HTTP de la part du client 
```
GET / HTTP/1.1                         # Méthode GET et version de HTTP
Host: example.com                      # Le nom du site
User-Agent: Mozilla/5.0 Firefox/87.0   # Le navigateur que nous utilisons
Referer: https://example.com/          # L'URL de la ressource 
```
* Réponse du serveur web
```
HTTP/1.1 200 OK                        # Version de HTTP et code réponse
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html                # text/plain | text/plain | text/javascript | application/xml | image/jpeg | audio/mpeg | video/mp4 | ...
Content-Length: 98                     # Le nombre de données envoyés et à verifier à la reception


<html>
<head>
    <title>Hello</title>
</head>
<body>
    Tout va bien
</body>
</html>
```

# III) En-tête (headers)
* Données supplémentaires qu'on peut envoyer au serveur web lors d'une requête
* Elle ne sont pas requises mais souvent necessaire au bon fonctionnement d'un site
* En tête lors d'une requête
	1. Host : Quand serveur gère plusieurs site, sinon par défaut
	2. User-Agent : Navigateur et sa version
	3. Content-Length : La quantité de données à attendre dans la requête.
	4. Accept-Encoding :  Méthodes de compression prises en charge par le navigateur
	5. Cookie : Données envoyées au serveur pour mémoriser vos informations
* En tête lors d'une réponse
	1. Set-Cookie : Informations à stocker
	2. Cache-Control : Durée de stockage du contenu de la réponse dans le cache du navigateur avant de la demander à nouveau.
	3. Content-Type : type de données renvoyées
	4. Content-Encoding : Méthode utilisée pour compresser les données

# IV) Cookies
* Fichier texte qui stocke des informations de sessions et préférence sur un site web
* Permet les de mémoriser les identifiants, langues par exemple
* Le serveur génère cookies avec les paramètres du client, le client envoie le cookie au site quand il reviens pour retrouver ses paramètres
1. Création du cookie lors de la première visite, le serveur envoie les données de session via en tete "Set-Cookie"
2. Stockage des cookies sur le client avec date d'expiration via en-tete "Cookie", soit 
	* persistant : Durée réelle dans le temps (10 jours)
	* Session : Fermeture du navigateurs
3. Mise à jour des cookies où le serveur modifie le cookie et le renvoie au client
* Démonstration mise en place de cookie
1. Le client remplie un formulaire simple avec son nom 
```
POST / HTTP/1.1
Host: example.com
User-agent: Firefox/87.0
Content-Type: aaplication/form
Content-Length: 9

name=toto
```
2. Réception requête coté serveur
```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Set-Cookie: name=toto
```

## HTTPS

Pour répondre aux problèmes de sécurité posés par le protocole HTTP, le protocole HTTPS a été introduit comme alternative sécurisée. HTTPS utilise le cryptage pour garantir que les données transmises entre le client et le serveur sont confidentielles et ne peuvent pas être déchiffrées par un tiers.

HTTPS utilise soit SSL (Secure Sockets Layer), soit TLS (Transport Layer Security) pour crypter les données. Ces protocoles cryptographiques assurent une sécurité de bout en bout, garantissant l'intégrité et l'authentification des données. Lorsque vous visitez un site web doté du protocole HTTPS, vous pouvez être certain que vos informations sont transmises en toute sécurité.

Pour mettre en œuvre le protocole HTTPS, les sites web doivent obtenir un certificat SSL/TLS auprès d'une autorité de certification (AC) de confiance. Ce certificat authentifie l'identité du site web et permet d'établir une connexion sécurisée entre le client et le serveur.