# Guide sur FTP-FTPS-SFTP

# 1) Différence entre FTP, FTPS et SFTP 
1. FTP (File Transfer Protocol) :
* Fonctionnement : FTP est un protocole standard de transfert de fichiers entre un client et un serveur sur un réseau informatique. Il utilise deux canaux séparés pour la communication : un canal de commande (port 21 par défaut) et un canal de données.
* Sécurité : FTP ne chiffre pas ses données, ce qui signifie que toutes les données, y compris les noms d'utilisateur, les mots de passe et les fichiers, sont transmis en clair. Cela peut être un risque pour la sécurité, surtout sur les réseaux non sécurisés.
Usage : Bien qu'il soit largement utilisé, FTP est de moins en moins privilégié en raison de ses faiblesses en matière de sécurité.

2. FTPS (FTP Secure) :
* Fonctionnement : FTPS est une extension du protocole FTP qui ajoute une prise en charge du chiffrement SSL/TLS. Comme FTP, il utilise également deux canaux : un canal de commande et un canal de données.
* Sécurité : FTPS offre une sécurité substantielle en chiffrant les données qui sont transmises entre le client et le serveur. Ceci garantit que les noms d'utilisateur, les mots de passe et les fichiers ne peuvent pas être interceptés en clair.
* Usage : FTPS est utilisé lorsque la sécurité est une priorité. Il est particulièrement important lorsque les données sensibles doivent être transmises sur un réseau.

3. SFTP (SSH File Transfer Protocol) :
* Fonctionnement : SFTP est un protocole de transfert de fichiers qui fait partie de la suite SSH (Secure Shell Protocol). Contrairement à FTP/FTPS, SFTP utilise un seul canal (port 22 par défaut) pour transmettre à la fois les commandes et les données, ce qui le rend plus efficace en termes de gestion du réseau.
* Sécurité : SFTP est sécurisé et utilise le protocole SSH pour chiffrer les données pendant le transfert. Comme SSH est un protocole sécurisé, SFTP bénéficie également d'une forte authentification et de l'intégrité des données.
* Usage : SFTP est largement utilisé pour transférer des fichiers de manière sécurisée sur Internet en raison de ses fortes capacités de chiffrement et d'authentification.

* Résumé des différences :

FTPS et SFTP sont tous deux des protocoles sécurisés pour le transfert de fichiers, mais ils sont basés sur des technologies différentes. FTPS est une extension sécurisée de FTP, tandis que SFTP est un sous-système de SSH.
FTPS utilise le même mécanisme que FTP mais ajoute une couche de sécurité avec SSL/TLS.
SFTP, contrairement à FTP/FTPS, utilise un seul canal pour transmettre les données et les commandes, et il est basé sur le protocole SSH, pas FTP.
FTP est le moins sécurisé des trois, car il ne chiffre pas les données transmises.

# 2) Spécificité de FTP 
* FTP, le File Transfer Protocol, fonctionne en utilisant deux canaux entre le client et le serveur : un canal de commande et un canal de données.

* Canal de commande : Il est utilisé pour envoyer des commandes entre le client et le serveur (comme LIST, RETR, STOR, etc.) et est établi dès que le client se connecte au serveur FTP. Par défaut, ce canal utilise le port TCP 21.

* Canal de données : Il est utilisé pour envoyer les données réelles entre le client et le serveur (comme les fichiers et les listes de répertoires). Ce canal est établi chaque fois qu'une commande nécessitant le transfert de données est initiée.

* FTP a deux modes pour établir ce canal de données : Actif (Active) et Passif (Passive).

1. Mode Actif :

* Dans le mode actif, après l'établissement du canal de commande, le client écoute sur un port aléatoire pour la connexion de données du serveur.
Le client informe le serveur du port sur lequel il écoute via le canal de commande.
Le serveur initie alors une connexion de données depuis son port 20 vers le port que le client a spécifié.

2. Mode Passif :

* En mode passif, c'est le serveur qui ouvre un port aléatoire pour la connexion de données, et informe le client du port à utiliser lors de l'établissement de la connexion de données.
Le client initie alors la connexion de données vers le port spécifié par le serveur.
Le mode passif est utile lorsque le client est derrière un pare-feu ou un NAT et ne peut pas accepter de connexions entrantes sur des ports aléatoires.

3. Pourquoi utiliser le Mode Passif ?

* Sécurité et Compatibilité Firewall/NAT : Le mode passif est devenu plus courant car il joue mieux avec les pare-feu et les NAT (Network Address Translation). Dans le mode passif, toutes les connexions (commande et données) sont initiées par le client, ce qui est généralement plus facile à gérer avec les pare-feu et les NAT.

* Contrôle des Plages de Ports : En mode passif, le serveur informe le client du port (ou de la plage de ports) à utiliser pour la connexion de données. Cette plage de ports peut être configurée par l'administrateur du serveur FTP, ce qui est utile pour configurer des règles de pare-feu

# SECTION FTP

## Scénario 1 : Répertoire privé pour chaque utilisateur
1. Installer le paquet "vsftpd"
```
apt-get install vsftpd
```
2. Créer un utilisateur local sur le serveur
```
sudo adduser <username>
sudo passwd <username> # Modifier password si besoin
```
2. Configurer le fichier `/etc/vsftpd.conf`
```
nano /etc/vsftpd.conf

>local_enable=YES
>write_enable=YES
>chroot_local_user=YES
>allow_writeable_chroot=YES
>user_sub_token=$USER
>local_root=/home/$USER/ftp
```
3. Redémarrer vsftpd
```
systemctl restart vsftpd
```
## Scénario 2 : Répertoire partagé pour un groupe d'utilisateurs
1. Créer un groupe et un répertoire partagé
```
sudo addgroup ftpshared
sudo mkdir /var/ftp/shared
sudo chown root:ftpshared /var/ftp/shared
sudo chmod 770 /var/ftp/shared
```
2. Ajouter les utilisateurs au groupe
```
sudo usermod -a -G ftpshared user1
sudo usermod -a -G ftpshared user2
```
3. Configurer le fichier vsftpd.conf
```
user_config_dir=/etc/vsftpd/userconf
```
4. Créer un repertoire pour les configurations utilisateurs (refaire pour chaque users)
```
mkdir /etc/vsftpd/userconf
touch /etc/vsftpd/userconf/user1
nano /etc/vsftpd/userconf/user1

> local_root=/var/ftp/shared
```
5. Redémarrer vsftpd
```
systemctl restart vsftpd
```

### Explications d'options et lignes du fichier de configuration

#### Générales
* anonymous_enable=NO : Cette option désactive les connexions anonymes.
* local_enable=YES : Cette option permet aux utilisateurs locaux de se connecter au serveur FTP.
* write_enable=YES : Cette option autorise les utilisateurs à écrire sur le serveur (c'est-à-dire à télécharger des fichiers).
* chroot_local_user=YES : Cette option enferme les utilisateurs dans leur répertoire d'accueil, ce qui signifie qu'ils ne peuvent pas accéder aux fichiers en dehors de leur propre répertoire.
* userlist_enable=YES : Si activée, vsftpd appliquera des règles d'accès basées sur les fichiers user_list et/ou vsftpd.user_list.
* userlist_deny=NO : Si cette option est définie à NO, alors les utilisateurs listés dans les fichiers user_list ou vsftpd.user_list sont autorisés à se connecter, et tous les autres utilisateurs sont refusés. Si elle est définie à YES, les utilisateurs listés sont refusés et les autres sont autorisés.
* Pour créer une liste d'utilisateur autorisés, ajouter un nom d'utilisateur par ligne dans le fichier `/etc/vsftpd.user_list`
```
nano /etc/vsftpd.user_list
```
#### Sécurité
* ssl_enable=YES : Si activé, les utilisateurs peuvent se connecter en utilisant le protocole FTPS, qui est une version sécurisée du FTP. Vous devrez également spécifier un fichier de certificat et de clé privée avec les directives rsa_cert_file et rsa_private_key_file.
* allow_anon_ssl=NO : Ne permet pas aux utilisateurs anonymes de se connecter via FTPS.
* force_local_data_ssl=YES et force_local_logins_ssl=YES : Ces options forcent les utilisateurs à se connecter via FTPS, ce qui assure que les données et les identifiants sont transmis de manière sécurisée.

#### Controler les accès
* anon_upload_enable=NO : Si vous avez autorisé les connexions anonymes, cette option empêche ces utilisateurs d'envoyer des fichiers sur le serveur.
* anon_mkdir_write_enable=NO : Cette option empêche les utilisateurs anonymes de créer des répertoires.
* no_anon_password=YES : Si vous permettez les connexions anonymes, cette option permet de ne pas demander de mot de passe pour ces utilisateurs.

#### Journaliser les audits
* xferlog_enable=YES : Cette option active le journal des transferts de vsftpd. Cela peut être utile pour surveiller qui télécharge ou téléverse des fichiers sur votre serveur FTP.

### FTPS
* Installer OpenSSL pour créer un certificat et une clé privée pour le chiffrement SSL/TLS
```
sudo apt-get install openssl
```
* Créer un certificat auto-signé et une clé privée
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.key -out /etc/ssl/certs/vsftpd.crt
```
* Configurer vstpd pour utiliser SSL/TLS
```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
rsa_cert_file=/etc/ssl/certs/vsftpd.crt
rsa_private_key_file=/etc/ssl/private/vsftpd.key

```
* Configurer le mode passif 
```
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000

```
10. Redémarrer le service vsftpd
```
sudo systemctl restart vsftpd
```
10. Ouvrir le port FTP sur le pare-feu (ici ufw)
```
sudo ufw allow 21/tcp
sudo ufw allow 40000:50000/tcp # Si mode passif (FTPS)

```

## 2) Utilisation de FTP
* Liste des actions possibles cotés client
  1. Téléchargement de fichiers : Les clients peuvent télécharger des fichiers depuis le serveur FTP vers leur propre système.
  2. Upload de fichiers : Les clients peuvent également envoyer des fichiers de leur système au serveur FTP.
  3. Gestion de fichiers et de répertoires : Les clients peuvent créer, supprimer et naviguer dans les répertoires, et également déplacer, supprimer et renommer les fichiers.

* Se connecter à un serveur FTP
1. Sur navigateur
```
ftp://<ip>
```
2. Via CLI
```
ftp <Adresse_IP_du_Serveur>
```
3. Via client FTP (FileZilla, Cyberduck,...)
```
Hôte : <Adresse_IP_du_Serveur>
Type : FTP ou FTPS (pour une connexion sécurisée)
Nom d'utilisateur : Votre nom d'utilisateur
Mot de passe : Votre mot de passe
Port : 21 (par défaut pour FTP) ou le port que vous avez configuré
```

* Liste des commandes à connaitre
```
  * open <host> : Ouvrir une connexion à un serveur FTP
  * user <username> : Spécifier le nom d'utilisateur
  * get <filename> : Télécharger un fichier du serveur
  * put <filename> : Envoyer un fichier vers le serveur
  * ls : Lister les fichiers du répertoire courant sur le serveur
  * cd <directory> : Changer de répertoire sur le serveur
  * mkdir <directory> : Créer un répertoire sur le serveur
  * rmdir <directory> : Supprimer un répertoire sur le serveur
  * delete <filename> : Supprimer un fichier sur le serveur
  * rename <oldname> <newname> : Renommer un fichier sur le serveur
  * quit : Fermer la connexion FTP et quitter le client FTP
```

# SECTION SFTP

## Scénario 1 : Répertoire privé pour chaque utilisateur
1. Installer le paquet openssh-server qui inclut SFTP
```
sudo apt-get install openssh-server
```
2. Créer les utilisateurs
```
sudo adduser user1
sudo adduser user2
```
3. Configurer le fichier /etc/ssh/sshd_config
```
nano /etc/ssh/sshd_config
```
4. Ajouter les lignes 
```
Match User user1,user2
    ChrootDirectory /home/%u
    ForceCommand internal-sftp
    AllowTCPForwarding no
    PasswordAuthentication yes

```
5. Redémarrer le service
```
sudo systemctl restart ssh
```
## Scénario 2 : Répertoire partagé par un groupe d'utilisateur
1. Créer un groupe et le repertoire partagé
```
sudo addgroup sftpshared
sudo mkdir -p /var/sftp/shared
sudo chown root:sftpshared /var/sftp/shared
sudo chmod 770 /var/sftp/shared
```
2. Ajouter les utilisateur au groupe
```
sudo usermod -a -G sftpshared user1
sudo usermod -a -G sftpshared user2
```
3. Configurer le fichier
```
Match Group sftpshared
    ChrootDirectory /var/sftp/shared
    ForceCommand internal-sftp
    AllowTCPForwarding no
    PasswordAuthentication yes
```
4. Redémarrer le service
```
sudo systemctl restart ssh
```


## 2) Amélioration de la sécurité (/etc/ssh/sshd_config)
### 1. Utilisé la connexion via cléf uniquement
* Ajouter/Modifier la ligne du fichier de configuration
```
PasswordAuthentication no
```
* Sur le client, générer un paire de clés (l'emplacement par défaut .ssh/id_rsa)
```
ssh-keygen -t rsa -b 4096
```
* Transférer la cléf publique (id_rsa.pub) vers le serveur dans l'emplacement (~/.ssh/authorized_keys)
```
ssh-copy-id <user>@<ip_serveur>
scp id_rsa.pub <user>@<ip_serveur>
```
* Sur serveur, verifie la configuration du service SSH
```
sudo nano /etc/ssh/sshd_config

PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
PasswordAuthentication no
```
* Redemarrer le service et tester la connexion depuis la connexion cliente
```
sudo systemctl restart sshd (serveur)
ssh <user>@<ip>
```
### Autres 
2. Changer le port SSH
```
Port 2222
sudo ufw allow 2222/tcp
```
3. Désactiver la connexion directe en tant que root via SSH
```
PermitRootLogin no
```
4. Spécifier exactement quels utilisateurs sont autorisés à se connecter via SSH
```
AllowUsers sftpuser1 sftpuser2
DenyUsers user1 user2
```
5. Controler les groupes qui peuvent se connecter
```
AllowGroups sftpgroup
DenyGroups group1 group2
```
6. Limiter les connexions SSH aux adresses IP spécifiques
```
AllowUsers sftpuser@192.168.1.*
```
7. Forcer une certaine cléf pour un user spécifique
```
Match User sftpuser
AuthorizedKeysFile /path/to/sftpuser_key.pub
```
9. Configurer un taux limite pour les tentatives de connexion
```
MaxAuthTries 3
MaxSessions 10
```
10. Redémarrer le service
```
sudo systemctl restart sshd
```
## 3) Utilisation de SFTP
### Linux 
1. Se connecter au serveur
```
sftp <username>@<ip/domaine>
```
2. Utiliser les commandes
* ls : Lister les fichiers du répertoire distant
* lls: Lister les fichiers du répertoire local
* get file.txt : Télécharger file.txt du serveur vers le client
* put file.txt : Envoyer file.txt du client vers le serveur
* cd directory/ : Changer le répertoire courant sur le serveur distant
* lcd directory/ : Changer le répertoire courant sur le client local
* mkdir directoryname : Créer un répertoire sur le serveur distant
* rmdir directoryname : Supprimer un répertoire sur le serveur distant
* bye ou exit: Quitter la session SFTP

### Windows 
* On utilise [WinSCP](https://winscp.net/eng/download.php)
