# Sommaire 
#### 1. Introduction à Python
- **Historique et philosophie** : Brève introduction sur l'origine de Python et ses principes de conception.
- **Installation et configuration** : Comment installer Python et configurer l'environnement de développement.

#### 2. Bases du langage
- **Syntaxe de base** : Structure d'un programme Python, indentation, commentaires.
- **Variables et types de données** : Nombres, chaînes de caractères, booléens.
- **Opérateurs** : Arithmétiques, de comparaison, logiques, d'assignation.

#### 3. Structures de contrôle
- **Instructions conditionnelles** : `if`, `elif`, `else`.
- **Boucles** : `for` pour les itérations déterminées, `while` pour les itérations indéterminées.

#### 4. Fonctions
- **Définition et appel** : Création de fonctions, passage d'arguments, valeurs de retour.
- **Portée des variables** : Locale vs globale.
- **Fonctions anonymes (lambda)** : Syntaxe et utilisation.

#### 5. Collections de données
- **Listes** : Création, accès aux éléments, méthodes de liste.
- **Tuples** : Comme les listes, mais immuables.
- **Dictionnaires** : Paires clé-valeur, méthodes de dictionnaire.
- **Ensembles** : Collections non ordonnées et uniques.

#### 6. Manipulation de fichiers
- **Lecture et écriture de fichiers** : `open`, `read`, `write`, `close`.

#### 7. Gestion des erreurs
- **Exceptions** : Try, except, finally pour la gestion des erreurs.

#### 8. Modules et paquets
- **Importation** : Utiliser des modules standard, installer et utiliser des paquets tiers.
- **Création de modules** : Comment organiser le code en modules.

#### 9. Programmation orientée objet
- **Classes et objets** : Définition de classes, création d'instances.
- **Encapsulation** : Utilisation des propriétés pour protéger l'accès aux données.
- **Héritage** : Dériver de nouvelles classes à partir de classes existantes.
- **Polymorphisme** : Définir des méthodes qui peuvent se comporter différemment selon l'objet.

#### 10. Techniques avancées
- **Compréhensions de liste** : Syntaxe concise pour créer des listes.
- **Générateurs et itérateurs** : Créer des séquences personnalisées efficaces.
- **Décorateurs** : Étendre et modifier le comportement des fonctions.

#### 11. Tests et débogage
- **Unit testing** : Créer des tests pour valider le code à l'aide du module `unittest`.
- **Débogage** : Utiliser des outils et des techniques pour identifier et corriger les erreurs.

#### 12. Bonnes pratiques
- **Style de codage** : Suivre les conventions PEP8.
- **Documentation** : Documenter le code avec des docstrings.

# 1) Introduction à Python

## 1.1 Historique et philosophie

Python a été créé par Guido van Rossum et a été rendu public pour la première fois en 1991. Le langage a été conçu pour être facile à lire et à écrire, avec une syntaxe claire qui favorise la lisibilité. La philosophie de Python repose sur plusieurs principes fondamentaux, souvent résumés par le "Zen de Python", un ensemble de règles aphoristiques pour écrire du code en Python. Ces principes incluent :
- La beauté est préférable à la laideur.
- Explicit est mieux qu'implicite.
- Simple est mieux que complexe.
- La lisibilité compte.

## 1.2 Installation et configuration

Installer Python et configurer un environnement de développement sont les premiers pas pour commencer à programmer en Python. Python peut être installé directement depuis python.org ou via des gestionnaires de paquets pour des systèmes spécifiques (comme `apt` sur Ubuntu ou `brew` sur macOS). 

**Variations possibles** :
- **Python 2 vs Python 3** : Python 3 est la version actuellement recommandée. Python 2 n'est plus pris en charge depuis janvier 2020.
- **Environnements virtuels** : Utiliser `venv` ou `conda` pour créer des environnements isolés pour différents projets. Cela permet de gérer les dépendances de manière plus propre et éviter les conflits entre les versions de paquets.

**Exemple de configuration** :

1. **Installation de Python** :
   - Sur Windows, téléchargez l'installateur depuis [python.org](https://www.python.org/downloads/) et suivez les instructions.
   - Sur macOS, utilisez Homebrew avec la commande : `brew install python3`.
   - Sur Ubuntu, utilisez APT : `sudo apt-get install python3`.

2. **Configuration d'un environnement virtuel** :
   - Créer un nouvel environnement virtuel : `python3 -m venv mon_env`
   - Activer l'environnement virtuel :
     - Sur Windows : `.\mon_env\Scripts\activate`
     - Sur macOS ou Linux : `source mon_env/bin/activate`

3. **Vérification de l'installation** :
   - Vérifiez que Python est correctement installé en exécutant : `python --version`
   - Vérifiez que pip (gestionnaire de paquets Python) fonctionne : `pip --version`

# 2) Bases du langage Python

## 2.1 Syntaxe de base

Python est conçu pour être un langage facile à lire et à écrire. La syntaxe de Python est épurée et met l'accent sur la lisibilité. Les aspects clés incluent :
- **Indentation** : Python utilise l'indentation pour délimiter les blocs de code. Cela signifie que les boucles, les conditions, les définitions de fonctions et les blocs de code d'autres structures de contrôle dépendent de l'indentation pour définir leur portée.
- **Commentaires** : Python utilise le symbole `#` pour les commentaires. Tout texte après `#` sur une ligne est ignoré par l'interpréteur Python.

**Exemple en code** :
```python
# C'est un commentaire en Python
def ma_fonction():
    if True:
        print("Hello, World!")  # Affiche un message à l'écran

ma_fonction()
```

## 2.2 Variables et types de données

Python est un langage de typage dynamique, ce qui signifie que vous n'avez pas besoin de déclarer explicitement le type d'une variable lors de sa création. Les principaux types de données en Python incluent :
- **Nombres** : Intégraux (`int`) et à virgule flottante (`float`).
- **Chaînes de caractères** (`str`) : Texte entouré de guillemets simples ou doubles.
- **Booléens** (`bool`) : Valeurs logiques `True` ou `False`.

**Exemple en code** :
```python
nombre = 10        # Un entier
pi = 3.14          # Un flottant
message = "Bonjour"  # Une chaîne de caractères
actif = True       # Un booléen
```

## 2.3 Opérateurs

Python offre une gamme complète d'opérateurs pour effectuer des calculs arithmétiques, des comparaisons et des opérations logiques. Ces opérateurs comprennent :

- **Opérateurs arithmétiques** : `+`, `-`, `*`, `/`, `//` (division entière), `%` (modulo), `**` (exponentiation).
- **Opérateurs de comparaison** : `==`, `!=`, `<`, `>`, `<=`, `>=`.
- **Opérateurs logiques** : `and`, `or`, `not`.
- **Opérateurs d'assignation** : `=`, `+=`, `-=`, `*=`, `/=`, etc.

**Exemple en code** :
```python
a = 10
b = 20
c = a + b  # Addition, résultat 30
d = a < b  # Comparaison, résultat True
e = not (a > b)  # Opérateur logique, résultat True

a += 5  # Augmente a de 5, maintenant a vaut 15
```

# 3) Structures de contrôle en Python

## 3.1 Instructions conditionnelles

Les instructions conditionnelles permettent d'exécuter différents blocs de code en fonction de certaines conditions. Python utilise les mots-clés `if`, `elif` (else if), et `else` pour gérer ces flux conditionnels. C'est un outil fondamental pour diriger le comportement d'un programme en fonction des valeurs des variables ou des résultats des opérations.

**Exemple en code** :
```python
age = 25

if age < 18:
    print("Vous êtes mineur.")
elif age >= 18 and age < 65:
    print("Vous êtes adulte.")
else:
    print("Vous êtes senior.")
```
Dans cet exemple, Python évalue l'âge et affiche un message approprié selon la tranche d'âge. Le code suit un chemin conditionnel basé sur les valeurs de `age`.

## 3.2 Boucles

Les boucles permettent de répéter l'exécution d'un bloc de code plusieurs fois, soit un nombre prédéterminé de fois (boucle `for`), soit tant qu'une condition donnée est vraie (boucle `while`). Ces structures sont essentielles pour effectuer des opérations répétitives sans dupliquer le code.

- **Boucle `for`** : Idéale pour itérer sur une séquence (comme une liste, un tuple, ou une chaîne de caractères) ou pour exécuter une action un nombre précis de fois en utilisant `range()`.
- **Boucle `while`** : Exécute un bloc de code tant que la condition spécifiée est vraie.

**Exemple en code** :
```python
# Exemple de boucle for
for i in range(5):
    print(f"Valeur de i: {i}")  # Affiche i de 0 à 4

# Exemple de boucle while
j = 5
while j > 0:
    print(f"Valeur de j: {j}")  # Affiche j à partir de 5 jusqu'à 1
    j -= 1  # Décrémente j de 1 à chaque itération
```
Dans ces exemples, la boucle `for` utilise `range(5)` pour itérer de 0 à 4. La boucle `while`, quant à elle, continue d'exécuter tant que `j` est supérieur à 0, et `j` est décrémenté après chaque passage dans la boucle.


# 4) Fonctions en Python

## 4.1 Définition et appel

Les fonctions en Python sont définies avec le mot-clé `def` et sont utilisées pour encapsuler du code réutilisable dans des blocs logiques. Elles peuvent prendre des arguments et renvoyer des valeurs. Les fonctions permettent de segmenter le programme en petites unités, facilitant la maintenance et le débogage.

**Exemple en code** :
```python
def additionner(a, b):
    """Retourne la somme de deux nombres."""
    return a + b

# Appel de la fonction
resultat = additionner(5, 3)
print("Le résultat de l'addition est :", resultat)
```
Dans cet exemple, `additionner` est une fonction qui prend deux arguments et retourne leur somme. La fonction est ensuite appelée avec les valeurs 5 et 3, et le résultat est affiché.

## 4.2 Portée des variables

En Python, la portée d'une variable détermine où elle peut être accessible dans le code. Les variables définies à l'intérieur d'une fonction ont une portée locale à cette fonction. Cela signifie qu'elles ne peuvent pas être accédées en dehors de cette fonction. Les variables définies à l'extérieur de toutes les fonctions ont une portée globale et peuvent être accessibles de n'importe quel endroit dans le code.

**Exemple en code** :
```python
x = "global"  # Variable globale

def demo():
    y = "local"  # Variable locale
    print(x)  # Accède à la variable globale
    print(y)  # Accède à la variable locale

demo()
# print(y)  # Cela causerait une erreur car y n'est pas accessible en dehors de la fonction
```
Dans cet exemple, `x` est une variable globale accessible partout, tandis que `y` est une variable locale qui ne peut être utilisée que dans la fonction `demo`.

## 4.3 Fonctions anonymes (lambda)

Les fonctions lambda en Python sont de petites fonctions anonymes définies en une seule ligne. Elles sont souvent utilisées pour des opérations nécessitant une fonction pour un court moment, sans avoir à la définir formellement. Les lambda sont particulièrement utiles pour les opérations simples et pour les arguments de fonctions qui attendent une fonction.

**Exemple en code** :
```python
# Une fonction lambda qui multiplie deux valeurs
multiplier = lambda x, y: x * y

# Utilisation de la fonction lambda
print("Le produit de 4 et 5 est :", multiplier(4, 5))

# Utilisation courante des lambdas avec des fonctions de haut niveau
nombres = [1, 2, 3, 4]
squares = list(map(lambda x: x ** 2, nombres))
print("Carrés des nombres :", squares)
```
Dans cet exemple, `multiplier` est une fonction lambda qui prend deux arguments et retourne leur produit. La fonction `map` est ensuite utilisée avec une autre lambda pour obtenir les carrés des nombres dans la liste `nombres`.


# 5) Collections de données en Python

## 5.1 Listes

Les listes en Python sont des collections ordonnées et modifiables qui peuvent contenir des éléments de différents types. Les listes sont très flexibles et utilisées couramment dans de nombreuses situations de programmation.

**Opérations de base** :
- **Création** : Utilisation de crochets `[]` pour créer une liste.
- **Accès aux éléments** : Utilisation de l'indexation, commençant à zéro.
- **Méthodes de liste** : `.append()`, `.remove()`, `.sort()`, etc.

**Exemple en code** :
```python
# Création d'une liste
fruits = ["pomme", "banane", "cerise"]

# Accès aux éléments
print(fruits[1])  # Affiche 'banane'

# Ajout d'un élément
fruits.append("orange")

# Suppression d'un élément
fruits.remove("cerise")

# Trier la liste
fruits.sort()
print(fruits)  # ['banane', 'orange', 'pomme']
```

## 5.2 Tuples

Les tuples sont des collections qui sont très similaires aux listes, mais immuables. Une fois créé, un tuple ne peut pas être modifié. Cela les rend utiles pour stocker des ensembles de valeurs qui ne doivent pas changer au cours de l'exécution du programme.

**Exemple en code** :
```python
# Création d'un tuple
dimensions = (1920, 1080)

# Accès aux éléments
print(dimensions[0])  # Affiche 1920

# Tenter de modifier un tuple générera une erreur
# dimensions[0] = 1200  # Ceci est interdit et lève une TypeError
```

## 5.3 Dictionnaires

Les dictionnaires en Python sont des collections non ordonnées de paires clé-valeur. Ils sont optimisés pour récupérer des valeurs lorsque la clé est connue.

**Opérations de base** :
- **Création** : Utilisation de `{}` ou `dict()`.
- **Accès aux éléments** : Accès via les clés.
- **Méthodes de dictionnaire** : `.keys()`, `.values()`, `.items()`, `.get()`, `.setdefault()`.

**Exemple en code** :
```python
# Création d'un dictionnaire
personne = {"nom": "Jean", "age": 30}

# Accès aux éléments
print(personne["nom"])  # Affiche 'Jean'

# Ajouter ou modifier une clé
personne["ville"] = "Paris"

# Utiliser get pour éviter les KeyError
print(personne.get("profession", "Non spécifiée"))  # Affiche 'Non spécifiée'

# Parcourir un dictionnaire
for cle, valeur in personne.items():
    print(f"{cle}: {valeur}")
```

## 5.4 Ensembles

Les ensembles sont des collections non ordonnées de valeurs uniques. Ils sont utilisés pour stocker des éléments sans doublons et pour effectuer des opérations mathématiques comme des unions, intersections, et différences.

**Exemple en code** :
```python
# Création d'un ensemble
nombres = {1, 2, 3, 4, 4, 5}

# L'ensemble contiendra {1, 2, 3, 4, 5}
print(nombres)

# Ajout d'un élément
nombres.add(6)

# Suppression d'un élément
nombres.remove(6)

# Opérations d'ensemble
autres = {4, 5, 6}
print(nombres.intersection(autres))  # Affiche {4, 5}
```


# 6) Manipulation de fichiers en Python

## 6.1 Lecture et écriture de fichiers

La manipulation de fichiers en Python est une compétence essentielle, permettant aux programmes de lire des données depuis des fichiers et d'y écrire des données. Python simplifie la gestion des fichiers grâce à des fonctions intégrées comme `open`, `read`, `write`, et `close`.

- **`open`** : Utilisée pour ouvrir un fichier et retourner un objet fichier. Le mode d'ouverture spécifie si le fichier est ouvert en lecture (`r`), écriture (`w`), ajout (`a`), ou d'autres modes.
- **`read`** : Lit les données d'un fichier. Vous pouvez lire le fichier entier ou lire un nombre spécifique de caractères.
- **`write`** : Écrit des données dans un fichier. Si le fichier n'existe pas, il sera créé.
- **`close`** : Ferme le fichier ouvert. Il est important de fermer les fichiers pour libérer les ressources système.

#### Exemple en code :

**Lecture de fichier** :
```python
# Ouvrir un fichier en mode lecture
f = open('exemple.txt', 'r')

# Lire le contenu entier du fichier
contenu = f.read()
print(contenu)

# Toujours fermer le fichier après utilisation
f.close()
```

**Écriture dans un fichier** :
```python
# Ouvrir un fichier en mode écriture, 'w' écrase le fichier s'il existe
f = open('nouveau.txt', 'w')

# Écrire du texte dans le fichier
f.write("Bonjour, monde!\n")

# Fermer le fichier pour s'assurer que les données sont sauvegardées
f.close()
```

**Utilisation du gestionnaire de contexte** :
Une meilleure pratique consiste à utiliser le gestionnaire de contexte `with` qui s'assure que le fichier est correctement fermé après que son bloc de code est exécuté, même en cas d'erreur.

```python
# Utilisation de 'with' pour la lecture
with open('exemple.txt', 'r') as f:
    contenu = f.read()
    print(contenu)

# Utilisation de 'with' pour l'écriture
with open('nouveau.txt', 'w') as f:
    f.write("Bonjour encore une fois, monde!\n")
```

Dans ces exemples, `with` ouvre le fichier et le ferme automatiquement à la fin du bloc indiqué, rendant le code plus sûr et plus propre.


# 7) Gestion des erreurs en Python

## 7.1 Exceptions

Les exceptions en Python sont des événements qui peuvent modifier le flux normal d'un programme. Elles sont généralement générées lorsque Python rencontre une erreur lors de l'exécution d'un programme. Au lieu de faire planter le programme, Python permet de gérer ces exceptions de manière gracieuse à l'aide des blocs `try`, `except`, `else`, et `finally`.

- **`try`** : Ce bloc vous permet de tester un bloc de code pour des erreurs, c'est-à-dire que le code à l'intérieur du bloc `try` est exécuté.
- **`except`** : Ce bloc vous permet de gérer l'erreur, c'est-à-dire de spécifier une réponse à l'erreur ou à l'exception soulevée dans le bloc `try`.
- **`else`** : Si le code dans le bloc `try` ne génère pas d'erreur, le code dans le bloc `else` est exécuté.
- **`finally`** : Ce bloc vous permet d'exécuter du code, indépendamment du résultat des blocs `try` et `except`. Ce code est souvent utilisé pour des actions de nettoyage.

#### Exemple en code :

**Gestion simple d'exception** :
```python
try:
    print("Division")
    resultat = 10 / 0  # Cette ligne va causer une exception DivisionError
except ZeroDivisionError:
    print("Une erreur de division par zéro s'est produite.")
finally:
    print("Ce bloc s'exécute toujours, qu'il y ait une exception ou non.")
```

**Utilisation multiple de `except`** :
```python
try:
    valeur = int(input("Veuillez entrer un nombre : "))
    resultat = 10 / valeur
except ValueError:
    print("Veuillez entrer une valeur correcte!")
except ZeroDivisionError:
    print("Division par zéro non permise!")
else:
    print(f"Résultat : {resultat}")
finally:
    print("Exécution terminée.")
```

Dans ce second exemple, plusieurs types d'exceptions sont gérés : `ValueError` pour les erreurs de conversion de type si l'entrée n'est pas un nombre, et `ZeroDivisionError` pour les tentatives de division par zéro. Le bloc `else` s'exécute si aucune erreur n'est levée, et `finally` s'exécute toujours, indépendamment de ce qui se passe dans les autres blocs.

#### Bonnes pratiques :
1. **Spécifier des exceptions** : Toujours attraper des exceptions spécifiques plutôt qu'une exception générale pour éviter de masquer des erreurs inattendues.
2. **Ressources de nettoyage** : Utiliser `finally` pour la libération de ressources, comme la fermeture de fichiers ou de connexions réseau, assurant que ces actions sont effectuées peu importe si une erreur survient ou non.


# 8) Modules et paquets en Python

## 8.1 Importation

Les modules en Python sont des fichiers contenant du code Python, typiquement définissant des classes, des fonctions, et des variables, ainsi que du code exécutable. L'importation permet de réutiliser des éléments d'un module dans un autre module. Les paquets sont des collections de modules organisés dans un dossier, où un fichier `__init__.py` est souvent présent pour indiquer que le dossier est un paquet Python.

- **Utiliser des modules standard** : Python vient avec une bibliothèque standard très riche, offrant des modules pour presque toutes les tâches (par exemple, `math`, `os`, `sys`, `datetime`).
- **Installer et utiliser des paquets tiers** : Pour des fonctionnalités non disponibles dans la bibliothèque standard, Python permet d'installer des paquets tiers via des outils comme pip, par exemple `requests` pour les requêtes HTTP ou `numpy` pour les calculs numériques.

**Exemple en code** :
```python
# Importation d'un module standard
import math
print(math.sqrt(16))  # Affiche 4.0

# Importation d'une fonction spécifique d'un module
from datetime import datetime
print(datetime.now())  # Affiche la date et l'heure actuelle

# Installation et importation d'un paquet tiers (exemple hypothétique)
# pip install requests
import requests
response = requests.get('https://api.github.com')
print(response.status_code)  # Affiche le code de statut de la réponse HTTP
```

## 8.2 Création de modules

Créer vos propres modules peut aider à organiser mieux votre code Python, surtout pour les grands projets. Un module peut être aussi simple qu'un fichier Python contenant des définitions de fonctions et de classes, qui peuvent être importées et utilisées dans d'autres fichiers ou modules.

**Étapes pour créer un module** :
1. **Écrire du code dans un fichier `.py`** : Placez les fonctions, les classes, et les variables que vous souhaitez inclure dans votre module.
2. **Importation dans d'autres scripts** : Utilisez le mot-clé `import` suivi du nom du fichier pour utiliser son contenu dans d'autres scripts Python.

**Exemple en code** :
Supposons que vous avez un fichier appelé `mymodule.py` avec le contenu suivant :
```python
# mymodule.py
def saluer(nom):
    print(f"Bonjour, {nom}!")
```
Vous pouvez utiliser ce module dans un autre script :
```python
# script.py
import mymodule
mymodule.saluer("Alice")  # Affiche "Bonjour, Alice!"
```

#### Bonnes pratiques :
- **Nommez les modules et les paquets de manière significative** : Les noms doivent refléter le contenu et les fonctionnalités.
- **Minimisez l'interdépendance entre les modules** : Essayez de rendre les modules aussi indépendants que possible pour faciliter la réutilisation.
- **Documentez vos modules** : Utilisez des docstrings pour expliquer ce que fait le module et comment les différentes fonctions et classes doivent être utilisées.


# 9) Programmation orientée objet en Python

## 9.1 Classes et objets

La programmation orientée objet (POO) est un paradigme de programmation basé sur le concept de "classes" et "objets". Les classes servent de modèles pour créer des objets, qui sont des instances de ces classes. Python, en tant que langage de programmation orienté objet, permet la création de classes complexe et la manipulation d'objets.

**Exemple en code** :
```python
class Voiture:
    def __init__(self, marque, modele):
        self.marque = marque
        self.modele = modele
    
    def afficher(self):
        print(f"Voiture: {self.marque} {self.modele}")

# Création d'une instance de Voiture
ma_voiture = Voiture("Toyota", "Corolla")
ma_voiture.afficher()  # Affiche "Voiture: Toyota Corolla"
```

## 9.2 Encapsulation

L'encapsulation est un concept clé en POO qui consiste à restreindre l'accès à certaines méthodes ou attributs d'une classe. Cela est réalisé en les déclarant comme privés ou protégés. Cela permet de cacher la complexité interne et de protéger l'intégrité des données.

**Exemple en code** :
```python
class CompteBancaire:
    def __init__(self, proprietaire, solde=0):
        self.proprietaire = proprietaire
        self.__solde = solde  # Attribut privé

    def deposer(self, montant):
        if montant > 0:
            self.__solde += montant
            print("Dépôt effectué.")
    
    def retirer(self, montant):
        if montant <= self.__solde:
            self.__solde -= montant
            print("Retrait effectué.")
        else:
            print("Fonds insuffisants.")

    def get_solde(self):
        return self.__solde

mon_compte = CompteBancaire("Alice")
mon_compte.deposer(200)
print(mon_compte.get_solde())  # Affiche 200
```

## 9.3 Héritage

L'héritage permet à une classe de hériter d'attributs et de méthodes d'une autre classe. La classe qui hérite est appelée classe dérivée ou sous-classe, tandis que la classe dont elle hérite est appelée classe de base ou superclasse.

**Exemple en code** :
```python
class Vehicule:
    def __init__(self, marque):
        self.marque = marque

class Voiture(Vehicule):
    def __init__(self, marque, modele):
        super().__init__(marque)  # Appelle le constructeur de la classe de base
        self.modele = modele

voiture = Voiture("Ford", "Mustang")
print(f"Voiture: {voiture.marque} {voiture.modele}")  # Ford Mustang
```

## 9.4 Polymorphisme

Le polymorphisme est la capacité d'utiliser une interface unique pour représenter différents types de données. En Python, le polymorphisme se manifeste souvent par la capacité de différentes classes d'être traitées comme leur classe de base commune.

**Exemple en code** :
```python
class Animal:
    def parler(self):
        pass

class Chien(Animal):
    def parler(self):
        return "Woof!"

class Chat(Animal):
    def parler(self):
        return "Meow!"

def faire_parler(animal):
    print(animal.parler())

mon_chien = Chien()
mon_chat = Chat()

faire_parler(mon_chien)  # Affiche "Woof!"
faire_parler(mon_chat)  # Affiche "Meow!"
```

Dans cet exemple, bien que `Chien` et `Chat` soient des classes différentes, ils partagent une méthode commune `parler()`, et peuvent être utilisés de manière interchangeable dans la fonction `faire_parler`. Cela illustre le polymorphisme où différentes classes partagent la même interface de méthodes.



# 10) Techniques avancées en Python

## 10.1 Compréhensions de liste

Les compréhensions de liste en Python fournissent une manière concise de créer des listes. Basées sur les notations mathématiques de construction d'ensembles, elles permettent de filtrer et de transformer des listes en une seule ligne de code.

**Exemple en code** :
```python
# Créer une liste des carrés des nombres de 0 à 9
carrés = [x**2 for x in range(10)]
print(carrés)  # Affiche [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Filtrer pour obtenir uniquement les carrés pairs
carrés_pairs = [x for x in carrés if x % 2 == 0]
print(carrés_pairs)  # Affiche [0, 4, 16, 36, 64]
```

## 10.2 Générateurs et itérateurs

Les générateurs sont des fonctions qui permettent de générer une séquence de valeurs au fil du temps, en utilisant le mot-clé `yield` plutôt que `return`. Les itérateurs sont des objets qui implémentent les méthodes `__iter__()` et `__next__()` pour permettre de parcourir les éléments d'une collection.

**Exemple en code** :
```python
# Un générateur simple
def mon_generateur(n):
    i = 0
    while i < n:
        yield i
        i += 1

# Utilisation du générateur
for valeur in mon_generateur(5):
    print(valeur)  # Affiche 0, 1, 2, 3, 4

# Création d'un itérateur
class CompteRebours:
    def __init__(self, start):
        self.current = start
    def __iter__(self):
        return self
    def __next__(self):
        if self.current > 0:
            num = self.current
            self.current -= 1
            return num
        raise StopIteration

# Utilisation de l'itérateur
for num in CompteRebours(3):
    print(num)  # Affiche 3, 2, 1
```

## 10.3 Décorateurs

Les décorateurs sont des fonctions qui modifient le comportement d'autres fonctions ou méthodes. Ils sont particulièrement utiles pour ajouter de manière propre et réutilisable des fonctionnalités aux fonctions existantes.

**Exemple en code** :
```python
# Décorateur simple
def mon_decorateur(func):
    def wrapper():
        print("Quelque chose se passe avant l'appel de la fonction.")
        func()
        print("Quelque chose se passe après l'appel de la fonction.")
    return wrapper

@mon_decorateur
def dit_bonjour():
    print("Bonjour!")

dit_bonjour()
# Affiche:
# Quelque chose se passe avant l'appel de la fonction.
# Bonjour!
# Quelque chose se passe après l'appel de la fonction.
```


# 11) Tests et débogage en Python

## 11.1 Unit testing

Les tests unitaires sont essentiels pour s'assurer que votre code fonctionne comme prévu. En Python, le module `unittest` fournit des outils pour créer des tests unitaires, qui peuvent automatiquement vérifier si différentes parties de votre programme fonctionnent correctement sous diverses conditions. Cela aide à identifier les bugs précocement dans le cycle de développement.

**Exemple en code** :
```python
import unittest

def somme(a, b):
    return a + b

class TestSomme(unittest.TestCase):
    def test_somme_positifs(self):
        self.assertEqual(somme(1, 2), 3)

    def test_somme_negatifs(self):
        self.assertEqual(somme(-1, -1), -2)

    def test_somme_posneg(self):
        self.assertEqual(somme(-1, 2), 1)

# Lancer les tests
if __name__ == "__main__":
    unittest.main()
```
Dans cet exemple, trois tests vérifient si la fonction `somme` fonctionne correctement avec des nombres positifs, négatifs et un mélange des deux.

## 11.2 Débogage

Déboguer est le processus de détecter, de traquer et de corriger les défauts ou problèmes dans le code. Python offre plusieurs outils et techniques de débogage, tels que l'utilisation de l'instruction `print()` pour afficher les valeurs, ou des outils plus avancés comme le module `pdb` (Python Debugger) qui permet de parcourir le code ligne par ligne pour examiner les valeurs des variables et le flux d'exécution.

**Techniques de débogage** :
- **Print Debugging** : Placer des instructions `print` pour afficher l'état interne du programme à divers points.
- **Utilisation de pdb** : Le module `pdb` offre des fonctionnalités telles que des points d'arrêt, des pas à pas, et la visualisation des états des variables.

**Exemple avec pdb** :
```python
import pdb

def trouver_max(lst):
    pdb.set_trace()
    max_val = lst[0]
    for val in lst:
        if val > max_val:
            max_val = val
    return max_val

liste = [1, 3, 2, 5, 4]
print("Le maximum est :", trouver_max(liste))
```
Dans cet exemple, `pdb.set_trace()` initie le débogueur, qui arrête l'exécution du programme à cet endroit et vous permet d'inspecter les variables et de contrôler l'exécution étape par étape.

#### Bonnes pratiques :
- **Écrire des tests dès le début** : Développer des tests en même temps que le code pour s'assurer que chaque partie fonctionne correctement dès sa création.
- **Utiliser des assertions** : Les assertions peuvent aider à vérifier que les conditions essentielles sont remplies durant l'exécution, arrêtant le programme si une condition n'est pas respectée.
- **Conservation des logs** : Pour les applications plus grandes, maintenir des fichiers de log peut aider à comprendre le comportement du programme et à diagnostiquer des problèmes après qu'ils se soient produits.

# 12. Bonnes pratiques en Python

## 12.1 Style de codage

Le respect des conventions de style de codage assure que le code est uniforme, lisible et maintenable. Python a une série de recommandations de style de codage connues sous le nom de PEP 8, qui incluent des directives sur la manière de nommer les variables, comment indenter le code, comment structurer les importations, etc.

**Conseils clés de PEP 8** :
- **Indentation** : Utiliser 4 espaces par niveau d'indentation.
- **Longueur de ligne** : Limiter les lignes à 79 caractères.
- **Imports** : Ils doivent être placés en haut du fichier, un par ligne, groupés par :
	- Bibliothèque standard
	- Bibliothèques tierces
	- Modules locaux/application
- **Espacements dans les expressions et les instructions** : Utiliser des espaces autour des opérateurs et après les virgules, mais pas directement à l'intérieur des crochets, des parenthèses ou des accolades.
- **Conventions de nommage** : Utiliser `Snake_case` pour les fonctions et les variables, `CamelCase` pour les noms de classe.

#### Exemple de code conforme à PEP 8 :
```python
import os
import sys

def calculer_somme(x, y):
    # Exemple de fonction bien documentée
    return x + y

class MaClasse:
    def methode_exemple(self):
        pass

# Utilisation de la fonction
resultat = calculer_somme(5, 3)
print(resultat)
```

## 12.2 Documentation

Documenter le code est crucial pour qu'il soit compréhensible non seulement pour les autres, mais souvent pour vous-même dans le futur. Python utilise les docstrings pour intégrer la documentation directement dans le code. Les docstrings sont des chaînes de caractères placées juste après la définition d'une fonction, méthode, classe ou module, et sont utilisées par des outils tels que `help()` pour afficher la documentation.

**Exemple de docstring** :
```python
def additionner(a, b):
    """
    Additionne deux nombres et retourne le résultat.

    Paramètres:
    a (int ou float) : premier nombre à additionner
    b (int ou float) : deuxième nombre à additionner

    Retourne:
    int ou float : la somme de a et b
    """
    return a + b

# Exemple d'utilisation de la fonction avec sa docstring
resultat = additionner(10, 20)
print(resultat)
```

Dans cet exemple, la docstring explique clairement ce que fait la fonction `additionner`, quels paramètres elle prend, et ce qu'elle retourne.

## Bonnes pratiques :
- **Rédiger des docstrings pour toutes les fonctions publiques, classes, et modules** : Assurez-vous que chaque élément de l'API publique a une docstring claire.
- **Utiliser des outils de vérification de style** : Des outils comme Flake8, Pylint, ou Black peuvent aider à vérifier la conformité de votre code avec PEP 8 et d'autres bonnes pratiques.
- **Réviser régulièrement le code** : Organiser des revues de code entre pairs pour maintenir la qualité et la conformité aux bonnes pratiques.