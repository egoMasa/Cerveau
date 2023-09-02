
# 1. C'est quoi APT et comment ça marche ?

**APT (Advanced Package Tool)** est le gestionnaire de paquets utilisé par Debian et ses distributions dérivées, comme Ubuntu. Il gère l'installation, la mise à jour et la suppression de logiciels sur le système.

**Comment ça marche ?**

- **Référentiels (Repositories)** : APT se base sur des référentiels en ligne ou locaux pour récupérer des informations sur les paquets disponibles et leurs dépendances. Ces référentiels sont définis dans `/etc/apt/sources.list` ou dans des fichiers individuels sous `/etc/apt/sources.list.d/`.

- **Dépendances** : L'un des avantages majeurs d'APT est sa capacité à gérer automatiquement les dépendances. Lorsque vous installez un paquet, APT détermine les dépendances nécessaires et les installe pour vous.

- **Mise à jour** : APT vérifie régulièrement les référentiels pour voir s'il y a des mises à jour disponibles pour les paquets installés.

**Comparaison** : Pensez à APT comme à un concierge d'hôtel. Lorsque vous (l'utilisateur) voulez un service (un paquet/logiciel), vous le demandez au concierge (APT). Il connaît tous les fournisseurs (référentiels) de la ville, s'assure d'obtenir pour vous ce que vous voulez, s'occupe de tous les détails (dépendances) et vous le livre.

# 2. Les commandes à connaître

- **Mettre à jour la liste des paquets disponibles** : Avant d'installer ou de mettre à jour des paquets, il est recommandé de mettre à jour la liste des paquets disponibles pour avoir les dernières versions.
  ```bash
  sudo apt update
  ```

- **Mettre à jour les paquets installés** : Après avoir mis à jour la liste des paquets, cette commande permet de mettre à jour les paquets déjà installés vers leurs dernières versions.
  ```bash
  sudo apt upgrade
  ```

- **Installer un paquet** : Pour installer un paquet ou un logiciel spécifique.
  ```bash
  sudo apt install nom_du_paquet
  ```

- **Supprimer un paquet** : Cette commande supprime le paquet, mais laisse les fichiers de configuration.
  ```bash
  sudo apt remove nom_du_paquet
  ```

  Si vous voulez supprimer le paquet et ses fichiers de configuration :
  ```bash
  sudo apt purge nom_du_paquet
  ```

- **Réinitialiser / Nettoyer** : Après l'installation ou la suppression de paquets, il peut rester des paquets inutilisés ou des fichiers temporaires. Ces commandes permettent de nettoyer le système.

  Pour supprimer les paquets qui ne sont plus nécessaires :
  ```bash
  sudo apt autoremove
  ```

  Pour nettoyer le cache des paquets téléchargés :
  ```bash
  sudo apt autoclean
  ```

**En résumé**, APT est un outil essentiel pour gérer les paquets sur les systèmes basés sur Debian. Grâce à lui, l'installation, la mise à jour et la suppression de logiciels sont simplifiées, rendant la gestion du système plus efficace et plus sûre.

# 2. DPKG

C'est un autre composant crucial du système de gestion des paquets de Debian et ses dérivés.

## Qu'est-ce que `dpkg` ?

`dpkg` est le gestionnaire de paquets de bas niveau pour Debian. Alors que `APT` gère les dépendances et les téléchargements depuis les référentiels, `dpkg` gère l'installation, la suppression, et l'information des paquets individuels (habituellement sous forme de fichiers `.deb`).

En d'autres termes, si APT est comme un concierge d'hôtel qui organise tout pour vous, `dpkg` est comme le personnel de chambre qui fait effectivement le travail sur le terrain.

## Quand utiliser `dpkg` ?

Vous pourriez utiliser `dpkg` directement dans quelques situations :

1. **Installer un paquet `.deb` téléchargé** : Si vous avez téléchargé un paquet `.deb` manuellement (en dehors des référentiels APT), vous pouvez l'installer avec :
   ```bash
   sudo dpkg -i nom_du_paquet.deb
   ```

2. **Lister les paquets installés** : Pour voir tous les paquets installés sur votre système :
   ```bash
   dpkg -l
   ```

3. **Obtenir des informations sur un paquet installé** :
   ```bash
   dpkg -s nom_du_paquet
   ```

4. **Extraire les fichiers d'un paquet .deb sans l'installer** :
   ```bash
   dpkg -x nom_du_paquet.deb /chemin/destination
   ```

## `dpkg-reconfigure` et sa pertinence

`dpkg-reconfigure` est une commande qui permet de reconfigurer un paquet déjà installé. Lors de l'installation de certains paquets, on vous pose des questions pour configurer le paquet (par exemple, pour choisir la langue par défaut, ou pour définir certains paramètres). Si vous souhaitez changer ces configurations après coup, vous n'avez pas besoin de désinstaller puis de réinstaller le paquet. Vous pouvez simplement utiliser `dpkg-reconfigure`.

Par exemple, pour reconfigurer la zone horaire :
```bash
sudo dpkg-reconfigure tzdata
```

Un cas d'utilisation courant est également la reconfiguration des paquets liés à la gestion des serveurs de noms de domaine, des serveurs de base de données, ou d'autres services qui nécessitent une configuration initiale lors de l'installation.

**En résumé**, `dpkg` est le gestionnaire de paquets de bas niveau qui fait le travail sous-jacent pour APT. Bien qu'APT soit généralement préféré pour la gestion quotidienne des paquets en raison de sa gestion des dépendances, `dpkg` offre une granularité qui est parfois nécessaire, notamment pour installer des paquets hors référentiels ou pour obtenir des informations détaillées sur les paquets. Quant à `dpkg-reconfigure`, il est essentiel pour reconfigurer les paquets sans les désinstaller.