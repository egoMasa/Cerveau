# FTP 
Le protocole de transfert de fichiers (FTP) est un protocole réseau standard utilisé pour transférer des fichiers d'un hôte à un autre hôte sur un réseau basé sur le protocole TCP, tel qu'Internet. Développé à l'origine dans les années 1970, c'est l'un des premiers protocoles de transfert de fichiers entre ordinateurs et il reste largement utilisé aujourd'hui.

## Comment fonctionne le protocole FTP ?
Le protocole FTP fonctionne selon un modèle client-serveur, dans lequel un ordinateur joue le rôle de client (l'expéditeur ou le demandeur) et l'autre celui de serveur (le destinataire ou le fournisseur). Le client établit une connexion avec le serveur, généralement en fournissant un nom d'utilisateur et un mot de passe pour l'authentification, puis demande un transfert de fichiers.

Le protocole FTP utilise deux canaux distincts pour effectuer ses opérations :

* Le canal de contrôle : Ce canal est utilisé pour établir la connexion entre le client et le serveur et envoyer des commandes, telles que la spécification du fichier à transférer, le mode de transfert et la structure du répertoire.
* Canal de données : Ce canal est utilisé pour transférer les données du fichier entre le client et le serveur.

## Modes FTP
Le protocole FTP offre deux modes de transfert de fichiers :

* Le mode ASCII : Ce mode est utilisé pour transférer des fichiers texte. Il convertit les fins de ligne des fichiers transférés pour qu'elles correspondent au format utilisé sur le système de destination. Par exemple, si le fichier est transféré d'un système Unix vers un système Windows, les fins de ligne seront converties de LF (Unix) à CR+LF (Windows).
* Mode binaire : Ce mode est utilisé pour transférer des fichiers binaires, tels que des images, des fichiers audio et des exécutables. Aucune conversion des données n'est effectuée au cours du processus de transfert.
## Problèmes de sécurité liés au protocole FTP
Le protocole FTP pose des problèmes de sécurité importants, principalement parce qu'il a été conçu avant l'utilisation généralisée des mécanismes de cryptage et d'authentification. Voici quelques-uns de ces problèmes :

* Les noms d'utilisateur et les mots de passe sont transmis en texte clair, ce qui permet à quiconque d'intercepter les données de les consulter.
* Les données transférées entre le client et le serveur ne sont pas cryptées par défaut, ce qui les rend vulnérables aux écoutes clandestines.
* Le protocole FTP ne permet pas de valider l'identité d'un serveur, ce qui le rend vulnérable aux attaques de type "man-in-the-middle".