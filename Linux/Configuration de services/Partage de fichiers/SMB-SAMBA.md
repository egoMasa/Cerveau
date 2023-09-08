# Guide SMB/SAMBA

## SMB 
* Protocole qui permet de partager des fichiers, imprimantes et autre ressources réseau
* Principalement utilisé par des clients Windows

## Samba
* Version open source de SMB pour Unix et Linux

### 1) Installation 
1. Installer le paquet Samba
```
sudo apt update
sudo apt install samba samba-client
```
2. Configurer samba `/etc/samba/smb.conf`
```
[global]
...
min protocol = SMB2
max protocol = SMB3
...


[<Nom_Partage>]
   path = <chemin>
   available = yes
   valid users = <username>
   read only = no
   browsable = yes
   public = yes
   writable = yes

```
3. Définir mot de passe pour samba
```
sudo smbpasswd -a <username>
```
4. Créer le répertoire du partage
```
sudo mkdir -p <chemin>
sudo chown <username>:<username> <chemin>
sudo chmod 755 <chemin>
```
5. Redémarrer le service 
```
sudo systemctl restart smbd
```
### 2) Utilisation 
#### Windows
1. Ouvrez l'Explorateur de fichiers.
2. Dans la barre d'adresse, tapez
```
\\<ip_server>\<Nom_Partage>
```
#### Linux
1. Installer le client samba
```
sudo apt install smbclient
```
2. Lister les partages disponiles sur le serveur
```
smbclient -L //<ip_server> -U <username> -m SMB3
```
3. Se connecter à un partage
```
smbclient //<ip_server>/<Nom_Partage> -U <username>
```
* Liste des commandes
```
   * ls : Listez les fichiers et dossiers.
   * cd <directory> : Changez de répertoire.
   * pwd : Affichez le chemin du répertoire actuel.
   * get <file> : Téléchargez un fichier du serveur vers le client.
   * mget <pattern> : Téléchargez plusieurs fichiers correspondant au motif. Par exemple, mget *.txt téléchargera tous les fichiers .txt.
   * put <file> : Envoyez un fichier du client vers le serveur.
   * mput <pattern> : Envoyez plusieurs fichiers correspondant au motif.
   * mkdir <directory> : Créez un nouveau répertoire.
   * rmdir <directory> : Supprimez un répertoire (seulement s'il est vide).
   * rm <file> : Supprimez un fichier.
   * rename <oldname> <newname> : Renommez un fichier ou un répertoire.
   * exit ou quit : Quittez smbclient.`
```

### 3) Configuration avancée 
* Exemple d'un fichier de configuration
```
[global]
    workgroup = WORKGROUP
    server string = Mon Serveur Samba
    log file = /var/log/samba/log.%m
    max log size = 1000
    security = user
    passdb backend = tdbsam
    smb encrypt = required

# 1. Simple partage de fichiers
[MonPartage]
    path = /chemin/vers/partage
    browsable = yes
    read only = no
    valid users = user1, user2
    guest ok = no

# 2. Partage d'imprimante
[MonImprimante]
    path = /chemin/vers/spool
    browsable = yes
    guest ok = no
    printable = yes
    print ok = yes
    valid users = user1, user2

# 3. Serveur de domaine (PDC)
[netlogon]
    path = /chemin/vers/netlogon
    domain logons = yes
    domain master = yes
    browsable = no
    read only = yes
    os level = 65

# 4. Partage pour les invités
[PartageInvites]
    path = /chemin/vers/partage_invites
    browsable = yes
    read only = yes
    guest ok = yes


# Paramètres de sécurité courants
    map to guest = bad user
    guest account = nobody
    hosts allow = 192.168.1.
    hosts deny = 192.168.2.

```
#### Explications globale
* workgroup = WORKGROUP: Ceci définit le groupe de travail ou le domaine que le serveur Samba va rejoindre. WORKGROUP est le groupe de travail par défaut sur de nombreux réseaux, mais cela peut être modifié pour correspondre à votre configuration spécifique.

* server string = Mon Serveur Samba: Il s'agit d'une description du serveur qui sera visible par les clients lors de la navigation.

* log file = /var/log/samba/log.%m: Ceci définit le chemin du fichier de log pour le serveur Samba. %m sera remplacé par le nom NetBIOS du client, permettant un fichier de log distinct pour chaque client.

* max log size = 1000: Ceci définit la taille maximale du fichier de log en kilo-octets. Lorsque cette taille est atteinte, le fichier de log est renouvelé.

* security = user: Cette directive détermine le mode de sécurité qui sera utilisé pour les authentifications des utilisateurs. Dans ce mode, Samba demande un nom d'utilisateur et un mot de passe.

* passdb backend = tdbsam: Ceci spécifie le backend de la base de données des mots de passe. "tdbsam" utilise une base de données Trivial Database pour stocker les informations d'authentification.

* smb encrypt = required: Cela oblige le chiffrement des sessions SMB3 pour les communications entre le client et le serveur.

#### Explications de partage
* path: Ceci définit le chemin du système de fichiers vers le répertoire qui sera partagé.

* browsable: Si défini sur "yes", le partage sera visible lors de la navigation sur le réseau.

* read only: Si défini sur "yes", le partage sera en lecture seule. "no" permet l'écriture.

* valid users: Liste des utilisateurs qui ont le droit d'accéder à ce partage.

* guest ok: Si défini sur "yes", un accès anonyme (en tant qu'invité) est autorisé.

* printable et print ok: Ces deux directives sont utilisées pour définir un partage d'imprimante. Si définies sur "yes", elles indiquent que le partage est une imprimante.

* domain logons: Utilisé pour un contrôleur de domaine Samba. Si défini sur "yes", cela permet à Samba de fournir des services de connexion pour les clients du domaine.

* domain master: Si défini sur "yes", cela fait de Samba le maître de navigation pour le domaine.

* os level: Cette directive définit la priorité de Samba lors de l'élection du maître de navigation. Une valeur plus élevée donne à Samba une plus grande priorité.

* map to guest: Ceci détermine comment les utilisateurs non valides (ceux qui ne sont pas reconnus) sont traités. "bad user" signifie que tout utilisateur non reconnu sera traité comme un invité.

* guest account: Spécifie le compte d'utilisateur sous lequel les sessions d'invité seront exécutées. Habituellement, cela pointe vers un compte avec des privilèges très limités.

* hosts allow et hosts deny: Ces directives contrôlent l'accès au partage basé sur l'adresse IP du client. "hosts allow" spécifie les adresses IP autorisées et "hosts deny" celles qui sont interdites.

#### Paramètres de sécurité courants
##### Encryption :
* smb encrypt: définit le mode de chiffrement des sessions SMB3. Les valeurs possibles sont : disabled, enabled, required.
##### Authentification :
* map to guest: détermine comment les utilisateurs non valides sont traités. Les valeurs courantes sont "bad user" (cartographie des utilisateurs inconnus en tant qu'invités) et "never" (pas de cartographie).
* guest account: spécifie le compte d'utilisateur sous lequel les sessions d'invité sont exécutées.
##### Contrôle d'accès :
* hosts allow: spécifie les adresses IP ou les réseaux autorisés à accéder au partage.
* hosts deny: spécifie les adresses IP ou réseaux qui ne sont pas autorisés à accéder au partage.
