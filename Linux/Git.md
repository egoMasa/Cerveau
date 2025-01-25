# Guide d'installation pour relier un dépôt distant à un répertoire local avec Git et SSH

Ce guide décrit les étapes complètes pour configurer un dépôt Git, se connecter en SSH, synchroniser des fichiers et cacher certains fichiers ou répertoires (à l'aide de `.gitignore`).
## Prérequis

1. **Git** installé sur votre système.
```bash
sudo apt update
sudo apt install git
```
2. **Compte GitHub** actif.
3. **Clé SSH** générée et configurée sur votre compte GitHub.

Si vous n'avez pas de clé SSH, consultez la section suivante.

---
## Étape 1 : Générer et configurer une clé SSH

1. **Générer une clé SSH** :
```bash
ssh-keygen -t ed25519 -C "votre_email@example.com"
```
- Appuyez sur **Entrée** pour accepter le chemin par défaut (`~/.ssh/id_ed25519`).
- (Facultatif) Entrez une phrase de passe pour plus de sécurité.
2. **Ajouter la clé au gestionnaire SSH** :
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

3. **Copier la clé publique** :
```bash
cat ~/.ssh/id_ed25519.pub
```

Copier la sortie de cette commande.

4. **Ajouter la clé à GitHub** :
- Allez sur GitHub : [SSH Keys Settings](https://github.com/settings/keys).
- Cliquez sur **New SSH key**.
- Collez votre clé publique dans le champ et sauvegardez.
5. **Tester la connexion SSH** :
```bash
ssh -T git@github.com
```

Si tout est bien configuré, un message comme :
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```


---

## Étape 2 : Relier un dépôt distant à un répertoire local

1. **Cloner un dépôt distant** :
- Remplacez `username` et `repository` par vos informations GitHub :
```bash
git clone git@github.com:username/repository.git
```
- Cela créera un répertoire local nommé `repository` contenant tous les fichiers.

2. **Accéder au répertoire** :
```bash
cd repository
```

3. **Configurer le dépôt** (facultatif) :
- Si votre dépôt a une branche principale différente (`main`, `master`, etc.), vérifiez-la :
```bash
git branch -r
```


---

## Étape 3 : Cacher les répertoires ou fichiers locaux

1. **Créer un fichier `.gitignore`** :
- À la racine de votre dépôt, créez un fichier `.gitignore` :
```bash
touch .gitignore
```

2. **Ajouter les répertoires à ignorer** :
- Ouvrez `.gitignore` avec un éditeur de texte (par exemple `nano`) :
```bash
nano .gitignore
```
- Ajoutez les répertoires ou fichiers à ignorer :
```
.obsidian/
.gitignore
```

3. **Supprimer les fichiers suivis (si nécessaire)** :
- Si `.obsidian` ou `.gitignore` ont déjà été ajoutés à Git, supprimez-les de l’index :
```bash
git rm -r --cached .obsidian .gitignore
```

4. **Vérifier que les fichiers sont ignorés** :
```bash
git status
```

Les fichiers/répertoires ignorés ne doivent pas apparaître.

---

## Étape 4 : Ajouter, commiter et pousser des modifications

1. **Ajouter les modifications au staging** :
- Ajouter un fichier ou un répertoire spécifique :
```bash
git add fichier.txt
```

- Ajouter tous les fichiers suivis :
```bash
git add .
```

2. **Créer un commit** :
- Avec un message décrivant les modifications :
```bash
git commit -m "Message de commit"
```

3. **Pousser les modifications sur le dépôt distant** :
```bash
git push origin main
```

(Remplacez `main` par le nom de la branche si besoin.)

---

## Étape 5 : Tirer les modifications depuis le dépôt distant

Pour synchroniser votre répertoire local avec les dernières modifications du dépôt distant :

```bash
git pull origin main
```

---

## Exemple complet

Voici un exemple résumant toutes les commandes :

```bash
# Génération de clé SSH
ssh-keygen -t ed25519 -C "email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Cloner un dépôt
cd ~/Documents
git clone git@github.com:username/repository.git
cd repository

# Créer et configurer .gitignore
echo ".obsidian/" >> .gitignore
echo ".gitignore" >> .gitignore
git rm -r --cached .obsidian .gitignore

# Ajouter, commiter et pousser un fichier
echo "# Mon fichier test" > test.md
git add test.md
git commit -m "Ajout du fichier test"
git push origin main

# Tirer les modifications
git pull origin main
```
