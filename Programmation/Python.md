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

#### 13. Mots-clés python
- **Tableau récapitulatif** : Mots-clés en Python et leur utilisation respective.

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

| Type de données | Description                                                    | Exemples                |
|-----------------|----------------------------------------------------------------|-------------------------|
| `int`           | Nombres entiers sans limite de taille spécifique.              | `10`, `-3`, `42`        |
| `float`         | Nombres à virgule flottante, pour les calculs décimaux.        | `3.14`, `-0.001`, `2.0` |
| `str`           | Séquences de caractères encodées en texte, immuables.          | `'Hello'`, `"world"`    |
| `bool`          | Type booléen qui ne peut être que `True` ou `False`.           | `True`, `False`         |

### Détails supplémentaires :

- **`int` (Nombres entiers)**
  - Pas de limite de taille, contrairement à beaucoup d'autres langages.
  - Peut être converti en `float` pour les besoins de calculs nécessitant des décimales.

- **`float` (Nombres à virgule flottante)**
  - Supporte des opérations telles que l'addition, la soustraction, la multiplication, etc.
  - Peut perdre en précision lors de calculs très spécifiques et complexes.

- **`str` (Chaînes de caractères)**
  - Immuables, ce qui signifie que toute modification crée une nouvelle chaîne.
  - Peuvent être concaténées avec `+`, répétées avec `*`, et indexées par des crochets `[]`.

- **`bool` (Booléens)**
  - Sous-classe de `int`, où `True` équivaut à `1` et `False` à `0`.
  - Utile dans les contrôles de flux et les conditions.

**Exemple en code** :
```python
nombre = 10        # Un entier
pi = 3.14          # Un flottant
message = "Bonjour"  # Une chaîne de caractères
actif = True       # Un booléen
```

## 2.3 Opérateurs

Python offre une gamme complète d'opérateurs pour effectuer des calculs arithmétiques, des comparaisons et des opérations logiques. Ces opérateurs comprennent :

| Catégorie               | Opérateurs                            | Description                                                                                             |
|-------------------------|---------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Arithmétiques**       | `+`, `-`, `*`, `/`, `//`, `%`, `**`   | Utilisés pour effectuer des calculs basiques ainsi que des opérations mathématiques avancées.           |
| **De comparaison**      | `==`, `!=`, `<`, `>`, `<=`, `>=`      | Utilisés pour comparer des valeurs entre elles, retournent un booléen.                                  |
| **Logiques**            | `and`, `or`, `not`                    | Utilisés pour combiner des conditions logiques, retournent un booléen.                                  |
| **D'assignation**       | `=`, `+=`, `-=`, `*=`, `/=`, etc.     | Utilisés pour assigner des valeurs aux variables ainsi que pour modifier et assigner en une opération.  |

### Détails supplémentaires :

- **Opérateurs arithmétiques**
  - `+` : Addition
  - `-` : Soustraction
  - `*` : Multiplication
  - `/` : Division (résultat en float)
  - `//` : Division entière (sans les décimales)
  - `%` : Modulo (reste de la division)
  - `**` : Puissance

- **Opérateurs de comparaison**
  - `==` : Égal à
  - `!=` : Différent de
  - `<` : Inférieur à
  - `>` : Supérieur à
  - `<=` : Inférieur ou égal à
  - `>=` : Supérieur ou égal à

- **Opérateurs logiques**
  - `and` : Opération ET logique
  - `or` : Opération OU logique
  - `not` : Négation logique

- **Opérateurs d'assignation**
  - `=` : Assignation
  - `+=` : Ajoute à la variable et assigne
  - `-=` : Soustrait de la variable et assigne
  - `*=` : Multiplie la variable et assigne
  - `/=` : Divise la variable et assigne
  - D'autres opérateurs combinés existent pour `//`, `%`, `**`, etc., fonctionnant de manière similaire.

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

| Méthode             | Description                                                                                     |
|---------------------|-------------------------------------------------------------------------------------------------|
| **Création**        | `liste = []` Utilisation de crochets pour créer une liste vide.                                 |
| **Accès aux éléments** | `liste[index]` Accès aux éléments par leur index, où l'indexation commence à zéro.              |
| **append(x)**       | Ajoute un élément `x` à la fin de la liste.                                                     |
| **extend(iterable)**| Étend la liste en ajoutant tous les éléments de l'itérable à la fin.                            |
| **insert(index, x)**| Insère un élément `x` à la position donnée `index`.                                             |
| **remove(x)**       | Supprime le premier élément dont la valeur est `x`. Lève une ValueError si l'élément n'existe pas.|
| **pop(index=-1)**   | Supprime l'élément à la position donnée et le retourne. Par défaut, supprime et retourne le dernier élément. |
| **clear()**         | Supprime tous les éléments de la liste.                                                         |
| **index(x, start=0, end=len(list))** | Retourne l'index du premier élément dont la valeur est `x`. Lève une ValueError si non trouvé. |
| **count(x)**        | Retourne le nombre de fois que `x` apparaît dans la liste.                                      |
| **sort(key=None, reverse=False)** | Trie les éléments de la liste in situ (les modifications sont appliquées sur la liste originale).|
| **reverse()**       | Inverse les éléments de la liste in situ.                                                       |
| **copy()**          | Retourne une copie superficielle de la liste.                                                   |

### Exemples d'utilisation

```python
liste = [3, 1, 4, 1, 5, 9, 2, 6]

# Append
liste.append(5)
print(liste)  # [3, 1, 4, 1, 5, 9, 2, 6, 5]

# Extend
liste.extend([7, 8])
print(liste)  # [3, 1, 4, 1, 5, 9, 2, 6, 5, 7, 8]

# Insert
liste.insert(2, 'inserted')
print(liste)  # [3, 1, 'inserted', 4, 1, 5, 9, 2, 6, 5, 7, 8]

# Remove
liste.remove('inserted')
print(liste)  # [3, 1, 4, 1, 5, 9, 2, 6, 5, 7, 8]

# Pop
last_item = liste.pop()
print(last_item)  # 8
print(liste)  # [3, 1, 4, 1, 5, 9, 2, 6, 5, 7]

# Sort
liste.sort()
print(liste)  # [1, 1, 2, 3, 4, 5, 5, 6, 7, 9]

# Reverse
liste.reverse()
print(liste)  # [9, 7, 6, 5, 5, 4, 3, 2, 1, 1]

# Index
print(liste.index(5))  # 3

# Count
print(liste.count(1))  # 2

# Clear
liste.clear()
print(liste)  # []
```

```python
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

| Opération / Méthode  | Description                                                                                         |
|----------------------|-----------------------------------------------------------------------------------------------------|
| **Création**         | `mon_tuple = (1, 2, 3)` Utilisation de parenthèses pour créer un tuple.                             |
| **Accès aux éléments** | `mon_tuple[index]` Accès aux éléments par leur index, où l'indexation commence à zéro.              |
| **count(x)**         | Compte le nombre d'occurrences de `x` dans le tuple.                                                |
| **index(x)**         | Trouve la première occurrence de `x` dans le tuple et retourne son index.                           |
| **Concaténation**    | `tuple1 + tuple2` Concatène deux tuples pour en former un nouveau.                                  |
| **Répétition**       | `tuple1 * 3` Crée un nouveau tuple qui répète les éléments de `tuple1` trois fois.                  |
| **Longueur**         | `len(tuple1)` Retourne le nombre d'éléments dans le tuple.                                          |
| **Min/Max**          | `min(tuple1)`, `max(tuple1)` Retourne les valeurs minimales et maximales dans le tuple.             |
| **Immuabilité**      | Les tuples ne peuvent pas être modifiés après leur création (pas de méthodes `append`, `remove`).   |

### Exemples d'utilisation

```python
# Création d'un tuple
mon_tuple = (1, 2, 3, 2, 4)

# Accéder aux éléments
print(mon_tuple[1])  # Affiche 2

# Compter les occurrences d'un élément
print(mon_tuple.count(2))  # Affiche 2

# Trouver l'index d'un élément
print(mon_tuple.index(3))  # Affiche 2

# Concaténation de tuples
nouveau_tuple = mon_tuple + (5, 6)
print(nouveau_tuple)  # Affiche (1, 2, 3, 2, 4, 5, 6)

# Répétition de tuples
repete_tuple = mon_tuple * 2
print(repete_tuple)  # Affiche (1, 2, 3, 2, 4, 1, 2, 3, 2, 4)

# Longueur du tuple
print(len(mon_tuple))  # Affiche 5

# Min et Max
print(min(mon_tuple))  # Affiche 1
print(max(mon_tuple))  # Affiche 4
```

## 5.3 Dictionnaires

Les dictionnaires en Python sont des collections non ordonnées de paires clé-valeur. Ils sont optimisés pour récupérer des valeurs lorsque la clé est connue.

**Opérations de base** :
- **Création** : Utilisation de `{}` ou `dict()`.
- **Accès aux éléments** : Accès via les clés.

| Méthode / Opération   | Description                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------|
| **Création**          | `mon_dict = {'cle1': 'valeur1', 'cle2': 'valeur2'}` Crée un dictionnaire avec des paires clé-valeur.        |
| **Accès aux éléments**| `mon_dict['cle1']` Accède à l'élément par la clé. Si la clé n'existe pas, lève une `KeyError`.               |
| **get(key, default=None)** | Retourne la valeur pour une clé donnée. Retourne `default` si la clé n'existe pas.                         |
| **setdefault(key, default=None)** | Retourne la valeur de la clé si elle existe, sinon ajoute la clé avec la valeur `default`.              |
| **update({key: value})** | Ajoute plusieurs paires clé-valeur à partir d'un autre dictionnaire ou d'un iterable de paires.           |
| **keys()**            | Retourne un nouvel affichage des clés dans le dictionnaire.                                                  |
| **values()**          | Retourne un nouvel affichage des valeurs dans le dictionnaire.                                               |
| **items()**           | Retourne un nouvel affichage des paires clé-valeur sous forme de tuples.                                      |
| **pop(key)**          | Supprime la clé et retourne la valeur associée. Si la clé n'est pas trouvée, lève une `KeyError`.            |
| **popitem()**         | Supprime et retourne une paire (clé, valeur) arbitraire. Lève une `KeyError` si le dictionnaire est vide.    |
| **clear()**           | Supprime tous les éléments du dictionnaire.                                                                  |

### Exemples d'utilisation

```python
# Création d'un dictionnaire
mon_dict = {'nom': 'Alice', 'age': 25}

# Accéder aux éléments
print(mon_dict['nom'])  # Affiche 'Alice'

# Utilisation de get
print(mon_dict.get('age'))  # Affiche 25
print(mon_dict.get('adresse', 'Non spécifiée'))  # Affiche 'Non spécifiée'

# Ajout / Mise à jour d'une clé
mon_dict['adresse'] = '123 rue principale'
mon_dict.update({'profession': 'Développeur'})

# Parcourir les clés et les valeurs
for cle, valeur in mon_dict.items():
    print(f"{cle}: {valeur}")

# Supprimer une clé
age = mon_dict.pop('age')
print(f"Age supprimé: {age}")

# Supprimer tous les éléments
mon_dict.clear()
print(mon_dict)  # Affiche {}
```

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

| Méthode / Opération   | Description                                                                                              |
|-----------------------|----------------------------------------------------------------------------------------------------------|
| **Création**          | `mon_ensemble = {1, 2, 3}` Crée un ensemble. Les doublons sont automatiquement éliminés.                 |
| **add(x)**            | Ajoute un élément `x` à l'ensemble, si `x` n'est pas déjà présent.                                       |
| **update([x, y, ...])** | Ajoute plusieurs éléments à l'ensemble.                                                                 |
| **remove(x)**         | Supprime `x` de l'ensemble. Lève une `KeyError` si `x` n'est pas trouvé.                                |
| **discard(x)**        | Supprime `x` de l'ensemble si présent. Ne lève pas d'erreur si `x` n'est pas trouvé.                     |
| **pop()**             | Supprime et retourne un élément arbitraire de l'ensemble. Lève une `KeyError` si l'ensemble est vide.    |
| **clear()**           | Supprime tous les éléments de l'ensemble.                                                                |
| **union(\*others)**   | Retourne un nouvel ensemble contenant tous les éléments de l'ensemble et de tous les `others`.           |
| **intersection(\*others)** | Retourne un nouvel ensemble avec les éléments communs à l'ensemble et à tous les `others`.            |
| **difference(\*others)** | Retourne un nouvel ensemble avec les éléments de l'ensemble qui ne sont pas dans les `others`.       |
| **symmetric_difference(other)** | Retourne un nouvel ensemble avec les éléments qui sont dans l'un des ensembles mais pas dans les deux. |
| **issubset(other)**   | Retourne `True` si l'ensemble est un sous-ensemble de `other`, sinon `False`.                            |
| **issuperset(other)** | Retourne `True` si l'ensemble est un sur-ensemble de `other`, sinon `False`.                             |
| **isdisjoint(other)** | Retourne `True` si l'ensemble n'a aucun élément en commun avec `other`, sinon `False`.                   |

### Exemples d'utilisation

```python
# Création d'un ensemble
mon_ensemble = {1, 2, 3}

# Ajouter un élément
mon_ensemble.add(4)
print(mon_ensemble)  # {1, 2, 3, 4}

# Ajouter plusieurs éléments
mon_ensemble.update([5, 6, 7])
print(mon_ensemble)  # {1, 2, 3, 4, 5, 6, 7}

# Supprimer un élément
mon_ensemble.remove(7)
print(mon_ensemble)  # {1, 2, 3, 4, 5, 6}

# Intersection d'ensembles
autre_ensemble = {4, 5, 6, 7}
print(mon_ensemble.intersection(autre_ensemble))  # {4, 5, 6}

# Union d'ensembles
print(mon_ensemble.union(autre_ensemble))  # {1, 2, 3, 4, 5, 6, 7}

# Différence symétrique
print(mon_ensemble.symmetric_difference(autre_ensemble))  # {1, 2, 3, 7}

# Vérifier si un ensemble est sous-ensemble d'un autre
print({1, 2}.issubset(mon_ensemble))  # True
```

# 6) Manipulation de fichiers en Python

## 6.1 Lecture et écriture de fichiers

La manipulation de fichiers en Python est une compétence essentielle, permettant aux programmes de lire des données depuis des fichiers et d'y écrire des données. Python simplifie la gestion des fichiers grâce à des fonctions intégrées comme

| Méthode                    | Description                                                                                             |
| -------------------------- | ------------------------------------------------------------------------------------------------------- |
| **read(size=-1)**          | Lit et retourne jusqu'à `size` caractères du fichier. Lit jusqu'à la fin si `size` est omis ou négatif. |
| **readline(size=-1)**      | Lit la ligne suivante du fichier, jusqu'à `size` caractères.                                            |
| **readlines(hint=-1)**     | Lit et retourne une liste de lignes du fichier. `hint` peut limiter le nombre de lignes retournées.     |
| **write(string)**          | Écrit la chaîne `string` dans le fichier et retourne le nombre de caractères écrits.                    |
| **writelines(lines)**      | Écrit une liste de `lines` dans le fichier (ne rajoute pas automatiquement de nouvelles lignes).        |
| **seek(offset, whence=0)** | Déplace le curseur à la position `offset` relative à `whence` (0: début, 1: position actuelle, 2: fin). |
| **tell()**                 | Retourne la position actuelle du curseur dans le fichier.                                               |
| **flush()**                | Rafraîchit le tampon d'écriture du fichier.                                                             |
| **close()**                | Ferme le fichier. Note : pas nécessaire avec `with`, car la fermeture est automatique.                  |
## Exemples d'utilisation

```python
# Lecture de contenu
with open('exemple.txt', 'r') as f:
    content = f.read()
    print(content)  # Affiche le contenu du fichier

# Lecture ligne par ligne
with open('exemple.txt', 'r') as f:
    for line in f:
        print(line, end='')  # Affiche chaque ligne du fichier

# Écriture dans un fichier
with open('output.txt', 'w') as f:
    f.write("Bonjour monde\n")

# Écriture de plusieurs lignes
lines = ["Première ligne\n", "Deuxième ligne\n"]
with open('output.txt', 'a') as f:
    f.writelines(lines)

# Déplacer le curseur
with open('exemple.txt', 'r+') as f:
    f.seek(10)  # Déplace le curseur à la position 10
    print(f.read())  # Lit à partir de la position 10

# Obtenir la position du curseur
with open('exemple.txt', 'r') as f:
    data = f.readline()
    print(f"Le curseur est à la position : {f.tell()}")

# Rafraîchir les écritures dans un fichier
with open('output.txt', 'a') as f:
    f.write("Ajout en fin de fichier")
    f.flush()  # Assure que "Ajout en fin de fichier" est écrit avant de continuer
```

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

| Module            | Description                                                         |
|-------------------|---------------------------------------------------------------------|
| `os`              | Interaction avec le système d'exploitation.                        |
| `sys`             | Accès aux fonctions et objets spécifiques à l'interpréteur.         |
| `math`            | Fonctions mathématiques.                                           |
| `datetime`        | Manipulation des dates et des heures.                              |
| `json`            | Encodage et décodage JSON.                                         |
| `http`            | Gestion des requêtes HTTP.                                         |
| `urllib`          | Manipulation d'URLs.                                               |
| `random`          | Génération de nombres aléatoires.                                  |
| `collections`     | Conteneurs de données alternatives.                                |
| `functools`       | Fonctions de haut niveau : opérations sur d'autres fonctions.      |
| `itertools`       | Création d'itérateurs pour des boucles efficaces.                  |
| `re`              | Manipulation d'expressions régulières.                             |
| `subprocess`      | Lancement de sous-processus.                                       |
| `multiprocessing` | Parallélisme basé sur des processus.                               |
| `threading`       | Gestion de threads.                                                |
| `pickle`          | Sérialisation et désérialisation d'objets Python.                  |
| `socket`          | Interface de bas niveau pour les communications réseau.            |
| `ssl`             | Prise en charge de TLS/SSL pour les objets socket.                 |
| `hashlib`         | Fonctions de hachage.                                              |
| `sqlite3`         | Interaction avec des bases de données SQLite.                      |
| `pathlib`         | Manipulation des chemins du système de fichiers de manière orientée objet. |
| `argparse`        | Analyse des arguments et options de la ligne de commande.          |
| `logging`         | Enregistrement de journaux, débogage et autres diagnostics.        |
| `unittest`        | Framework de test unitaire.                                        |
| `pdb`             | Débogage des programmes Python.                                    |
| `tkinter`         | Outils pour créer des interfaces graphiques.                       |
| `csv`             | Lecture et écriture de fichiers CSV.                               |
| `xml.etree.ElementTree` | Manipulation simple et efficace des données XML.              |
* Pour lister tous les modules standards disponibles : `python -m pydoc modules`

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


# 12) Gestion de la mémoire

Les programmes sur un système d'exploitation utilisent la mémoire pour stocker des instructions de programme, des données et pour gérer l'exécution des processus. Voici une explication de la manière dont cela fonctionne généralement, suivi par les spécificités de la gestion de la mémoire en Python.
### Gestion de la mémoire dans un système d'exploitation
1. **Allocation de mémoire** :
   - Les systèmes d'exploitation allouent de la mémoire aux programmes à travers un espace de mémoire virtuelle, qui est séparé de la mémoire physique réelle du système. Chaque processus exécuté par le système d'exploitation dispose de son propre espace d'adressage virtuel.
2. **Pagination et Swap** :
   - La mémoire virtuelle est gérée en utilisant des unités appelées pages. Le système d'exploitation mappe ces pages à la mémoire physique. Lorsque la mémoire physique est pleine, le système peut transférer (swapper) certaines pages vers un espace de stockage sur le disque dur (swap) pour libérer de la mémoire.
3. **Gestion du cache** :
   - Les données fréquemment utilisées peuvent être stockées dans un cache de mémoire rapide pour améliorer les performances d'accès aux données.
4. **Garbage Collection** (GC) :
   - Certains langages de haut niveau comme Java utilisent un mécanisme appelé ramasse-miettes pour automatiser la gestion de la mémoire. Le GC se charge de libérer automatiquement la mémoire qui n'est plus utilisée par le programme.

### Gestion de la mémoire en Python
Python simplifie la gestion de la mémoire grâce à plusieurs mécanismes intégrés, principalement le comptage de références et le garbage collector.
1. **Comptage de références** :
   - Python utilise le comptage de références comme méthode principale pour gérer la mémoire. Chaque objet en Python a un compteur qui garde trace du nombre de références qui pointent vers cet objet. Lorsque ce nombre tombe à zéro, cela signifie qu'aucune référence n'existe plus pour cet objet, et la mémoire peut être libérée.
2. **Garbage Collection** :
   - Python (CPython en particulier) possède également un ramasse-miettes pour détecter et libérer des cycles de références qui ne peuvent pas être nettoyés par le comptage de références seul. Cela peut arriver lorsque deux objets ou plus se réfèrent mutuellement mais ne sont plus accessibles depuis le code.
3. **Pools de mémoire** :
   - Python utilise un système de pools de mémoire pour optimiser les petites allocations et désallocations. Par exemple, le gestionnaire de mémoire de Python, appelé pymalloc, alloue des blocs de mémoire en groupes pour gérer les objets de petite taille efficacement.
4. **Fragmentation** :
   - Python tente de minimiser la fragmentation de la mémoire en maintenant des listes de blocs libres de tailles variées et en réutilisant les blocs libérés pour des allocations futures de tailles similaires.

Ces mécanismes assurent que Python, tout en étant simple d'utilisation pour le programmeur, gère efficacement la mémoire en arrière-plan, réduisant les fuites de mémoire et optimisant l'utilisation de la mémoire pour des programmes de grande taille ou longtemps en exécution. Pour les développeurs Python, cela signifie moins de soucis concernant les détails de l'allocation et la libération de mémoire, permettant de se concentrer davantage sur la logique du programme.

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



# 13) Mots-clés et built-in functions
## 13.1 Tableau récapitulatif mots-clés
Voici un tableau Markdown qui décrit les mots-clés en Python et leur utilisation respective. Ce tableau couvre les mots-clés les plus communs et explique brièvement la fonction de chaque mot.

| Mot-clé    | Description                                                                                             | Particularités                               |
|------------|---------------------------------------------------------------------------------------------------------|----------------------------------------------|
| `False`    | Représente la valeur booléenne fausse.                                                                  | Une des constantes de vérité de Python.      |
| `None`     | Représente l'absence de valeur.                                                                         | Utilisé pour signaler l'absence de valeur.   |
| `True`     | Représente la valeur booléenne vraie.                                                                   | Une des constantes de vérité de Python.      |
| `and`      | Opérateur logique ET.                                                                                   | Utilisé pour tester si toutes les conditions sont vraies. |
| `as`       | Utilisé dans les instructions `with` et `import` pour renommer un module ou gérer des contextes.        | Permet un aliasing de module ou une gestion de contexte simplifiée. |
| `assert`   | Déclaration pour aider à déboguer en vérifiant que les conditions suivantes sont vraies.                | S'il échoue, lève une `AssertionError`.      |
| `async`    | Définit une fonction comme coroutine, utilisée avec `await`.                                            | Introduit dans Python 3.5 pour la programmation asynchrone. |
| `await`    | Utilisé pour attendre qu'une coroutine soit terminée.                                                   | Doit être utilisé à l'intérieur d'une fonction `async`. |
| `break`    | Interrompt la boucle englobante la plus proche.                                                         | Utilisé dans les boucles `while` et `for`.   |
| `class`    | Utilisé pour définir une nouvelle classe.                                                               |                                              |
| `continue` | Passe à l'itération suivante de la boucle englobante la plus proche.                                     | Utilisé dans les boucles `while` et `for`.   |
| `def`      | Définit une fonction ou une méthode.                                                                    |                                              |
| `del`      | Supprime un objet de Python.                                                                            | Peut être utilisé pour supprimer des variables, des éléments de liste, des clés de dictionnaire, etc. |
| `elif`     | Abréviation de "else if". Partie d'une structure de condition `if`.                                     |                                              |
| `else`     | Bloc qui s'exécute si les conditions `if` ou `elif` précédentes ne sont pas vraies.                     |                                              |
| `except`   | Capture une exception si elle est levée dans le bloc `try` associé.                                     | Peut spécifier un type d'exception pour la capture sélective. |
| `finally`  | Bloc qui s'exécute après les blocs `try` et `except`, quel que soit le résultat de ces derniers.        | Utilisé pour les actions de nettoyage.       |
| `for`      | Définit une boucle for qui itère sur une séquence.                                                      |                                              |
| `from`     | Utilisé avec `import` pour spécifier le module à partir duquel importer.                                |                                              |
| `global`   | Déclare qu'une variable appartient à la portée globale.                                                 |                                              |
| `if`       | Introduit une conditionnelle.                                                                           |                                              |
| `import`   | Utilisé pour importer des modules ou des objets spécifiques dans le module actuel.                      |                                              |
| `in`       | Vérifie si une valeur est dans une séquence ou itère sur une séquence dans une boucle `for`.            |                                              |
| `is`       | Teste l'identité des objets; vérifie si deux références pointent vers le même objet.                    |                                              |
| `lambda`   | Crée une fonction anonyme (une fonction sans nom).                                                      | Utilisé pour de petites fonctions jetables.  |
| `nonlocal` | Déclare qu'une variable appartient à la portée englobante la plus proche, excluant la portée globale.   | Utilisé dans les fonctions imbriquées.       |
| `not`      | Opérateur logique de négation.                                                                          |                                              |
| `or`       | Opérateur logique OU.                                                                                   | Utilisé pour tester si au moins une condition est vraie. |
| `pass`     | Une instruction qui ne fait rien; utilisé comme un remplisseur syntaxique.                              |                                              |
| `raise`    | Utilisé pour lever une exception spécifiée.                                                             |                                              |
| `return`   | Termine une fonction et éventuellement retourne une expression.                                         |                                              |
| `try`      | Début d'un bloc de gestion d'exceptions.                                                                |                                              |
| `while`    | Définit une boucle while.                                                                               |                                              |
| `with`     | Simplifie l'utilisation des ressources qui nécessitent des opérations de nettoyage.                     |                                              |
| `yield`    | Utilisé pour transformer une fonction en générateur.                                                    | Renvoie une valeur et pause l'exécution de la fonction. |

## 13.2 Tableau récapitulatif built-in functions

| Fonction      | Description                                                                   | Exemple                                           |
|---------------|-------------------------------------------------------------------------------|---------------------------------------------------|
| `abs()`       | Retourne la valeur absolue d'un nombre.                                       | `abs(-5)` donne `5`                               |
| `all()`       | Retourne `True` si tous les éléments d'un itérable sont vrais.                | `all([True, True, True])` donne `True`            |
| `any()`       | Retourne `True` si un élément d'un itérable est vrai.                         | `any([False, True, False])` donne `True`          |
| `bool()`      | Convertit une valeur en booléen.                                              | `bool(0)` donne `False`                           |
| `chr()`       | Retourne le caractère qui correspond à un entier ASCII.                       | `chr(97)` donne `'a'`                             |
| `dir()`       | Liste les attributs et méthodes d'un objet sans les valeurs.                  | `dir([])` liste les méthodes de liste             |
| `divmod()`    | Retourne le quotient et le reste de la division entière de deux nombres.      | `divmod(9, 4)` donne `(2, 1)`                     |
| `enumerate()` | Retourne un objet énuméré.                                                    | `list(enumerate(['a', 'b']))` donne `[(0, 'a'), (1, 'b')]` |
| `filter()`    | Filtre les éléments d'un itérable.                                            | `list(filter(lambda x: x > 0, [-1, 0, 1]))` donne `[1]` |
| `float()`     | Convertit une chaîne ou un nombre en un nombre à virgule flottante.           | `float('3.14')` donne `3.14`                      |
| `getattr()`   | Retourne la valeur de l'attribut d'un objet.                                  | `getattr(obj, 'attribut')`                        |
| `hasattr()`   | Vérifie si un objet possède un attribut spécifié.                             | `hasattr(obj, 'attribut')` donne `True` ou `False`|
| `hash()`      | Retourne la valeur de hachage d'un objet.                                     | `hash('test')`                                    |
| `help()`      | Appelle le système d'aide intégré.                                            | `help(str)`                                       |
| `hex()`       | Convertit un entier en une chaîne hexadécimale.                               | `hex(255)` donne `'0xff'`                         |
| `id()`        | Retourne l'identifiant « identité » d'un objet.                               | `id(obj)`                                         |
| `input()`     | Permet à l'utilisateur de saisir une chaîne.                                  | `nom = input('Entrez votre nom: ')`               |
| `int()`       | Convertit une chaîne ou un nombre en un entier.                               | `int('10')` donne `10`                            |
| `isinstance()`| Vérifie si un objet est une instance d'une classe ou d'un tuple de classes.   | `isinstance(5, int)` donne `True`                 |
| `len()`       | Retourne le nombre d'éléments dans un objet.                                  | `len([1, 2, 3])` donne `3`                        |
| `list()`      | Convertit un itérable en liste.                                               | `list('abc')` donne `['a', 'b', 'c']`              |
| `map()`       | Applique une fonction à tous les éléments d'un itérable.                      | `list(map(lambda x: x * 2, [1, 2, 3]))` donne `[2, 4, 6]` |
| `max()`       | Retourne le plus grand élément dans un itérable.                              | `max([1, 2, 3])` donne `3`                        |
| `min()`       | Retourne le plus petit élément dans un itérable.                              | `min([1, 2, 3])` donne `1`                        |
| `ord()`       | Convertit un caractère en son code ASCII correspondant.                       | `ord('a')` donne `97`                             |
| `print()`     | Affiche des arguments avec une séparation et une fin de ligne spécifiées.     | `print('Hello, world!')`                          |
| `range()`     | Génère une séquence de nombres.                                               | `list(range(5))` donne `[0, 1, 2, 3, 4]`          |
| `round()`     | Arrondit un nombre à virgule flottante à un certain nombre de décimales.      | `round(3.14159, 2)` donne `3.14`                  |
| `set()`       | Crée un nouvel ensemble, une collection non ordonnée d'éléments uniques.      | `set([1, 2, 2, 3])` donne `{1, 2, 3}`             |
| `sorted()`    | Retourne une nouvelle liste triée à partir des éléments d'un itérable.        | `sorted([3, 1, 2])` donne `[1, 2, 3]`             |
| `str()`       | Convertit un objet en chaîne de caractères.                                   | `str(10)` donne `'10'`                            |
| `sum()`       | Somme tous les éléments d'un itérable.                                        | `sum([1, 2, 3])` donne `6`                        |
| `type()`      | Retourne le type de l'objet.                                                  | `type('Hello')` donne `<class 'str'>`             |
| `zip()`       | Agrège les éléments de deux ou plusieurs itérables.                           | `list(zip([1, 2], ['a', 'b']))` donne `[(1, 'a'), (2, 'b')]` |
