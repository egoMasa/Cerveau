# Sommaire 
1. Généralités
	1. Présentation de C et C++
	2. Notion de compilation
	3. Capacités de C++
2. Bases du langage
	1. Syntaxe de base
	2. Variables et types de données
	3. Opérateurs
3. Contrôle de flux
	1. Instructions conditionnelles
	2. Boucles
4. Fonctions
	1. Définition et appel
	2. Fonctions inline
	3. Surcharge de fonctions
5. Portée et espace de nommage
	1. Portée des variables
	2. Espaces de noms
6. Pointeurs et références
	1. Pointeurs
	2. Références
7. Programmation orientée objet
	1. **Classes et objets**
	2. **Encapsulation**
	3. **Héritage**
	4. **Polymorphisme**
	5. **Abstraction**
8. Gestion de la mémoire
	1. **Allocation dynamique de mémoire**
	2. **Gestionnaire de ressources**
9. Collections de données
	1. **Tableaux**
	2. **Chaînes de caractères**
	3. **Structures de données standard**
10. Entrées et sorties
	1. **Entrées/sorties standard**
	2. **Fichiers**
11. Exceptions
	1. **Gestion des exceptions**
12. Modèles (Templates)
	1. **Templates de fonction et de classe**
# 1) Présentation de C et C++

- **C** est un langage de programmation de bas niveau 
- Créé en 1972 par Dennis Ritchie chez Bell Labs. 
- Il a été développé pour la reprogrammation du système d'exploitation UNIX, ce qui a permis une portabilité accrue entre les différents systèmes. 
- C est particulièrement reconnu pour sa performance et son contrôle de bas niveau sur les ressources système, le rendant idéal pour les systèmes embarqués, les systèmes d'exploitation, et les applications nécessitant une gestion fine de la mémoire.

- **C++** est une extension du langage C 
- Développé par Bjarne Stroustrup dans les années 1980. 
- C++ offre toutes les capacités de C avec l'ajout de la programmation orientée objet (OOP). 
- Cela permet une structuration plus complexe des programmes à travers des classes, de l'héritage, du polymorphisme, et de l'encapsulation. 
- C++ est souvent utilisé pour le développement de logiciels systèmes, de jeux vidéo, de moteurs de rendu graphique, et d'applications nécessitant de hautes performances.

# 2) Compilation

* Processus de transformation du code écrit dans un langage de haut niveau (comme C ou C++) en langage machine, compréhensible par le processeur. 
* Pour C et C++, cela nécessite généralement un compilateur tel que ***GCC*** ou ***Clang***. 
* Le code source est compilé en un fichier exécutable ou en une bibliothèque, et durant ce processus, diverses optimisations sont appliquées pour améliorer la performance du programme final.

# 3) Capacités de C++

- **Développement de systèmes et d'applications embarquées**: la gestion précise de la mémoire et la performance sont cruciales dans ces domaines.
- **Jeux vidéo et réalité virtuelle**: C++ est très prisé pour son efficacité et son support étendu via des bibliothèques comme Unreal Engine.
- **Applications de bureau et serveurs**: de nombreuses applications logicielles et serveurs web critiques sont écrits en C et C++ pour maximiser l'efficacité.
- **Simulations scientifiques et calculs de haute performance**: la vitesse d'exécution est essentielle dans le traitement de grandes quantités de données.

|Caractéristique|Python|C|C++|
|---|---|---|---|
|**Type de Langage**|Haut niveau, interprété|Bas niveau, compilé|Bas niveau, compilé avec OOP|
|**Gestion de la mémoire**|Automatique (Garbage Collection)|Manuelle|Manuelle|
|**Complexité**|Simple et facile à apprendre|Plus complexe, nécessite une gestion minutieuse des ressources|Encore plus complexe avec les fonctionnalités OOP|
|**Vitesse d'exécution**|Moins rapide (interprété)|Très rapide (compilé)|Très rapide (compilé)|
|**Utilisation typique**|Scripting, Web, Data Science|Systèmes embarqués, OS|Applications système, jeux vidéo, simulations|

Python est excellent pour les débutants et les projets nécessitant un développement rapide, tandis que C et C++ sont préférés pour les applications nécessitant une optimisation maximale et une gestion directe de la mémoire. Les différences de paradigmes, de vitesse, et d’utilisation entre ces langages montrent bien leur diversité d’application.

# 3) Setup de l'environnement (Windows/Unix)

## Windows

### 1. Installer un compilateur :

MinGW (Minimalist GNU for Windows) est un ensemble d'outils GNU pour Windows, y compris le compilateur GCC (GNU Compiler Collection), qui est nécessaire pour compiler des programmes C++ sous Windows.
1. Télécharge le gestionnaire d'installation de MinGW depuis le site officiel
2. Lance le fichier d'installation téléchargé (`mingw-get-setup.exe`).
3. Pendant l'installation, tu seras invité à sélectionner les composants à installer. Assure-toi de sélectionner au moins le package `mingw32-base`, qui inclut le compilateur GCC pour la compilation de programmes C++.
4. Choisis un répertoire d'installation pour MinGW. Le répertoire par défaut est généralement `C:\MinGW`.
5. Termine l'installation en suivant les instructions à l'écran.
### 2. Ajouter le compilateur à la variable PATH :

Une fois que MinGW est installé, tu dois ajouter son chemin d'accès au répertoire `bin` à la variable d'environnement PATH de ton système. Cela permettra à Windows de trouver les outils de MinGW lorsqu'ils sont utilisés dans la ligne de commande.
1. Recherche "***Variables d'environnement système***" dans la barre de recherche
4. Dans "***Variables d'environnement***", recherche la variable "***PATH***" double clique
5. Ajoute le chemin d'accès au répertoire`C:\MinGW\bin`.
6. Clique sur "OK" pour enregistrer les modifications et ferme toutes les fenêtres.
7. Vérifier que la commande gcc est accessible dans le CMD `gcc --version`

Maintenant, le compilateur GCC de MinGW devrait être accessible depuis n'importe quel emplacement dans la ligne de commande.
### 3. Installer l'extension C++ sur VSCode :
1. Ouvre Visual Studio Code.
2. Clique sur l'icône des extensions dans la barre latérale ou utilise le raccourci `Ctrl+Shift+X`.
3. Dans la barre de recherche, tape "C++".
4. Sélectionne l'extension "C/C++" proposée par Microsoft
5. Une fois l'installation terminée, l'extension est prête à être utilisée.

Maintenant, tu es prêt à écrire, compiler et exécuter des programmes C++ dans Visual Studio Code sur Windows, en utilisant le compilateur GCC fourni par MinGW.
### 4. Sélectionner le compilateur dans VSCode :

Lorsque tu installes l'extension C++ dans Visual Studio Code, elle tente généralement de détecter automatiquement les compilateurs disponibles sur ton système, y compris g++, le compilateur C++ de GNU fourni par MinGW sur Windows. Si la détection automatique ne fonctionne pas ou si tu souhaites spécifier manuellement le compilateur, tu peux le faire en suivant ces étapes :
1. Ouvre un fichier C++ (.cpp) dans Visual Studio Code.
2. Va dans "Affichage" > "Palette de commandes" ou utilise `Ctrl+Shift+P`.
3. Tape "C/C++: Sélect IntelliSense Configuration" et choisir g++.
### 5. Compiler le script :

Après avoir sélectionné le compilateur, tu peux compiler ton script en suivant ces étapes :
1. Ouvre le fichier C++ que tu veux compiler dans Visual Studio Code.
2. Utilise la commande de build en appuyant sur `Ctrl+Shift+B` ou en allant dans "Exécution" > "Tâches" > "Exécuter la tâche de build".
3. Sélectionne l'option de compilation (par exemple, "g++.exe build active file") dans la liste des tâches disponibles. Cette tâche utilisera le compilateur g++ que tu as sélectionné précédemment pour compiler le fichier actif.

Visual Studio Code générera un fichier exécutable (.exe) à partir de ton script C++ si la compilation réussit.
### 6. Exécuter le programme :
1. Tape le nom du fichier exécutable (par exemple, ./nom_du_fichier.exe) dans le terminal et appuie sur Entrée pour exécuter le programme.

## Unix
### 1. Installer un compilateur :

Sur Debian, le compilateur GCC (GNU Compiler Collection) est souvent déjà installé par défaut. Cependant, pour être sûr que tu as toutes les dépendances nécessaires pour le développement C++, tu peux installer le paquet `build-essential` qui inclut GCC ainsi que d'autres outils de compilation :

```bash
sudo apt update
sudo apt install build-essential
```

Cette commande met à jour les informations sur les paquets disponibles et installe ensuite le paquet `build-essential`, qui contient GCC et d'autres outils nécessaires pour la compilation de programmes C++.

### 2. Installer l'extension C++ sur VSCode :

L'installation de l'extension C++ dans Visual Studio Code est similaire à celle sur Windows :

1. Ouvre Visual Studio Code.
2. Clique sur l'icône des extensions dans la barre latérale ou utilise le raccourci `Ctrl+Shift+X`.
3. Dans la barre de recherche, tape "C++".
4. Sélectionne l'extension "C/C++" proposée par Microsoft.
5. Clique sur "Installer".

Une fois l'installation terminée, l'extension est prête à être utilisée.

### 3. Sélectionner le compilateur dans VSCode :

L'extension C++ de Visual Studio Code devrait automatiquement détecter GCC installé sur Debian. Si elle ne le fait pas, tu peux spécifier manuellement le compilateur en suivant ces étapes :

1. Ouvre un fichier C++ (.cpp) dans Visual Studio Code.
2. Va dans "Affichage" > "Palette de commandes" ou utilise `Ctrl+Shift+P`.
3. Tape "C/C++: Sélect IntelliSense Configuration" et choisis GCC.

### 4. Compiler le script :

Après avoir sélectionné le compilateur, tu peux compiler ton script en suivant ces étapes :

1. Ouvre le fichier C++ que tu veux compiler dans Visual Studio Code.
2. Utilise la commande de build en appuyant sur `Ctrl+Shift+B` ou en allant dans "Exécution" > "Tâches" > "Exécuter la tâche de build".
3. Sélectionne l'option de compilation dans la liste des tâches disponibles. Cette tâche utilisera le compilateur GCC que tu as sélectionné précédemment pour compiler le fichier actif.

Visual Studio Code générera un fichier exécutable à partir de ton script C++ si la compilation réussit.
### 5. Exécuter le programme :

1. Une fois que ton programme a été compilé avec succès, tu peux exécuter le fichier exécutable en ouvrant un terminal dans Visual Studio Code et en naviguant jusqu'au répertoire où se trouve le fichier exécutable.
2. Tape le nom du fichier exécutable dans le terminal et appuie sur Entrée pour exécuter le programme.

Ces étapes te permettront de configurer un environnement de développement C++ sur Debian, d'écrire, de compiler et d'exécuter des programmes C++ dans Visual Studio Code.
# 4) Bases du langage 
## 4.1 Syntaxe de base 
* La syntaxe de base de C++ inclut la structure des déclarations de fonction, la définition de variables, le corps des fonctions, les points-virgules en fin d'instruction, et les blocs de code encapsulés entre accolades `{}`.
```cpp
#include <iostream> 

int main() { // Fonction principale d'entrée du programme
    std::cout << "Bonjour le monde!"; // Affichage à l'écran
    return 0; // Valeur de retour du programme
}

```
## 4.2 Variables et types de données 
* En C++, les variables doivent être déclarées avec un type spécifique qui détermine la taille et le layout de la mémoire de la variable. Les types de données de base incluent `int` (entiers), `double` (nombres à virgule flottante), `char` (caractères), et `bool` (booléens).
**Variations possibles** :

| Catégorie              | Type                    | Description                                                                                   |
|------------------------|-------------------------|-----------------------------------------------------------------------------------------------|
| **Types simples**      | `int`                   | Entier de taille standard, généralement 32 bits sur la plupart des systèmes.                  |
|                        | `float`                 | Nombre à virgule flottante à simple précision, typiquement 32 bits.                           |
|                        | `double`                | Nombre à virgule flottante à double précision, typiquement 64 bits.                           |
|                        | `char`                  | Caractère unique, typiquement 8 bits.                                                         |
|                        | `bool`                  | Valeur booléenne, `true` ou `false`.                                                          |
| **Types modifiés**     | `unsigned int`          | Version non signée de `int`, peut stocker seulement des valeurs positives.                    |
|                        | `long int`              | Version longue de `int`, permettant une plus grande plage de valeurs.                         |
|                        | `short int`             | Version courte de `int`, utilisée pour économiser de la mémoire, plage de valeurs réduite.    |
| **Types non primitifs**| Structures              | Collections de données de types potentiellement différents, regroupées sous un même nom.      |
|                        | Unions                  | Types où différentes données sont stockées dans la même position de mémoire.                  |
|                        | Classes                 | Types avancés permettant d'encapsuler données et fonctions, supports principaux de la POO.    |

```cpp
int a = 5; 
float b = 3.14; 
double c = 2.71828; 
char d = 'A'; 
bool e = true;
unsigned int f = 4000000000;
long int g = 1234567890123;
short int h = 32767;
struct Person {
  string name;
  int age;
};
union Data {
  int i;
  float f;
  char str[20];
};
class Car {
  public:
    void drive() {
      // Code to drive the car
    }
};
```
## 4.3 Opérateurs
Les opérateurs permettent de réaliser des opérations mathématiques, de comparaison ou logiques sur des variables. Ils incluent les opérateurs arithmétiques (`+`, `-`, `*`, `/`, `%`), les opérateurs de comparaison (`==`, `!=`, `<`, `>`, `<=`, `>=`), et les opérateurs logiques (`&&`, `||`, `!`).

**Variations possibles** :

| Catégorie                              | Opérateurs                                | Description                                               | Exemple                                   |
|----------------------------------------|-------------------------------------------|-----------------------------------------------------------|-------------------------------------------|
| **Opérateurs arithmétiques**           | `+`, `-`, `*`, `/`, `%`                   | Utilisés pour les calculs mathématiques simples.           | `int a = 5 + 3; // a vaut 8`              |
|                                        |                                           |                                                           | `int b = a % 2; // b vaut 0`              |
| **Opérateurs de comparaison**          | `==`, `!=`, `<`, `>`, `<=`, `>=`          | Utilisés pour comparer deux valeurs.                       | `if (a == 8)`                             |
|                                        |                                           |                                                           | `if (b > 1)`                              |
| **Opérateurs logiques**                | `&&`, `\|\|`, `!`                         | Utilisés pour combiner des conditions booléennes.          | `if (a == 8 && b == 0)`                   |
| **Opérateurs d'assignation**           | `=`, `+=`, `-=`, `*=`, `/=`               | Utilisés pour assigner des valeurs aux variables.          | `a += 2; // a vaut maintenant 10`         |
|                                        |                                           |                                                           | `b *= 3; // b vaut maintenant 0`          |
| **Opérateurs d'incrémentation/décrémentation** | `++`, `--` (préfixe et suffixe)   | Utilisés pour augmenter ou diminuer une valeur de un.      | `a++; // a vaut maintenant 11`            |
|                                        |                                           |                                                           | `--b; // b vaut maintenant -1`            |

```cpp
int result = 10 / 3; // result vaut 3 
int remainder = 10 % 3; // remainder vaut 1

if (result != remainder) {
    cout << "Les valeurs sont différentes." << endl;
}

bool isAdult = true;
int age = 20;
if (isAdult && age >= 18) {
    cout << "Vous êtes un adulte." << endl;
}

int x = 10; 
x += 5; // x est maintenant 15

for (int i = 0; i < 10; i++) { cout << i << " "; } // Affiche 0 1 2 3 4 5 6 7 8 9
```

# 5) Contrôle de flux

## 5.1 Instructions conditionnelles

Les instructions conditionnelles permettent d'exécuter des blocs de code selon que certaines conditions sont vraies ou fausses. Elles sont essentielles pour diriger le flux du programme en fonction des données d'entrée ou des résultats intermédiaires.

**Variations possibles** :

| Instruction   | Description                                                                                        | Exemple                                            |
| ------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **`if`**      | Exécute un bloc de code si une condition spécifiée est vraie.                                      | `if (a > b) { cout << "a est plus grand que b"; }` |
| **`else`**    | Exécute un bloc de code si la condition de l'instruction `if` précédente est fausse.               | `else { cout << "a n'est pas plus grand que b"; }` |
| **`else if`** | Fournit une condition supplémentaire si les conditions précédentes `if` ou `else if` sont fausses. | `else if (a == b) { cout << "a est égal à b"; }`   |
| **`switch`**  | Teste une variable par rapport à une série de valeurs pour exécuter différents blocs de code.      | ```cpp                                             |
switch (x) {
    case 1:
        cout << "x est 1";
        break;
    case 2:
        cout << "x est 2";
        break;
    default:
        cout << "x n'est ni 1 ni 2";
}
```cpp
int a = 10, b = 20;
if (a < b) {
  cout << "b est plus grand.";
}

if (a > b) {
    cout << "a est plus grand.";
} else {
    cout << "a n'est pas plus grand.";
}

if (a > b) {
    cout << "a est plus grand.";
} else if (a == b) {
    cout << "a et b sont égaux.";
} else {
    cout << "b est plus grand.";
}


int x = 2;
switch (x) {
    case 1:
        cout << "x est 1";
        break;
    case 2:
        cout << "x est 2";
        break;
    default:
        cout << "x n'est ni 1 ni 2";
}

```

## 5.2 Boucles

Les boucles permettent de répéter l'exécution d'un bloc de code tant que certaines conditions sont remplies, rendant le code plus compact et évitant la duplication.

**Variations possibles** :
- **`for`** : Exécute un bloc de code un nombre prédéterminé de fois, avec une variable de boucle qui s'incrémente ou se décrémente à chaque itération.
- **`while`** : Continue à exécuter un bloc de code tant que la condition est vraie.
- **`do-while`** : Similaire à `while`, mais garantit l'exécution du bloc de code au moins une fois avant de vérifier la condition.

| Instruction    | Description                                                                                                                              |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **`for`**      | Exécute un bloc de code un nombre prédéterminé de fois, avec une variable de boucle qui s'incrémente ou se décrémente à chaque itération |
| **`while`**    | Continue à exécuter un bloc de code tant que la condition est vraie.                                                                     |
| **`do-while`** | Similaire à `while`, mais garantit l'exécution du bloc de code au moins une fois avant de vérifier la condition.                         |

```cpp
// Exemple de boucle for
for (int i = 0; i < 5; i++) {
    std::cout << "i = " << i << "\n";
}

// Exemple de boucle while
int count = 5;
while (count > 0) {
    std::cout << "Comptage: " << count << "\n";
    count--;
}

// Exemple de boucle do-while
int n;
do {
    std::cout << "Entrez un nombre positif: ";
    std::cin >> n;
} while (n <= 0);
```

# 6) Fonctions en C++

## 6.1 Définition et appel

Les fonctions en C++ sont des blocs de code qui effectuent une tâche spécifique et peuvent être appelées plusieurs fois dans le programme. Elles permettent de modulariser le code en regroupant des tâches logiquement cohérentes. Une fonction peut prendre des paramètres, effectuer des opérations et retourner une valeur.

```cpp
#include <iostream>

// Définition de la fonction
int addition(int a, int b) {
    return a + b; // Retourne la somme de a et b
}

// Fonction principale
int main() {
    int result = addition(5, 3); // Appel de la fonction
    std::cout << "Le résultat est : " << result << std::endl;
    return 0;
}
```

## 6.2 Fonctions inline

Les fonctions `inline` sont une suggestion au compilateur pour intégrer le code de la fonction directement à l'endroit de l'appel afin de réduire le coût d'appel de la fonction (overhead). Cela peut améliorer la performance pour les petites fonctions fréquemment utilisées. Cependant, l'utilisation de `inline` est une suggestion et le compilateur peut choisir de l'ignorer.

```cpp
#include <iostream>

// Définition d'une fonction inline
inline int max(int x, int y) {
    return (x > y) ? x : y;
}

// Fonction principale
int main() {
    int a = 10, b = 20;
    std::cout << "Le plus grand nombre est : " << max(a, b) << std::endl;
    return 0;
}
```

## 6.3 Surcharge de fonctions

La surcharge de fonctions permet à plusieurs fonctions de partager le même nom mais avec des listes de paramètres différentes (par exemple, le nombre de paramètres ou leur type). Cela permet de créer des fonctions qui accomplissent des tâches similaires pour différents types de données ou différents nombres d'arguments.

```cpp
#include <iostream>

// Première version de la fonction
void afficher(int i) {
    std::cout << "L'entier est : " << i << std::endl;
}

// Surcharge avec un paramètre de type double
void afficher(double f) {
    std::cout << "Le nombre à virgule flottante est : " << f << std::endl;
}

// Surcharge avec un paramètre de type string
void afficher(const std::string& s) {
    std::cout << "La chaîne est : " << s << std::endl;
}

// Fonction principale
int main() {
    afficher(10);    // Appel avec int
    afficher(3.14159); // Appel avec double
    afficher("Bonjour le monde!"); // Appel avec string
    return 0;
}
```

# 7) Portée et espace de nommage en C++

## 7.1 Portée des variables

La portée d'une variable détermine où elle est accessible dans le code. Cela affecte la visibilité et la durée de vie des variables. Les variables peuvent avoir une portée locale, globale, ou de bloc.
- **Locale** : Les variables déclarées à l'intérieur d'une fonction ou d'un bloc sont accessibles uniquement dans ce contexte.
- **Globale** : Les variables déclarées en dehors de toutes les fonctions sont accessibles de n'importe où dans le fichier de code.
- **De bloc** : Les variables déclarées à l'intérieur d’un bloc `{}` sont accessibles uniquement à l'intérieur de ce bloc.

```cpp
#include <iostream>

int varGlobale = 100;  // Variable globale

void demo() {
    int varLocale = 10;  // Variable locale à la fonction demo
    std::cout << "Variable locale: " << varLocale << std::endl;
    std::cout << "Variable globale dans demo: " << varGlobale << std::endl;
}

int main() {
    demo();
    std::cout << "Variable globale dans main: " << varGlobale << std::endl;
    // std::cout << "Variable locale: " << varLocale; // Ceci générerait une erreur
    return 0;
}
```

## 7.2 Espaces de noms

Les espaces de noms en C++ permettent de regrouper des entités comme des classes, des objets et des fonctions sous un nom distinct pour éviter les conflits de noms. Cela est particulièrement utile dans de grands projets ou lors de l'utilisation de multiples bibliothèques.
- **`namespace`** : Le mot-clé utilisé pour définir un espace de noms.
- **`using`** : Ce mot-clé peut être utilisé pour introduire un espace de noms dans un autre contexte, permettant d'utiliser les membres de l'espace de noms sans préfixe.

```cpp
#include <iostream>

namespace premier {
    void affiche() {
        std::cout << "Dans le premier espace de noms" << std::endl;
    }
}

namespace second {
    void affiche() {
        std::cout << "Dans le second espace de noms" << std::endl;
    }
}

int main() {
    premier::affiche();  // Appel de la fonction dans le premier espace de noms
    second::affiche();   // Appel de la fonction dans le second espace de noms
    return 0;
}
```

Dans cet exemple, deux espaces de noms `premier` et `second` contiennent chacun une fonction `affiche()`. Grâce aux espaces de noms, il n'y a pas de conflit entre ces deux fonctions malgré qu'elles partagent le même nom. La portée et l'espace de nommage sont cruciaux pour maintenir une structure de code propre et éviter les collisions et confusions dans les programmes plus grands et complexes.

# 8) Pointeurs et références en C++

## 8.1 Pointeurs

Un pointeur est une variable qui stocke l'adresse mémoire d'une autre variable. Ils sont utilisés pour accéder à la mémoire et manipuler des données à différents endroits du programme. Les pointeurs sont puissants mais doivent être utilisés avec prudence pour éviter des bugs difficiles à tracer comme les fuites de mémoire ou les violations d'accès.

```cpp
#include <iostream>

int main() {
    int var = 8;  // Déclaration d'une variable entière
    int* ptr = &var;  // Pointeur sur entier, initialisé avec l'adresse de var

    std::cout << "Valeur de var: " << var << std::endl;
    std::cout << "Adresse de var: " << ptr << std::endl;
    std::cout << "Valeur pointée par ptr: " << *ptr << std::endl;  // Déréférencement

    *ptr = 10;  // Modification de la valeur de var via le pointeur
    std::cout << "Nouvelle valeur de var: " << var << std::endl;

    return 0;
}
```

Dans cet exemple, `ptr` est un pointeur sur un entier (`int*`). Il est initialisé avec l'adresse de `var` (`&var`). L'opérateur `*` est utilisé pour accéder ou modifier la valeur de la variable pointée.

## 8.2 Références

Les références en C++ sont des alias pour d'autres variables. Contrairement aux pointeurs, une fois qu'une référence est initialisée à une variable, elle ne peut plus être changée pour référencer une autre variable. Les références sont plus faciles et plus sûres à utiliser que les pointeurs car elles ne nécessitent pas d'opérations de gestion de la mémoire ni de déréférencement explicite.

```cpp
#include <iostream>

void increment(int& n) {  // La fonction prend une référence à un entier
    n++;
}

int main() {
    int var = 5;
    increment(var);  // Appel de fonction avec var comme référence
    std::cout << "Valeur de var après incrementation: " << var << std::endl;
    return 0;
}
```

Dans cet exemple, `var` est incrémentée via la fonction `increment`, qui prend un argument par référence. Cela signifie que les modifications apportées à `n` dans la fonction affectent directement `var`.

**Comparaison et utilisation** :
- **Pointeurs** : utiles pour l'allocation dynamique de mémoire, l'implémentation de structures de données complexes comme les listes liées, et pour les interfaces de programmation bas niveau avec des systèmes ou des bibliothèques.
- **Références** : préférées pour les cas où la simplicité et la sécurité sont prioritaires, comme les passages d'arguments à des fonctions sans copie et les retours de fonction complexes.

Ces concepts fondamentaux de pointeurs et de références sont essentiels pour la programmation efficace en C++, offrant des outils puissants pour la gestion de la mémoire et la manipulation de données complexes.


# 9) Programmation orientée objet en C++

## 9.1 Classes et objets

Les classes sont des structures de données qui encapsulent les données (attributs) et les méthodes (fonctions) qui opèrent sur ces données. Un objet est une instance d'une classe. Les classes définissent le type de données, et les objets sont les instances réelles qui sont manipulées dans le programme.

```cpp
#include <iostream>
using namespace std;

class Voiture {
public:
    string marque;
    int annee;
    
    void demarrer() {
        cout << "La voiture " << marque << " démarre!" << endl;
    }
};

int main() {
    Voiture maVoiture;  // Création d'un objet de la classe Voiture
    maVoiture.marque = "Toyota";
    maVoiture.annee = 2021;
    maVoiture.demarrer();

    return 0;
}
```

## 9.2 Encapsulation

L'encapsulation est un concept fondamental qui consiste à restreindre l'accès direct aux composants d'une classe. Cela est réalisé en utilisant des modificateurs d'accès comme `private`, `public`, et `protected`. 

```cpp
class CompteBancaire {
private:
    double solde;  // Accès restreint de l'extérieur de la classe

public:
    void deposer(double montant) {
        if (montant > 0) {
            solde += montant;
        }
    }

    void retirer(double montant) {
        if (montant <= solde) {
            solde -= montant;
        }
    }

    double getSolde() {
        return solde;
    }
};
```

## 9.3 Héritage

L'héritage permet à une classe de hériter des attributs et méthodes d'une autre classe. La classe qui hérite est appelée classe dérivée, et la classe dont elle hérite est appelée classe de base.

```cpp
class Vehicule {
public:
    string marque;
    void klaxonner() {
        cout << "Tut tut!" << endl;
    }
};

class Camion : public Vehicule {  // Héritage
public:
    double capaciteChargement;
};

int main() {
    Camion monCamion;
    monCamion.marque = "Volvo";
    monCamion.capaciteChargement = 5000;
    monCamion.klaxonner();  // Appel de la méthode héritée
}
```

## 9.4 Polymorphisme

Le polymorphisme permet aux classes de définir des méthodes qui ont le même nom mais qui se comportent différemment selon l'objet qui les appelle. Le polymorphisme peut être implémenté via le surchargement de méthodes et la redéfinition de méthodes (override).

```cpp
class Animal {
public:
    virtual void parler() {
        cout << "Un son d'animal!" << endl;
    }
};

class Chien : public Animal {
public:
    void parler() override {  // Redéfinition
        cout << "Woof!" << endl;
    }
};

void faireParler(Animal& a) {
    a.parler();
}

int main() {
    Animal a;
    Chien c;
    faireParler(a);  // Polymorphisme
    faireParler(c);
}
```

## 9.5 Abstraction

L'abstraction est un principe par lequel une classe ne révèle que les opérations nécessaires à l'utilisation d'un objet, en masquant les détails de mise en œuvre. Elle est souvent mise en œuvre à l'aide de classes abstraites ou d'interfaces.

```cpp
class Instrument {
public:
    virtual void jouerNote(int note) = 0;  // Méthode abstraite
};

class Piano : public Instrument {
public:
    void jouerNote(int note) override {
        cout << "Jouer la note " << note << " sur le piano." << endl;
    }
};

int main() {
    Piano p;
    p.jouerNote(60);  // Implémentation concrète
}
```

# 10) Gestion de la mémoire en C++

## 10.1 Allocation dynamique de mémoire

L'allocation dynamique de mémoire permet à un programme de demander de la mémoire pendant son exécution. En C++, cela est réalisé principalement via les opérateurs `new` et `delete`. L'utilisation de `new` alloue de la mémoire pour une variable ou un tableau de variables, tandis que `delete` libère cette mémoire. La gestion correcte de cette mémoire est cruciale pour éviter les fuites de mémoire et autres problèmes de ressources.

```cpp
#include <iostream>

int main() {
    int* ptr = new int(10);  // Allocation de mémoire pour un entier, initialisation à 10
    std::cout << "Valeur allouée: " << *ptr << std::endl;

    delete ptr;  // Libération de la mémoire allouée à ptr
    ptr = nullptr;  // Bonne pratique pour éviter les pointeurs pendouillants

    // Allocation pour un tableau
    int* arr = new int[5];  // Allocation de mémoire pour un tableau de 5 entiers
    for (int i = 0; i < 5; i++) {
        arr[i] = i * 2;  // Initialisation des éléments du tableau
    }

    for (int i = 0; i < 5; i++) {
        std::cout << "arr[" << i << "] = " << arr[i] << std::endl;
    }

    delete[] arr;  // Libération de la mémoire allouée pour le tableau
    arr = nullptr;  // Éviter les pointeurs pendouillants

    return 0;
}
```

## 10.2 Gestionnaire de ressources

En C++, la gestion des ressources traite de la gestion correcte des ressources telles que la mémoire, les descripteurs de fichiers, les connexions réseau, etc. Les smart pointers (pointeurs intelligents) sont des wrappers template qui prennent en charge la gestion automatique de la mémoire en utilisant le concept de RAII (Resource Acquisition Is Initialization). Ces pointeurs s'assurent que les objets alloués sont correctement supprimés lorsque le smart pointer sort de la portée, prévenant ainsi les fuites de mémoire.

- **`std::unique_ptr`** : gère une ressource qui ne doit pas être partagée avec un autre pointer. Lorsque le `unique_ptr` sort de la portée, il détruit automatiquement l'objet pointé.
- **`std::shared_ptr`** : maintient un compteur de référence pour gérer la propriété partagée d'un objet. L'objet est détruit uniquement lorsque le dernier `shared_ptr` est détruit ou réaffecté.
- **`std::weak_ptr`** : permet de référencer un objet géré par `shared_ptr` sans augmenter le compteur de référence, utile pour éviter les cycles de référence qui peuvent mener à des fuites de mémoire.

```cpp
#include <iostream>
#include <memory>  // Bibliothèque pour les smart pointers

int main() {
    std::unique_ptr<int> pUnique(new int(42));  // unique_ptr gérant un entier
    std::cout << "Valeur unique_ptr: " << *pUnique << std::endl;

    std::shared_ptr<int> pShared1(new int(100));  // shared_ptr gérant un entier
    std::shared_ptr<int> pShared2 = pShared1;  // pShared2 partage la propriété de l'entier
    std::cout << "Valeur shared_ptr: " << *pShared1 << " (ref count: " << pShared1.use_count() << ")" << std::endl;

    // pUnique et pShared sont automatiquement désalloués à la fin de la portée
    return 0;
}
```

Dans ces exemples, les smart pointers facilitent la gestion de la mémoire en automatisant la libération des ressources, ce qui aide à prévenir les problèmes communs liés à l'allocation dynamique de mémoire, tels que les fuites de mémoire et les erreurs de segmentation.

# 11) Collections de données en C++

## 11.1 Tableaux

Les tableaux en C++ sont des collections de données de même type stockées contiguëment en mémoire. Ils peuvent être statiques ou dynamiques, et leur taille doit être connue au moment de la compilation pour les tableaux statiques. L'indexation des éléments commence à zéro.

```cpp
#include <iostream>

int main() {
    int tableau[5] = {1, 2, 3, 4, 5};  // Déclaration d'un tableau statique de 5 entiers

    // Affichage des éléments du tableau
    for(int i = 0; i < 5; ++i) {
        std::cout << "tableau[" << i << "] = " << tableau[i] << std::endl;
    }

    return 0;
}
```

## 11.2 Chaînes de caractères

En C++, les chaînes de caractères peuvent être manipulées de manière basique via des tableaux de `char` terminés par un caractère nul (`\0`), ou plus commodément à l'aide de l'objet `std::string` de la bibliothèque standard qui offre une gestion flexible des chaînes avec la manipulation dynamique de la mémoire.

```cpp
#include <iostream>
#include <string>  // Inclusion pour std::string

int main() {
    char chaineC[] = "Bonjour";  // Chaîne de caractères style C
    std::string str = "Bonjour le monde!";  // Chaîne de caractères style C++

    std::cout << "Chaîne C: " << chaineC << std::endl;
    std::cout << "Chaîne C++: " << str << std::endl;

    // Ajout à la chaîne
    str += " avec C++";
    std::cout << "Chaîne modifiée: " << str << std::endl;

    return 0;
}
```

## 11.3 Structures de données standard

C++ offre une riche bibliothèque de structures de données, `Standard Template Library` (STL), qui comprend des conteneurs comme `vector`, `map`, `set`, et beaucoup d'autres qui gèrent dynamiquement la mémoire et offrent une variété de fonctions pour manipuler ces données.

```cpp
#include <iostream>
#include <vector>
#include <map>
#include <set>

int main() {
    std::vector<int> vecteur = {1, 2, 3, 4, 5};  // Vector pour un accès dynamique et efficace
    std::map<std::string, int> notes = {{"Alice", 92}, {"Bob", 85}};  // Map pour une relation clé-valeur
    std::set<int> ensemble = {1, 2, 3, 3, 4, 4, 5};  // Set pour un ensemble unique d'éléments

    // Affichage du vecteur
    std::cout << "Vecteur:";
    for(auto& v : vecteur) {
        std::cout << " " << v;
    }
    std::cout << std::endl;

    // Affichage des notes
    std::cout << "Notes:";
    for(auto& pair : notes) {
        std::cout << " " << pair.first << "->" << pair.second;
    }
    std::cout << std::endl;

    // Affichage de l'ensemble
    std::cout << "Ensemble:";
    for(auto& e : ensemble) {
        std::cout << " " << e;
    }
    std::cout << std::endl;

    return 0;
}
```


# 12) Entrées et sorties en C++

## 12.1 Entrées/sorties standard

Les entrées et sorties standard (IO) en C++ sont gérées principalement à travers les objets `std::cin`, `std::cout`, et `std::cerr` de la bibliothèque iostream. `std::cout` est utilisé pour l'affichage à l'écran, `std::cin` pour la lecture de l'entrée clavier, et `std::cerr` pour les messages d'erreur.
- `std::cout` pour écrire sur la sortie standard (écran).
- `std::cin` pour lire depuis l'entrée standard (clavier).
- `std::cerr` pour les erreurs, s'affiche aussi à l'écran mais peut être redirigé séparément.

```cpp
#include <iostream>
#include <string>

int main() {
    std::string nom;
    std::cout << "Entrez votre nom: ";
    std::cin >> nom;  // Lecture d'une chaîne depuis l'entrée standard
    std::cout << "Bonjour, " << nom << "!" << std::endl;

    int age;
    std::cout << "Entrez votre age: ";
    std::cin >> age;
    std::cout << "Vous avez " << age << " ans." << std::endl;

    return 0;
}
```

## 12.2 Fichiers

Pour la manipulation de fichiers, C++ utilise les classes `ifstream` pour la lecture de fichiers, `ofstream` pour l'écriture, et `fstream` qui peut faire les deux. Ces classes sont également incluses dans la bibliothèque iostream et fonctionnent de manière similaire aux objets de flux standard mais sont liées à des fichiers.

```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::string filename = "exemple.txt";

    // Écriture dans un fichier
    std::ofstream outfile(filename);  // Crée ou ouvre le fichier pour l'écriture
    if (outfile.is_open()) {
        outfile << "Bonjour le monde!" << std::endl;
        outfile << "Ceci est un test d'écriture de fichier." << std::endl;
        outfile.close();
    } else {
        std::cerr << "Impossible d'ouvrir le fichier pour l'écriture." << std::endl;
    }

    // Lecture d'un fichier
    std::ifstream infile(filename);
    if (infile.is_open()) {
        std::string line;
        while (getline(infile, line)) {  // Lire ligne par ligne
            std::cout << line << std::endl;
        }
        infile.close();
    } else {
        std::cerr << "Impossible d'ouvrir le fichier pour la lecture." << std::endl;
    }

    return 0;
}
```

Dans cet exemple, `ofstream` est utilisé pour écrire dans un fichier texte, et `ifstream` est utilisé pour le lire. La gestion des erreurs est importante pour s'assurer que les fichiers sont bien ouverts avant d'essayer de lire ou écrire, pour éviter les erreurs d'exécution.


# 13) Exceptions

## 13.1 Gestion des exceptions

La gestion des exceptions en C++ permet de répondre à des conditions d'erreur exceptionnelles (comme des erreurs de programmation ou des problèmes d'exécution) de manière contrôlée. Une exception est un problème qui survient pendant l'exécution du programme et qui interrompt le flux normal des instructions. En C++, les exceptions sont gérées par trois mots-clés : `try`, `catch`, et `throw`.
- **`try`** : Bloc de code où les exceptions peuvent être levées.
- **`throw`** : Instruction utilisée pour lancer une exception.
- **`catch`** : Bloc de code qui traite une exception spécifique.

Les exceptions peuvent être de n'importe quel type (intégré, objet, etc.), mais il est plus commun d'utiliser des objets dérivés de la classe `std::exception`.

```cpp
#include <iostream>
#include <stdexcept>  // Pour std::runtime_error

int diviser(int num, int denom) {
    if (denom == 0) {
        throw std::runtime_error("Division par zéro!");  // Lancer une exception de type runtime_error
    }
    return num / denom;
}

int main() {
    int x = 10, y = 0;
    try {
        int resultat = diviser(x, y);
        std::cout << "Résultat: " << resultat << std::endl;
    } catch (const std::runtime_error& e) {  // Attraper les exceptions spécifiques
        std::cerr << "Exception capturée: " << e.what() << std::endl;
    }

    return 0;
}
```

Dans cet exemple, la fonction `diviser` lance une exception `std::runtime_error` si le dénominateur est zéro. Le bloc `try` dans `main` appelle `diviser`, et le bloc `catch` intercepte et gère l'exception.

**Avantages de la gestion des exceptions** :
- **Séparation du code de gestion des erreurs du code principal** : Cela rend le code plus propre et plus facile à maintenir.
- **Propagation des erreurs** : Les exceptions peuvent être propagées depuis la fonction où elles sont survenues jusqu'au contexte qui est capable de les gérer, sans nécessiter de multiples vérifications de retour d'erreur.
- **Gestion des erreurs inattendues** : Permet de gérer des erreurs qui n'ont pas été directement prévues par les conditions de retour normales.


# 14) Modèles (Templates)

## 14.1 Templates de fonction et de classe

Les templates en C++ sont un puissant outil de métaprogrammation qui permet de créer des fonctions et des classes génériques. Les templates permettent aux développeurs de programmer des structures génériques qui fonctionnent avec n'importe quel type de données. Cela aide à éviter la duplication de code pour des types différents et améliore la maintenabilité du code.
- **Templates de fonction** : Permettent d'écrire une fonction qui peut accepter n'importe quel type de données.
- **Templates de classe** : Permettent de définir des classes telles que les conteneurs qui peuvent gérer n'importe quel type de données.

```cpp
#include <iostream>

// Template de fonction
template <typename T>
T max(T a, T b) {
    return (a > b) ? a : b;
}

// Template de classe
template <class T>
class Boite {
public:
    T contenu;
    Boite(T contenu) : contenu(contenu) {}
    void afficher() const {
        std::cout << "Contenu: " << contenu << std::endl;
    }
};

int main() {
    // Utilisation du template de fonction
    int i = max(5, 10);
    double d = max(5.5, 10.1);
    std::cout << "Le plus grand int est : " << i << std::endl;
    std::cout << "Le plus grand double est : " << d << std::endl;

    // Utilisation du template de classe
    Boite<int> boite1(123);
    Boite<std::string> boite2("Hello World");
    boite1.afficher();
    boite2.afficher();

    return 0;
}
```

Dans cet exemple, la fonction `max` est un template qui peut comparer deux éléments de n'importe quel type (tant que le type supporte l'opérateur `>`). De même, la classe `Boite` est un template qui peut stocker et afficher un contenu de n'importe quel type.

**Avantages des templates** :
- **Flexibilité** : Les templates permettent aux développeurs de créer des fonctions et des classes flexibles qui ne sont pas liées à des types de données spécifiques.
- **Réutilisation du code** : Les templates aident à réduire la duplication en gérant de multiples types de données avec une seule définition de fonction ou de classe.
- **Performance** : Contrairement aux fonctions polymorphes à l'exécution, les templates sont résolus à la compilation, ce qui élimine le coût d'exécution du polymorphisme.

# 15) Mots-clés et fonctions standard 
## 15.1 Tableau récapitulatif Mots-clés

| Mot-clé     | Description                                                                                       | Particularités                             |
|-------------|---------------------------------------------------------------------------------------------------|--------------------------------------------|
| `auto`      | Déduit automatiquement le type d'une variable à partir de son expression d'initialisation.        | C++11 et plus récent                       |
| `bool`      | Définit un type booléen, vrai ou faux.                                                            |                                            |
| `break`     | Interrompt l'exécution de la boucle la plus proche (while, do-while, for, switch).                |                                            |
| `case`      | Définit une alternative dans un bloc switch.                                                     | Doit être suivi par une valeur constante.  |
| `catch`     | Bloque utilisé pour capturer des exceptions levées dans un bloc try.                              | Utilisé avec try et throw.                 |
| `char`      | Définit un type caractère.                                                                       |                                            |
| `class`     | Définit un type de classe.                                                                       |                                            |
| `const`     | Qualifie les types dont la valeur ne peut pas être modifiée.                                      |                                            |
| `continue`  | Passe immédiatement à la prochaine itération de la boucle englobante.                             |                                            |
| `default`   | Définit l'alternative par défaut dans un bloc switch.                                             | Un seul par bloc switch.                   |
| `delete`    | Détruit des objets et libère la mémoire associée.                                                 | Correspond à l'opérateur new.              |
| `do`        | Commence une boucle do-while.                                                                    | Boucle qui s'exécute au moins une fois.    |
| `double`    | Définit un type à virgule flottante à double précision.                                           |                                            |
| `else`      | Spécifie un bloc de code à exécuter si le test if est faux.                                       |                                            |
| `enum`      | Définit un type énumération.                                                                     |                                            |
| `explicit`  | Prévient la conversion implicite.                                                                | C++11 pour les constructeurs de conversion.|
| `extern`    | Déclare une variable ou une fonction et spécifie qu'elle est définie ailleurs.                    |                                            |
| `float`     | Définit un type à virgule flottante à simple précision.                                           |                                            |
| `for`       | Définit une boucle for.                                                                          | Peut aussi être utilisé pour des boucles basées sur une plage en C++11. |
| `friend`    | Permet à une fonction ou classe d'accéder aux membres privés d'une classe.                        |                                            |
| `goto`      | Permet un saut non conditionnel à une étiquette.                                                  | Généralement évité en programmation moderne.|
| `if`        | Définit une condition à tester.                                                                   |                                            |
| `inline`    | Suggère que la fonction est intégrée, remplaçant l'appel de fonction par le corps de la fonction. |                                            |
| `int`       | Définit un type entier.                                                                          |                                            |
| `long`      | Définit un type entier long.                                                                     | Peut qualifier un double ou un int.        |
| `mutable`   | Permet à un membre de classe const d'être modifié.                                                |                                            |
| `namespace` | Définit un espace de noms.                                                                       |                                            |
| `new`       | Alloue dynamiquement de la mémoire.                                                              | Correspond à l'opérateur delete.           |
| `operator`  | Définit/déclare un opérateur ou une fonction de conversion de type spéciale.                      |                                            |
| `private`   | Rend les membres accessibles uniquement depuis d'autres membres de la même classe.                |                                            |
| `protected` | Rend les membres accessibles depuis la classe et ses dérivées.                                    |                                            |
| `public`    | Rend les membres accessibles depuis n'importe où où l'objet est accessible.                       |                                            |
| `register`  | Suggère que la variable soit stockée dans un registre du processeur.                              | Obsolète en C++17.                         |
| `reinterpret_cast` | Convertit un type en un autre type de manière brute.                                     | Risqué et doit être utilisé avec prudence. |
| `return`    | Termine une fonction et spécifie une valeur à retourner à l'appelant.                             |                                            |
| `short`     | Définit un type entier court.                                                                    |                                            |
| `signed`    | Qualifie un type entier comme signé.                                                             |                                            |
| `sizeof`    | Donne la taille d'un type ou d'une variable en octets.                                            |                                            |
| `static`    | Déclare des membres statiques ou des variables avec une durée de vie de programme entière.        |                                            |
| `struct`    | Définit une structure de données.                                                                | Similaire à class.                         |
| `switch`    | Permet une sélection parmi de multiples alternatives basées sur une variable.                     | Utilisé avec case et default.              |
| `template`  | Définit un modèle pour une classe ou fonction générique.                                          |                                            |
| `this`      | Pointeur vers l'objet courant.                                                                   |                                            |
| `throw`     | Lance une exception.                                                                             | Utilisé avec try et catch.                 |
| `try`       | Bloque de code dans lequel des exceptions peuvent être lancées.                                   | Utilisé avec catch et/ou finally.          |
| `typedef`   | Donne un nom de type.                                                                            |                                            |
| `typeid`    | Utilisé pour obtenir le type exact d'un objet polymorphe.                                         |                                            |
| `typename`  | Spécifie que l'identificateur qui suit est un type.                                               | C++11 et plus récent.                      |
| `union`     | Définit une union, un type spécial de structure où les membres partagent la même zone mémoire.    |                                            |
| `unsigned`  | Qualifie un type entier comme non signé.                                                         |                                            |
| `using`     | Déclaration pour introduire un nom de namespace ou créer un alias de type.                        | C++11 et plus récent.                      |
| `virtual`   | Indique qu'une méthode est virtuelle et peut être redéfinie dans une classe dérivée.               |                                            |
| `void`      | Indique l'absence de type.                                                                       |                                            |
| `volatile`  | Indique que la valeur d'une variable peut changer à tout moment sans action du code environnant. | Souvent utilisé en programmation embarquée.|
| `wchar_t`   | Type de caractère large.                                                                         | Utilisé pour les caractères Unicode.       |
## 15.2 Tableau récapitulatif fonctions standard 

| Fonction           | En-tête Inclus         | Description                                                                 | Exemple                                 |
|--------------------|------------------------|-----------------------------------------------------------------------------|-----------------------------------------|
| `std::cout`        | `<iostream>`           | Utilisé pour l'affichage de sortie.                                         | `std::cout << "Hello, world!";`         |
| `std::cin`         | `<iostream>`           | Utilisé pour l'entrée standard.                                             | `int num; std::cin >> num;`             |
| `std::getline()`   | `<string>`             | Lit une ligne de texte depuis un flux d'entrée standard.                    | `std::string line; std::getline(std::cin, line);` |
| `std::sort()`      | `<algorithm>`          | Trie les éléments dans un conteneur.                                        | `std::sort(vec.begin(), vec.end());`    |
| `std::max()`       | `<algorithm>`          | Retourne le plus grand des éléments fournis.                                | `std::max(5, 10);`                      |
| `std::min()`       | `<algorithm>`          | Retourne le plus petit des éléments fournis.                                | `std::min(5, 10);`                      |
| `std::abs()`       | `<cstdlib>`            | Calcule la valeur absolue d'un nombre.                                      | `std::abs(-5);`                         |
| `std::sqrt()`      | `<cmath>`              | Calcule la racine carrée d'un nombre.                                       | `std::sqrt(25);`                        |
| `std::pow()`       | `<cmath>`              | Élève un nombre à la puissance spécifiée.                                   | `std::pow(2, 3);`                       |
| `std::swap()`      | `<utility>`            | Échange les valeurs de deux variables.                                      | `std::swap(a, b);`                      |
| `std::reverse()`   | `<algorithm>`          | Inverse l'ordre des éléments dans un conteneur.                             | `std::reverse(vec.begin(), vec.end());` |
| `std::stoi()`      | `<string>`             | Convertit une chaîne en un entier.                                          | `std::stoi("42");`                      |
| `std::stod()`      | `<string>`             | Convertit une chaîne en un double.                                          | `std::stod("42.0");`                    |
| `std::string()`    | `<string>`             | Convertit des valeurs en chaîne de caractères.                              | `std::string str = std::to_string(42);` |
| `std::setprecision()` | `<iomanip>`          | Définit la précision numérique pour le flux de sortie.                      | `std::cout << std::setprecision(4) << 3.14159;` |

### Détails supplémentaires et exemples de code

- **Manipulation d'entrée/sortie**
  ```cpp
  #include <iostream>
  int main() {
      int age;
      std::cout << "Enter your age: ";
      std::cin >> age;
      std::cout << "You are " << age << " years old.";
      return 0;
  }
