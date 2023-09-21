
# Différentes bases de données 
1. Working Directory
2. Local Repository
3. Remote Repository (GitHub)

# Logique 

## Phase 1 : Working Directory
* Le ***working directory*** est tout simplement un répertoire présent sur notre PC avec des fichiers sur lesquels on travail
## Phase 2 : Staging des modifications
- Lorsqu'on termine nos modifications sur un ou plusieurs fichiers, on passe à la phase de staging. Cette étape permet de sélectionner et de marquer les fichiers ou parties de fichiers que l'on souhaite inclure dans le prochain commit.
- Lors du staging, ce ne sont pas forcément les fichiers entiers qui sont pris en compte, mais plutôt les segments modifiés de ces fichiers. Git détecte ces modifications et nous offre la possibilité de décider si nous voulons les inclure dans le prochain commit ou non.
- On peut stager toutes les modifications d'un fichier en utilisant 
```
git add [NOM_DU_FICHIER]
```
- Si l'on souhaite stager des modifications de manière interactive, c'est-à-dire choisir spécifiquement quelles parties des modifications on souhaite inclure (Git nous présentera alors chaque segment modifié et nous demandera si nous voulons l'inclure dans le staging)
```
git add -p
```

## Phase 3 : Commit vers le local repository
- Avec les modifications stagées, nous sommes prêts à créer un nouveau commit qui représentera cet ensemble de modifications dans le local repository.
- Le local repo est une sorte de base de données qui contient toutes les suites de commits effectués sur le répertoire. Il contient l'historique des anciens commits (versions).
- Une fois le commit réalisé dans le local repo, on va effectuer un push de ce nouveau commit (section modifiée) vers le remote repo, qui pourra alors afficher de façon graphique l'évolution et l'historique des commits du fichier.
* Après avoir stagé vos modifications (ce qui a été discuté dans la phase 2), vous allez maintenant les "commiter" dans votre local repository.
```
git commit -m "Description des modifications"
```
## Phase 4 : Local Repository vers Remote Repository
* Une fois le commit créer on va l'envoyer vers le Remote Repository afin qu'il soit centraliser
```
git remote add origin https://github.com/[URL].git
git branch -M [BRANCH]
git push origin [BRANCH]
```