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


## 1.3 Fonctionnement du langage
### Composants du langage Python :
1. **Langage Python** : Python est un langage de programmation de haut niveau, conçu pour être simple à lire et à écrire. Il offre une syntaxe claire et expressive qui facilite le développement de logiciels.
2. **Interpréteur Python** : L'interpréteur Python est le programme responsable de l'exécution du code Python. Il comprend la syntaxe et les règles du langage Python, et traduit ces instructions en actions exécutables par l'ordinateur. L'interpréteur Python analyse le code source, le compile en bytecode et l'exécute ligne par ligne.
3. **Bytecode** : Le bytecode Python est un langage intermédiaire qui est généré par l'interpréteur Python à partir du code source Python. Il s'agit d'un ensemble d'instructions bas niveau spécifiques à la machine virtuelle Python (PVM). Le bytecode est portable et indépendant de la plate-forme, ce qui signifie qu'il peut être exécuté sur n'importe quelle plate-forme prenant en charge la PVM.
4. **Machine Virtuelle Python (PVM)** : La PVM est le composant responsable de l'exécution du bytecode Python. Elle agit comme une couche d'abstraction entre le code Python et le système d'exploitation sous-jacent. La PVM prend en charge l'exécution des instructions bytecode et les traduit en instructions machine spécifiques à la plate-forme sur laquelle elle s'exécute. La PVM offre également des fonctionnalités telles que la gestion de la mémoire, la gestion des exceptions et l'interaction avec le système d'exploitation.
### Fonctionnement de l'exécution d'un programme Python :
1. **Analyse du code source** : Lorsque tu exécutes un programme Python, l'interpréteur Python commence par analyser le code source pour détecter d'éventuelles erreurs de syntaxe.
2. **Compilation en bytecode** : Une fois que le code source est analysé avec succès, l'interpréteur Python compile le code en bytecode. Chaque ligne du code source est transformée en instructions bytecode, qui sont plus proches du langage machine, mais toujours indépendantes de la plate-forme.
3. **Exécution du bytecode par la PVM** : Le bytecode ainsi généré est ensuite exécuté par la machine virtuelle Python (PVM). La PVM prend en charge l'exécution des instructions bytecode et les traduit en instructions machine spécifiques à la plate-forme sur laquelle elle s'exécute.
4. **Gestion de la mémoire et des ressources** : Pendant l'exécution du programme, la PVM gère la mémoire et les ressources nécessaires à son fonctionnement. Elle alloue de la mémoire pour stocker les variables et les objets, et libère automatiquement la mémoire non utilisée grâce à un processus appelé ramasse-miettes (garbage collection).
5. **Interaction avec le système d'exploitation** : La PVM interagit également avec le système d'exploitation sous-jacent pour effectuer des opérations telles que la lecture et l'écriture de fichiers, l'accès au réseau et l'exécution de processus.
### Chronologie détaillée des étapes :

1. **Analyse lexicale et syntaxique** :
   L'interpréteur Python commence par analyser le code source du script Python pour détecter d'éventuelles erreurs de syntaxe. Cette étape consiste à décomposer le code en tokens (mots-clés, identificateurs, opérateurs, etc.) et à vérifier que la structure du code est correcte selon les règles de la syntaxe Python.
2. **Compilation en bytecode** :
   Une fois que le code source a été analysé avec succès, l'interpréteur Python compile le code en bytecode. Chaque ligne du code source est transformée en instructions bytecode, qui sont stockées dans un fichier `.pyc` (fichier de bytecode compilé) ou dans la mémoire si l'optimisation est activée.
3. **Chargement du bytecode** :
   L'interpréteur Python charge le bytecode compilé en mémoire. Si un fichier `.pyc` correspondant au script Python existe déjà et est à jour, l'interpréteur peut utiliser ce bytecode plutôt que de le recompiler à chaque exécution du script, ce qui peut accélérer le processus d'exécution.
4. **Initialisation de la PVM (Python Virtual Machine)** :
   La machine virtuelle Python (PVM) est initialisée pour exécuter le bytecode. Cela implique l'allocation de ressources mémoire nécessaires à l'exécution du programme, ainsi que l'initialisation de divers composants de la PVM tels que la pile d'exécution, le gestionnaire d'exceptions, etc.
5. **Exécution du bytecode** :
   La PVM commence à exécuter le bytecode ligne par ligne. Chaque instruction bytecode est récupérée, décodée et exécutée par la PVM. Les opérations courantes incluent l'assignation de variables, les appels de fonctions, les boucles, les conditions, etc.
6. **Gestion de la mémoire** :
   Pendant l'exécution du programme, la PVM gère la mémoire en allouant de l'espace pour stocker les variables, les objets et les données temporaires. La gestion de la mémoire comprend également la collecte des déchets (garbage collection), qui consiste à libérer la mémoire occupée par les objets qui ne sont plus utilisés.
7. **Interaction avec le système d'exploitation** :
   Pendant l'exécution du script, la PVM peut interagir avec le système d'exploitation sous-jacent pour effectuer des opérations telles que la lecture et l'écriture de fichiers, l'accès au réseau, l'exécution de processus externes, etc.
8. **Fin de l'exécution** :
   Lorsque le programme atteint la fin du script Python, ou lorsqu'une instruction `return` est rencontrée, l'exécution du programme se termine. La PVM nettoie les ressources utilisées par le programme et libère la mémoire avant de se terminer.
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

| str.method()                                                                   | Description                                                                                   |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| [capitalize()](https://www.w3schools.com/python/ref_string_capitalize.asp)     | Converts the first character to upper case                                                    |
| [casefold()](https://www.w3schools.com/python/ref_string_casefold.asp)         | Converts string into lower case                                                               |
| [center()](https://www.w3schools.com/python/ref_string_center.asp)             | Returns a centered string                                                                     |
| [count()](https://www.w3schools.com/python/ref_string_count.asp)               | Returns the number of times a specified value occurs in a string                              |
| [encode()](https://www.w3schools.com/python/ref_string_encode.asp)             | Returns an encoded version of the string                                                      |
| [endswith()](https://www.w3schools.com/python/ref_string_endswith.asp)         | Returns true if the string ends with the specified value                                      |
| [expandtabs()](https://www.w3schools.com/python/ref_string_expandtabs.asp)     | Sets the tab size of the string                                                               |
| [find()](https://www.w3schools.com/python/ref_string_find.asp)                 | Searches the string for a specified value and returns the position of where it was found      |
| [format()](https://www.w3schools.com/python/ref_string_format.asp)             | Formats specified values in a string                                                          |
| format_map()                                                                   | Formats specified values in a string                                                          |
| [index()](https://www.w3schools.com/python/ref_string_index.asp)               | Searches the string for a specified value and returns the position of where it was found      |
| [isalnum()](https://www.w3schools.com/python/ref_string_isalnum.asp)           | Returns True if all characters in the string are alphanumeric                                 |
| [isalpha()](https://www.w3schools.com/python/ref_string_isalpha.asp)           | Returns True if all characters in the string are in the alphabet                              |
| [isascii()](https://www.w3schools.com/python/ref_string_isascii.asp)           | Returns True if all characters in the string are ascii characters                             |
| [isdecimal()](https://www.w3schools.com/python/ref_string_isdecimal.asp)       | Returns True if all characters in the string are decimals                                     |
| [isdigit()](https://www.w3schools.com/python/ref_string_isdigit.asp)           | Returns True if all characters in the string are digits                                       |
| [isidentifier()](https://www.w3schools.com/python/ref_string_isidentifier.asp) | Returns True if the string is an identifier                                                   |
| [islower()](https://www.w3schools.com/python/ref_string_islower.asp)           | Returns True if all characters in the string are lower case                                   |
| [isnumeric()](https://www.w3schools.com/python/ref_string_isnumeric.asp)       | Returns True if all characters in the string are numeric                                      |
| [isprintable()](https://www.w3schools.com/python/ref_string_isprintable.asp)   | Returns True if all characters in the string are printable                                    |
| [isspace()](https://www.w3schools.com/python/ref_string_isspace.asp)           | Returns True if all characters in the string are whitespaces                                  |
| [istitle()](https://www.w3schools.com/python/ref_string_istitle.asp)           | Returns True if the string follows the rules of a title                                       |
| [isupper()](https://www.w3schools.com/python/ref_string_isupper.asp)           | Returns True if all characters in the string are upper case                                   |
| [join()](https://www.w3schools.com/python/ref_string_join.asp)                 | Converts the elements of an iterable into a string                                            |
| [ljust()](https://www.w3schools.com/python/ref_string_ljust.asp)               | Returns a left justified version of the string                                                |
| [lower()](https://www.w3schools.com/python/ref_string_lower.asp)               | Converts a string into lower case                                                             |
| [lstrip()](https://www.w3schools.com/python/ref_string_lstrip.asp)             | Returns a left trim version of the string                                                     |
| [maketrans()](https://www.w3schools.com/python/ref_string_maketrans.asp)       | Returns a translation table to be used in translations                                        |
| [partition()](https://www.w3schools.com/python/ref_string_partition.asp)       | Returns a tuple where the string is parted into three parts                                   |
| [replace()](https://www.w3schools.com/python/ref_string_replace.asp)           | Returns a string where a specified value is replaced with a specified value                   |
| [rfind()](https://www.w3schools.com/python/ref_string_rfind.asp)               | Searches the string for a specified value and returns the last position of where it was found |
| [rindex()](https://www.w3schools.com/python/ref_string_rindex.asp)             | Searches the string for a specified value and returns the last position of where it was found |
| [rjust()](https://www.w3schools.com/python/ref_string_rjust.asp)               | Returns a right justified version of the string                                               |
| [rpartition()](https://www.w3schools.com/python/ref_string_rpartition.asp)     | Returns a tuple where the string is parted into three parts                                   |
| [rsplit()](https://www.w3schools.com/python/ref_string_rsplit.asp)             | Splits the string at the specified separator, and returns a list                              |
| [rstrip()](https://www.w3schools.com/python/ref_string_rstrip.asp)             | Returns a right trim version of the string                                                    |
| [split()](https://www.w3schools.com/python/ref_string_split.asp)               | Splits the string at the specified separator, and returns a list                              |
| [splitlines()](https://www.w3schools.com/python/ref_string_splitlines.asp)     | Splits the string at line breaks and returns a list                                           |
| [startswith()](https://www.w3schools.com/python/ref_string_startswith.asp)     | Returns true if the string starts with the specified value                                    |
| [strip()](https://www.w3schools.com/python/ref_string_strip.asp)               | Returns a trimmed version of the string                                                       |
| [swapcase()](https://www.w3schools.com/python/ref_string_swapcase.asp)         | Swaps cases, lower case becomes upper case and vice versa                                     |
| [title()](https://www.w3schools.com/python/ref_string_title.asp)               | Converts the first character of each word to upper case                                       |
| [translate()](https://www.w3schools.com/python/ref_string_translate.asp)       | Returns a translated string                                                                   |
| [upper()](https://www.w3schools.com/python/ref_string_upper.asp)               | Converts a string into upper case                                                             |
| [zfill()](https://www.w3schools.com/python/ref_string_zfill.asp)               | Fills the string with a specified number of 0 values at the beginning                         |
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

| Method                                                             | Description                                                                  |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [append()](https://www.w3schools.com/python/ref_list_append.asp)   | Adds an element at the end of the list                                       |
| [clear()](https://www.w3schools.com/python/ref_list_clear.asp)     | Removes all the elements from the list                                       |
| [copy()](https://www.w3schools.com/python/ref_list_copy.asp)       | Returns a copy of the list                                                   |
| [count()](https://www.w3schools.com/python/ref_list_count.asp)     | Returns the number of elements with the specified value                      |
| [extend()](https://www.w3schools.com/python/ref_list_extend.asp)   | Add the elements of a list (or any iterable), to the end of the current list |
| [index()](https://www.w3schools.com/python/ref_list_index.asp)     | Returns the index of the first element with the specified value              |
| [insert()](https://www.w3schools.com/python/ref_list_insert.asp)   | Adds an element at the specified position                                    |
| [pop()](https://www.w3schools.com/python/ref_list_pop.asp)         | Removes the element at the specified position                                |
| [remove()](https://www.w3schools.com/python/ref_list_remove.asp)   | Removes the first item with the specified value                              |
| [reverse()](https://www.w3schools.com/python/ref_list_reverse.asp) | Reverses the order of the list                                               |
| [sort()](https://www.w3schools.com/python/ref_list_sort.asp)       | Sorts the list                                                               |

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

| Method                                                          | Description                                                                             |
| --------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [count()](https://www.w3schools.com/python/ref_tuple_count.asp) | Returns the number of times a specified value occurs in a tuple                         |
| [index()](https://www.w3schools.com/python/ref_tuple_index.asp) | Searches the tuple for a specified value and returns the position of where it was found |

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

| Method                                                                         | Description                                                                                                 |
| ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| [clear()](https://www.w3schools.com/python/ref_dictionary_clear.asp)           | Removes all the elements from the dictionary                                                                |
| [copy()](https://www.w3schools.com/python/ref_dictionary_copy.asp)             | Returns a copy of the dictionary                                                                            |
| [fromkeys()](https://www.w3schools.com/python/ref_dictionary_fromkeys.asp)     | Returns a dictionary with the specified keys and value                                                      |
| [get()](https://www.w3schools.com/python/ref_dictionary_get.asp)               | Returns the value of the specified key                                                                      |
| [items()](https://www.w3schools.com/python/ref_dictionary_items.asp)           | Returns a list containing a tuple for each key value pair                                                   |
| [keys()](https://www.w3schools.com/python/ref_dictionary_keys.asp)             | Returns a list containing the dictionary's keys                                                             |
| [pop()](https://www.w3schools.com/python/ref_dictionary_pop.asp)               | Removes the element with the specified key                                                                  |
| [popitem()](https://www.w3schools.com/python/ref_dictionary_popitem.asp)       | Removes the last inserted key-value pair                                                                    |
| [setdefault()](https://www.w3schools.com/python/ref_dictionary_setdefault.asp) | Returns the value of the specified key. If the key does not exist: insert the key, with the specified value |
| [update()](https://www.w3schools.com/python/ref_dictionary_update.asp)         | Updates the dictionary with the specified key-value pairs                                                   |
| [values()](https://www.w3schools.com/python/ref_dictionary_values.asp)         | Returns a list of all the values in the dictionary                                                          |

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

## 5.4 Ensembles (set)

Les ensembles sont des collections non ordonnées de valeurs uniques. Ils sont utilisés pour stocker des éléments sans doublons et pour effectuer des opérations mathématiques comme des unions, intersections, et différences.

| Method                                                                                                    | Description                                                                    |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [add()](https://www.w3schools.com/python/ref_set_add.asp)                                                 | Adds an element to the set                                                     |
| [clear()](https://www.w3schools.com/python/ref_set_clear.asp)                                             | Removes all the elements from the set                                          |
| [copy()](https://www.w3schools.com/python/ref_set_copy.asp)                                               | Returns a copy of the set                                                      |
| [difference()](https://www.w3schools.com/python/ref_set_difference.asp)                                   | Returns a set containing the difference between two or more sets               |
| [difference_update()](https://www.w3schools.com/python/ref_set_difference_update.asp)                     | Removes the items in this set that are also included in another, specified set |
| [discard()](https://www.w3schools.com/python/ref_set_discard.asp)                                         | Remove the specified item                                                      |
| [intersection()](https://www.w3schools.com/python/ref_set_intersection.asp)                               | Returns a set, that is the intersection of two other sets                      |
| [intersection_update()](https://www.w3schools.com/python/ref_set_intersection_update.asp)                 | Removes the items in this set that are not present in other, specified set(s)  |
| [isdisjoint()](https://www.w3schools.com/python/ref_set_isdisjoint.asp)                                   | Returns whether two sets have a intersection or not                            |
| [issubset()](https://www.w3schools.com/python/ref_set_issubset.asp)                                       | Returns whether another set contains this set or not                           |
|                                                                                                           | Returns whether all items in this set is present in other, specified set(s)    |
| [issuperset()](https://www.w3schools.com/python/ref_set_issuperset.asp)                                   | Returns whether this set contains another set or not                           |
|                                                                                                           | Returns whether all items in other, specified set(s) is present in this set    |
| [pop()](https://www.w3schools.com/python/ref_set_pop.asp)                                                 | Removes an element from the set                                                |
| [remove()](https://www.w3schools.com/python/ref_set_remove.asp)                                           | Removes the specified element                                                  |
| [symmetric_difference()](https://www.w3schools.com/python/ref_set_symmetric_difference.asp)               | Returns a set with the symmetric differences of two sets                       |
| [symmetric_difference_update()](https://www.w3schools.com/python/ref_set_symmetric_difference_update.asp) | Inserts the symmetric differences from this set and another                    |
| [union()](https://www.w3schools.com/python/ref_set_union.asp)                                             | Return a set containing the union of sets                                      |
| [update()](https://www.w3schools.com/python/ref_set_update.asp)                                           | Update the set with the union of this set and others                           |

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

| Method                                                                   | Description                                                                          |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| [close()](https://www.w3schools.com/python/ref_file_close.asp)           | Closes the file                                                                      |
| detach()                                                                 | Returns the separated raw stream from the buffer                                     |
| [fileno()](https://www.w3schools.com/python/ref_file_fileno.asp)         | Returns a number that represents the stream, from the operating system's perspective |
| [flush()](https://www.w3schools.com/python/ref_file_flush.asp)           | Flushes the internal buffer                                                          |
| [isatty()](https://www.w3schools.com/python/ref_file_isatty.asp)         | Returns whether the file stream is interactive or not                                |
| [read()](https://www.w3schools.com/python/ref_file_read.asp)             | Returns the file content                                                             |
| [readable()](https://www.w3schools.com/python/ref_file_readable.asp)     | Returns whether the file stream can be read or not                                   |
| [readline()](https://www.w3schools.com/python/ref_file_readline.asp)     | Returns one line from the file                                                       |
| [readlines()](https://www.w3schools.com/python/ref_file_readlines.asp)   | Returns a list of lines from the file                                                |
| [seek()](https://www.w3schools.com/python/ref_file_seek.asp)             | Change the file position                                                             |
| [seekable()](https://www.w3schools.com/python/ref_file_seekable.asp)     | Returns whether the file allows us to change the file position                       |
| [tell()](https://www.w3schools.com/python/ref_file_tell.asp)             | Returns the current file position                                                    |
| [truncate()](https://www.w3schools.com/python/ref_file_truncate.asp)     | Resizes the file to a specified size                                                 |
| [writable()](https://www.w3schools.com/python/ref_file_writable.asp)     | Returns whether the file can be written to or not                                    |
| [write()](https://www.w3schools.com/python/ref_file_write.asp)           | Writes the specified string to the file                                              |
| [writelines()](https://www.w3schools.com/python/ref_file_writelines.asp) | Writes a list of strings to the file                                                 |
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

| Exception             | Description                                                                       |
| --------------------- | --------------------------------------------------------------------------------- |
| ArithmeticError       | Raised when an error occurs in numeric calculations                               |
| AssertionError        | Raised when an assert statement fails                                             |
| AttributeError        | Raised when attribute reference or assignment fails                               |
| Exception             | Base class for all exceptions                                                     |
| EOFError              | Raised when the input() method hits an "end of file" condition (EOF)              |
| FloatingPointError    | Raised when a floating point calculation fails                                    |
| GeneratorExit         | Raised when a generator is closed (with the close() method)                       |
| ImportError           | Raised when an imported module does not exist                                     |
| IndentationError      | Raised when indentation is not correct                                            |
| IndexError            | Raised when an index of a sequence does not exist                                 |
| KeyError              | Raised when a key does not exist in a dictionary                                  |
| KeyboardInterrupt     | Raised when the user presses Ctrl+c, Ctrl+z or Delete                             |
| LookupError           | Raised when errors raised cant be found                                           |
| MemoryError           | Raised when a program runs out of memory                                          |
| NameError             | Raised when a variable does not exist                                             |
| NotImplementedError   | Raised when an abstract method requires an inherited class to override the method |
| OSError               | Raised when a system related operation causes an error                            |
| OverflowError         | Raised when the result of a numeric calculation is too large                      |
| ReferenceError        | Raised when a weak reference object does not exist                                |
| RuntimeError          | Raised when an error occurs that do not belong to any specific exceptions         |
| StopIteration         | Raised when the next() method of an iterator has no further values                |
| SyntaxError           | Raised when a syntax error occurs                                                 |
| TabError              | Raised when indentation consists of tabs or spaces                                |
| SystemError           | Raised when a system error occurs                                                 |
| SystemExit            | Raised when the sys.exit() function is called                                     |
| TypeError             | Raised when two different types are combined                                      |
| UnboundLocalError     | Raised when a local variable is referenced before assignment                      |
| UnicodeError          | Raised when a unicode problem occurs                                              |
| UnicodeEncodeError    | Raised when a unicode encoding problem occurs                                     |
| UnicodeDecodeError    | Raised when a unicode decoding problem occurs                                     |
| UnicodeTranslateError | Raised when a unicode translation problem occurs                                  |
| ValueError            | Raised when there is a wrong value in a specified data type                       |
| ZeroDivisionError     | Raised when the second operator in a division is zero                             |
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
## 13.1 Tableau récapitulatif keyword
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

|Function|Description|
|---|---|
|[abs()](https://www.w3schools.com/python/ref_func_abs.asp)|Returns the absolute value of a number|
|[all()](https://www.w3schools.com/python/ref_func_all.asp)|Returns True if all items in an iterable object are true|
|[any()](https://www.w3schools.com/python/ref_func_any.asp)|Returns True if any item in an iterable object is true|
|[ascii()](https://www.w3schools.com/python/ref_func_ascii.asp)|Returns a readable version of an object. Replaces none-ascii characters with escape character|
|[bin()](https://www.w3schools.com/python/ref_func_bin.asp)|Returns the binary version of a number|
|[bool()](https://www.w3schools.com/python/ref_func_bool.asp)|Returns the boolean value of the specified object|
|[bytearray()](https://www.w3schools.com/python/ref_func_bytearray.asp)|Returns an array of bytes|
|[bytes()](https://www.w3schools.com/python/ref_func_bytes.asp)|Returns a bytes object|
|[callable()](https://www.w3schools.com/python/ref_func_callable.asp)|Returns True if the specified object is callable, otherwise False|
|[chr()](https://www.w3schools.com/python/ref_func_chr.asp)|Returns a character from the specified Unicode code.|
|classmethod()|Converts a method into a class method|
|[compile()](https://www.w3schools.com/python/ref_func_compile.asp)|Returns the specified source as an object, ready to be executed|
|[complex()](https://www.w3schools.com/python/ref_func_complex.asp)|Returns a complex number|
|[delattr()](https://www.w3schools.com/python/ref_func_delattr.asp)|Deletes the specified attribute (property or method) from the specified object|
|[dict()](https://www.w3schools.com/python/ref_func_dict.asp)|Returns a dictionary (Array)|
|[dir()](https://www.w3schools.com/python/ref_func_dir.asp)|Returns a list of the specified object's properties and methods|
|[divmod()](https://www.w3schools.com/python/ref_func_divmod.asp)|Returns the quotient and the remainder when argument1 is divided by argument2|
|[enumerate()](https://www.w3schools.com/python/ref_func_enumerate.asp)|Takes a collection (e.g. a tuple) and returns it as an enumerate object|
|[eval()](https://www.w3schools.com/python/ref_func_eval.asp)|Evaluates and executes an expression|
|[exec()](https://www.w3schools.com/python/ref_func_exec.asp)|Executes the specified code (or object)|
|[filter()](https://www.w3schools.com/python/ref_func_filter.asp)|Use a filter function to exclude items in an iterable object|
|[float()](https://www.w3schools.com/python/ref_func_float.asp)|Returns a floating point number|
|[format()](https://www.w3schools.com/python/ref_func_format.asp)|Formats a specified value|
|[frozenset()](https://www.w3schools.com/python/ref_func_frozenset.asp)|Returns a frozenset object|
|[getattr()](https://www.w3schools.com/python/ref_func_getattr.asp)|Returns the value of the specified attribute (property or method)|
|[globals()](https://www.w3schools.com/python/ref_func_globals.asp)|Returns the current global symbol table as a dictionary|
|[hasattr()](https://www.w3schools.com/python/ref_func_hasattr.asp)|Returns True if the specified object has the specified attribute (property/method)|
|hash()|Returns the hash value of a specified object|
|help()|Executes the built-in help system|
|[hex()](https://www.w3schools.com/python/ref_func_hex.asp)|Converts a number into a hexadecimal value|
|[id()](https://www.w3schools.com/python/ref_func_id.asp)|Returns the id of an object|
|[input()](https://www.w3schools.com/python/ref_func_input.asp)|Allowing user input|
|[int()](https://www.w3schools.com/python/ref_func_int.asp)|Returns an integer number|
|[isinstance()](https://www.w3schools.com/python/ref_func_isinstance.asp)|Returns True if a specified object is an instance of a specified object|
|[issubclass()](https://www.w3schools.com/python/ref_func_issubclass.asp)|Returns True if a specified class is a subclass of a specified object|
|[iter()](https://www.w3schools.com/python/ref_func_iter.asp)|Returns an iterator object|
|[len()](https://www.w3schools.com/python/ref_func_len.asp)|Returns the length of an object|
|[list()](https://www.w3schools.com/python/ref_func_list.asp)|Returns a list|
|[locals()](https://www.w3schools.com/python/ref_func_locals.asp)|Returns an updated dictionary of the current local symbol table|
|[map()](https://www.w3schools.com/python/ref_func_map.asp)|Returns the specified iterator with the specified function applied to each item|
|[max()](https://www.w3schools.com/python/ref_func_max.asp)|Returns the largest item in an iterable|
|[memoryview()](https://www.w3schools.com/python/ref_func_memoryview.asp)|Returns a memory view object|
|[min()](https://www.w3schools.com/python/ref_func_min.asp)|Returns the smallest item in an iterable|
|[next()](https://www.w3schools.com/python/ref_func_next.asp)|Returns the next item in an iterable|
|[object()](https://www.w3schools.com/python/ref_func_object.asp)|Returns a new object|
|[oct()](https://www.w3schools.com/python/ref_func_oct.asp)|Converts a number into an octal|
|[open()](https://www.w3schools.com/python/ref_func_open.asp)|Opens a file and returns a file object|
|[ord()](https://www.w3schools.com/python/ref_func_ord.asp)|Convert an integer representing the Unicode of the specified character|
|[pow()](https://www.w3schools.com/python/ref_func_pow.asp)|Returns the value of x to the power of y|
|[print()](https://www.w3schools.com/python/ref_func_print.asp)|Prints to the standard output device|
|property()|Gets, sets, deletes a property|
|[range()](https://www.w3schools.com/python/ref_func_range.asp)|Returns a sequence of numbers, starting from 0 and increments by 1 (by default)|
|repr()|Returns a readable version of an object|
|[reversed()](https://www.w3schools.com/python/ref_func_reversed.asp)|Returns a reversed iterator|
|[round()](https://www.w3schools.com/python/ref_func_round.asp)|Rounds a numbers|
|[set()](https://www.w3schools.com/python/ref_func_set.asp)|Returns a new set object|
|[setattr()](https://www.w3schools.com/python/ref_func_setattr.asp)|Sets an attribute (property/method) of an object|
|[slice()](https://www.w3schools.com/python/ref_func_slice.asp)|Returns a slice object|
|[sorted()](https://www.w3schools.com/python/ref_func_sorted.asp)|Returns a sorted list|
|staticmethod()|Converts a method into a static method|
|[str()](https://www.w3schools.com/python/ref_func_str.asp)|Returns a string object|
|[sum()](https://www.w3schools.com/python/ref_func_sum.asp)|Sums the items of an iterator|
|[super()](https://www.w3schools.com/python/ref_func_super.asp)|Returns an object that represents the parent class|
|[tuple()](https://www.w3schools.com/python/ref_func_tuple.asp)|Returns a tuple|
|[type()](https://www.w3schools.com/python/ref_func_type.asp)|Returns the type of an object|
|[vars()](https://www.w3schools.com/python/ref_func_vars.asp)|Returns the __dict__ property of an object|
|[zip()](https://www.w3schools.com/python/ref_func_zip.asp)|Returns an iterator, from two or more iterators|
