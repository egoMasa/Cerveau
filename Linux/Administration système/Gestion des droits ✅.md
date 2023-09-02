# Sommaire 
* Attribution des droits avec chmod
* Gestion de propriétés avec chown et chgrp
* Elevation de privilèges avec sudo
* su
* Fichiers de gestion utilisateurs
# Attribution des droits avec chmod

## 1. **Différents droits**
- **r** = lire
- **w** = écrire (créer, modifier, supprimer)
- **x** = exécuter (pour un script ou un programme) ou parcourir (pour un répertoire)

**Afficher les droits d'un fichier/répertoire**:
```
(machine)root# ls -l
````
Les droits peuvent être affichés sous forme de lettres (r, w, x) pour l'utilisateur (propriétaire du fichier), le groupe et les autres utilisateurs.

## 2. **Notation octale** :
- **7** = r, w, x
- **6** = r, w
- **5** = r, x
- **4** = r
- **3** = w, x
- **2** = w
- **1** = x
- **0** = aucun droit

## 3. Commandes de modifications
* Pour changer les droits d'un fichier ou d'un répertoire, utilisez `chmod` avec la notation octale ou symbolique.
````
(machine)root# chmod XXX fichier/repertoire
````
* Ou en notation symbolique:
````
(machine)root# chmod u=rwx,g=rx,o=rx fichier/repertoire
````

# Gestion de propriétés avec chown et chgrp
## **1. Utilisateur (Owner/Propriétaire) et Groupe**
- **Utilisateur (Owner/Propriétaire)** : L'utilisateur propriétaire d'un fichier ou d'un répertoire est généralement celui qui l'a créé. Cet utilisateur a des droits spécifiques sur le fichier ou le répertoire, qui peuvent différer de ceux accordés aux autres utilisateurs du système.
    
- **Groupe** : En plus de l'utilisateur propriétaire, un fichier ou un répertoire appartient également à un groupe. Les membres de ce groupe peuvent se voir accorder des droits distincts de ceux du propriétaire ou des autres utilisateurs.
## **2. Distinguer propriétaire et groupe**
La distinction entre propriétaire et groupe permet une flexibilité dans la gestion des droits. Par exemple :

- Un utilisateur peut vouloir partager un fichier avec un groupe de travail spécifique, mais pas avec tous les autres utilisateurs du système.
- Un administrateur peut vouloir accorder des droits spécifiques à un groupe d'administrateurs tout en limitant l'accès pour les autres utilisateurs.

## 3. Commandes de modification
* Modifier le propriétaire uniquement 
```
(machine)root#chown @user @fichier
```
* Modifier le groupe uniquement 
```
(machine)root#chgrp @groupe @fichier
```
* Modifier le propriétaire et le groupe 
```
(machine)root#chown @user:@groupe @fichier
```
* Modifier un répertoire (-R)
```
(machine)root#chown -R @user @repertoire
```
# Sudo 

## **1. Principe de `sudo`**

- **Qu'est-ce que `sudo` ?**  
`sudo` (pour "substitute user do") est une commande Unix/Linux qui permet aux utilisateurs autorisés d'exécuter une commande en tant qu'un autre utilisateur (généralement l'utilisateur root). Elle est couramment utilisée pour accorder des privilèges administratifs temporaires à un utilisateur normal.

- **Pourquoi utiliser `sudo` plutôt que de se connecter en tant que root ?**  
Se connecter en tant que root ou utiliser la commande `su` peut être dangereux car une petite erreur pourrait compromettre le système. `sudo` offre une manière plus sécurisée d'accorder des privilèges, car il peut être configuré pour limiter les actions que chaque utilisateur peut effectuer.
    
---
## **2. Configuration**

- **Le fichier `/etc/sudoers`**  
Ce fichier est le fichier de configuration principal de `sudo`. Il détermine qui peut utiliser `sudo` et pour quelles commandes.

Exemple d'entrées :
```
root    ALL=(ALL:ALL) ALL
%sudo   ALL=(ALL:ALL) ALL
```
- Chaque entrée dans `/etc/sudoers` a plusieurs champs qui déterminent QUI peut exécuter QUOI et COMMENT. Les utilisateurs individuels ou les groupes (précédés d'un `%`) peuvent être spécifiés.

- **Modification sécurisée du fichier `/etc/sudoers`**  
N'éditez jamais ce fichier directement. Utilisez plutôt la commande `visudo` qui assure une édition sécurisée et vérifie les erreurs avant d'enregistrer.

## **3. Sécurité**

- **Exécution contrôlée**  
Grâce à `/etc/sudoers`, l'administrateur du système peut définir précisément quelles commandes un utilisateur peut exécuter avec des privilèges élevés. Cela réduit le risque d'actions malveillantes ou d'erreurs.

- **Journalisation**  
Toutes les commandes exécutées avec `sudo` sont enregistrées. Cela permet de retracer toutes les actions effectuées avec des privilèges élevés.

- **Mot de passe nécessaire**  
Par défaut, lorsque vous utilisez `sudo`, vous devez entrer votre mot de passe (et non celui de root). Cela empêche toute utilisation non autorisée si vous laissez votre session ouverte.

- **Cache du mot de passe**  
Après avoir entré votre mot de passe pour `sudo`, il est "mis en cache" pendant une courte période (généralement 5 minutes). Cela signifie que vous n'aurez pas à retaper votre mot de passe pour chaque commande `sudo` pendant cette période.

## **4. Utilisation**

- **Commandes basiques avec `sudo`**  
Pour exécuter une commande en tant que super utilisateur :
```
sudo [commande]
```
* ***Exécution en tant qu'un autre utilisateur**  
Si vous souhaitez exécuter une commande en tant qu'un autre utilisateur (et non root) :
```
sudo -u [nom_utilisateur] [commande]
```
* ***Obtenir un shell avec des privilèges élevés**  
Si vous avez besoin d'exécuter plusieurs commandes en tant que root, plutôt que de préfixer chaque commande par `sudo`, vous pouvez obtenir un shell avec des privilèges root :
```
sudo -i
```

# Su (substitute user)
#### **1. Qu'est-ce que `su` ?**

**`su`**, ou "substitute user", est une commande Unix/Linux qui permet à un utilisateur de se connecter en tant qu'un autre utilisateur, sans avoir à se déconnecter et à se reconnecter. Par défaut, sans spécifier d'utilisateur, `su` permet de se connecter en tant que root (l'administrateur du système).

**Syntaxe** :
```
su [nom_utilisateur]
```
Si vous n'indiquez pas de nom d'utilisateur, `su` tentera de vous connecter en tant que root. Dans les deux cas, vous devez fournir le mot de passe de l'utilisateur auquel vous essayez de vous connecter.

- **Fonction principale** : `su` est utilisé pour changer d'utilisateur au sein d'une session déjà active. Il permet de démarrer un nouveau shell en tant qu'un autre utilisateur.

- **Mot de passe** : Quand vous utilisez `su`, vous devez entrer le mot de passe de l'utilisateur vers lequel vous basculez, sauf si vous êtes l'utilisateur root (qui peut changer pour n'importe quel utilisateur sans fournir de mot de passe).

- **Environnement** : Sauf si on utilise `su` avec l'option `-`, l'environnement reste celui de l'utilisateur initial. C'est-à-dire que les variables d'environnement de l'utilisateur actuel resteront inchangées.
```
su - [nom_utilisateur]
```

#### **3. Différences clés entre `su` et `sudo`**

1. **Nature des commandes** :
    - **`su`** : Permet de changer d'utilisateur et de lancer un nouveau shell. Si aucun utilisateur n'est spécifié, il se connectera en tant que root.
    - **`sudo`** : Exécute une seule commande en tant qu'un autre utilisateur (généralement root).
2. **Mot de passe requis** :
    - **`su`** : Demande le mot de passe de l'utilisateur auquel vous essayez de vous connecter.
    - **`sudo`** : Demande généralement votre propre mot de passe (et non celui de root), à moins d'être configuré différemment.
3. **Configuration** :
    - **`su`** : N'a pas de configuration spécifique. Tout utilisateur avec le mot de passe approprié peut utiliser `su` pour changer d'utilisateur.
    - **`sudo`** : Est hautement configurable via le fichier `/etc/sudoers`, ce qui permet d'accorder des privilèges spécifiques à des utilisateurs ou groupes pour des commandes spécifiques.
4. **Sécurité** :
    - **`sudo`** offre une trace de toutes les commandes exécutées, ce qui est précieux pour auditer et vérifier les actions réalisées avec des droits élevés. `su` n'a pas cette fonctionnalité par défaut.

#### **4. Quand utiliser `su` ou `sudo` ?**

- **`sudo`** est généralement préféré dans les distributions modernes de Linux pour les tâches administratives courantes car il offre une granularité et une traçabilité plus grandes.
    
- **`su`** peut être utile lorsque vous devez effectuer de nombreuses tâches en tant qu'un autre utilisateur ou si vous souhaitez travailler dans un environnement complètement différent, comme celui d'un autre utilisateur.

# Fichiers de gestion utilisateurs
* Sous Linux, plusieurs fichiers systèmes sont essentiels pour la gestion des utilisateurs et de leurs droits. Trois des plus importants sont `/etc/passwd`, `/etc/group` et `/etc/shadow`. Ils stockent respectivement les informations des utilisateurs, les informations des groupes et les mots de passe chiffrés des utilisateurs.
## /etc/passwd : Informations sur les utilisateurs
* Le fichier `/etc/passwd` contient les informations de base de chaque utilisateur du système.
* Structure d'une ligne 
```
username:password:UID:GID:GECOS:home_directory:shell
```
- **username** : Nom d'utilisateur.
- **password** : Historiquement, stockait le mot de passe chiffré, mais maintenant il contient souvent simplement un "x", le mot de passe étant stocké dans `/etc/shadow`.
- **UID** (User ID) : Identifiant numérique unique attribué à l'utilisateur.
- **GID** (Group ID) : Identifiant numérique du groupe principal de l'utilisateur.
- **GECOS** : Champ de commentaires (souvent utilisé pour stocker le nom complet de l'utilisateur).
- **home_directory** : Chemin vers le répertoire personnel de l'utilisateur.
- **shell** : Shell par défaut de l'utilisateur.
## /etc/group : Informations sur les groupes
* Le fichier `/etc/group` contient les informations sur les groupes du système.
* Structure d'une ligne 
```
group_name:password:GID:members
```
- **group_name** : Nom du groupe.
- **password** : Habituellement laissé vide ou contenant "x".
- **GID** (Group ID) : Identifiant numérique unique attribué au groupe.
- **members** : Liste des membres du groupe, séparés par des virgules.
## /etc/shadow : Mots de passe hashés des utilisateurs
* Le fichier `/etc/shadow` contient les mots de passe chiffrés des utilisateurs ainsi que des informations liées à la politique de mots de passe.
* Structure d'une ligne 
```
username:encrypted_password:last_change:min_days:max_days:warn_days:inactive_days:expiration_date:reserved
```
- **username** : Nom d'utilisateur.
- **encrypted_password** : Mot de passe chiffré.
- **last_change** : Date du dernier changement de mot de passe, exprimée en jours depuis le 1er janvier 1970.
- **min_days** : Nombre minimum de jours avant de pouvoir changer le mot de passe.
- **max_days** : Nombre maximum de jours avant de devoir changer le mot de passe.
- **warn_days** : Nombre de jours d'avertissement avant expiration du mot de passe.
- **inactive_days** : Nombre de jours après expiration du mot de passe avant que le compte soit désactivé.
- **expiration_date** : Date d'expiration du compte.
- **reserved** : Champ réservé pour une utilisation future

Les systèmes Linux modernes utilisent généralement l'un des algorithmes de hachage suivants pour les mots de passe :

1. **MD5** : Bien que MD5 soit l'un des premiers mécanismes utilisés pour le hachage des mots de passe sous Linux, il est maintenant considéré comme obsolète et vulnérable à diverses attaques. Il est identifié dans `/etc/shadow` par le préfixe `$1$`.
    
2. **Blowfish** : Un algorithme de hachage plus robuste que MD5, parfois utilisé dans certaines distributions Linux. Il est identifié par le préfixe `$2a$` ou `$2y$`.
    
3. **SHA-256** et **SHA-512** : Ces deux algorithmes sont actuellement parmi les plus couramment utilisés pour le hachage des mots de passe sous Linux, car ils offrent un bon équilibre entre sécurité et performance. Ils sont identifiés respectivement par les préfixes `$5$` et `$6$`.