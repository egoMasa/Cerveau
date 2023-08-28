# Guide SSH (Secure Shell)

---

## **1. Introduction**

SSH (Secure Shell) est un protocole cryptographique qui permet de communiquer de manière sécurisée sur un réseau non sécurisé, tel qu'Internet. Il est couramment utilisé pour se connecter à des serveurs à distance et pour exécuter des commandes, transférer des fichiers et configurer des services. SSH a remplacé de nombreux protocoles plus anciens comme telnet et rlogin en raison de sa sécurité accrue.

---

## **2. Fonctionnalités Principales**

1. **Authentification** : SSH offre plusieurs méthodes pour authentifier des utilisateurs, notamment par mot de passe, clé publique, ou une combinaison des deux.

2. **Cryptographie** : SSH utilise des algorithmes cryptographiques puissants pour protéger les données pendant leur transfert.

3. **Intégrité des Données** : SSH protège contre les modifications malveillantes et assure que les données n'ont pas été altérées pendant le transfert.

4. **Tunneling & Port Forwarding** : Permet de transmettre des données de manière sécurisée à partir d'applications spécifiques via la connexion SSH.

---

## **3. Historique & Versions**

SSH est disponible en deux versions principales:

- **SSH-1**: La première version de SSH, mais elle est maintenant considérée comme obsolète en raison de vulnérabilités de sécurité.
  
- **SSH-2**: Une version améliorée et plus sécurisée, elle est actuellement la norme.

---

## **4. Mécanisme de Fonctionnement**

1. **Négociation de protocole** : Lorsque la connexion est établie, le client et le serveur conviennent de la version du protocole SSH à utiliser.

2. **Négociation de clés** : Le client et le serveur échangent des clés publiques et déterminent une clé de session partagée.

3. **Authentification** : Le client s'authentifie auprès du serveur en utilisant un mot de passe, une clé publique ou d'autres méthodes.

4. **Session** : Une fois authentifié, le client peut commencer à envoyer des commandes au serveur. Toutes les données échangées pendant la session sont chiffrées.

---

## **5. Authentification**

- **Par mot de passe**: La méthode la plus simple; l'utilisateur fournit un nom d'utilisateur et un mot de passe.

- **Par clé publique**: Une méthode plus sécurisée. L'utilisateur génère une paire de clés (publique et privée). La clé publique est stockée sur le serveur, tandis que la clé privée reste chez le client.

---

## **6. Tunneling & Port Forwarding**

SSH peut encapsuler d'autres protocoles (comme HTTP, FTP, etc.) pour les transmettre de manière sécurisée. Cela peut être utilisé pour sécuriser des protocoles non sécurisés ou pour établir des connexions sécurisées à travers des pare-feux.

- **Local Port Forwarding**: Les données du client sont envoyées à un serveur distant via le serveur SSH.
  
- **Remote Port Forwarding**: Les données du serveur sont envoyées à un client distant via le serveur SSH.

- **Dynamic Port Forwarding**: Utilise SOCKS pour transférer dynamiquement les données.

---

## **7. Sécurité & Vulnérabilités**

Bien que SSH soit sécurisé, il n'est pas à l'abri des vulnérabilités.

- **Brute Force Attacks**: Tentatives répétées pour deviner le mot de passe.

- **Man-in-the-Middle Attacks**: Un attaquant intercepte et modifie la communication entre le client et le serveur.

- Désactiver la connexion root : Pour réduire le risque d'accès non autorisé, il est recommandé de désactiver la connexion directe à la racine et d'utiliser un compte d'utilisateur standard avec des privilèges sudo pour les tâches d'administration.
    
- Utiliser l'authentification par clé : Pour renforcer la sécurité, il est recommandé d'interdire l'authentification par mot de passe et d'utiliser l'authentification par clé publique, ce qui rendra plus difficile l'accès des pirates par des attaques par force brute.
    
- Limiter l'accès SSH : Limitez l'accès SSH à des adresses IP ou à des réseaux spécifiques, afin de réduire la surface d'attaque potentielle.
    
- Maintenez le logiciel SSH à jour : Mettez régulièrement à jour vos logiciels client et serveur SSH pour vous assurer que vous disposez des derniers correctifs de sécurité et des dernières fonctionnalités.

---

## **8. Commandes cisco

- Activer cryptage des mots de passe
```
service password-encryption
```

- Création d'un utilisateur avec mot de passe et privilèges
```
username @nom password @mp  
```

- Authentification des utilisateurs locaux dans les consoles distantes :
```
(config)#line vty 0 4
(config-line)#login local
(config-line)#transport input ssh
```

## **Commandes de Base**

* Connexion à un serveur:
```
- `ssh [user]@[host]`
```

* Transférer des fichiers via SCP:
```
- `scp [file] [user]@[host]:[path]`
```

- Authentification des utilisateurs locaux dans les consoles distantes :
```
(config)#line vty 0 4
(config-line)#login local
(config-line)#transport input ssh
```
---
## 9. Etablissement d'une connexion 

Le processus d'établissement d'une connexion SSH est un échange complexe qui vise à assurer la confidentialité, l'authentification et l'intégrité des données. Voici une explication détaillée des étapes impliquées:

### **1. Négociation du Protocole**

Quand un client SSH tente de se connecter à un serveur SSH :
- Le client envoie la version du protocole SSH qu'il utilise et d'autres paramètres de configuration initiale.
- Le serveur répond avec la version du protocole SSH qu'il utilise.

### **2. Échange de Clés**

Cette étape est cruciale pour établir une communication chiffrée.

- Le serveur envoie sa clé publique au client.
- Le client génère une clé de session secrète pour cette session spécifique.
- Cette clé de session est chiffrée avec la clé publique du serveur et envoyée au serveur.
- Le serveur déchiffre la clé de session à l'aide de sa clé privée. À la fin de cette étape, les deux parties disposent de la même clé de session secrète, qui sera utilisée pour chiffrer toute la communication de cette session.

### **3. Authentification**

Après l'établissement d'une communication chiffrée, la phase d'authentification commence:

- **Authentification par mot de passe** : 
  - Le client envoie le nom d'utilisateur.
  - Le serveur demande un mot de passe.
  - Le client envoie le mot de passe chiffré.
  
- **Authentification par clé** :
  - Le client envoie le nom d'utilisateur et signe un message avec sa clé privée.
  - Le serveur, qui connaît déjà la clé publique correspondante de l'utilisateur, vérifie la signature pour confirmer l'identité du client.

### **4. Établissement de la Session**

Une fois authentifié :
- Le client peut maintenant commencer à exécuter des commandes à distance sur le serveur.
- Toutes les données échangées entre le client et le serveur (y compris les commandes et leurs sorties) sont chiffrées avec la clé de session établie précédemment.

### **5. Terminaison**

Quand la session est terminée, soit par le client, soit par le serveur :
- Les deux parties terminent la connexion de manière propre, et la clé de session est détruite. Si le client souhaite se reconnecter, le processus entier recommence, y compris la génération d'une nouvelle clé de session.

## **9. Conclusion**

SSH est un outil essentiel pour les administrateurs système et les professionnels de la sécurité réseau. Il fournit un moyen sécurisé de se connecter à distance à des serveurs, de transférer des fichiers et d'exécuter des commandes. En comprenant son fonctionnement, ses avantages et ses limites, vous pouvez l'utiliser efficacement tout en maintenant un niveau élevé de sécurité.