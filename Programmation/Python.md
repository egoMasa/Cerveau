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
- **Types simples** : `int`, `float`, `double`, `char`, `bool`
- **Types modifiés** : `unsigned int`, `long int`, `short int`
- **Types non primitifs** : structures, unions, classes
```cpp
int age = 25; // Déclaration d'une variable entière
double prix = 99.99; // Déclaration d'une variable à virgule flottante
char lettre = 'A'; // Déclaration d'un caractère
bool estConnecte = true; // Déclaration d'une variable booléenne

```
## 4.3 Opérateurs
Les opérateurs permettent de réaliser des opérations mathématiques, de comparaison ou logiques sur des variables. Ils incluent les opérateurs arithmétiques (`+`, `-`, `*`, `/`, `%`), les opérateurs de comparaison (`==`, `!=`, `<`, `>`, `<=`, `>=`), et les opérateurs logiques (`&&`, `||`, `!`).

**Variations possibles** :
- **Opérateurs arithmétiques** : utilisés pour les calculs mathématiques simples.
- **Opérateurs de comparaison** : utilisés pour comparer deux valeurs.
- **Opérateurs logiques** : utilisés pour combiner des conditions booléennes.
- **Opérateurs d'assignation** : `=`, `+=`, `-=`, `*=`, `/=`
- **Opérateurs d'incrémentation/décrémentation** : `++`, `--` (préfixe et suffixe)

```cpp
int x = 10;
int y = 20;
int z = x + y; // Utilisation d'un opérateur arithmétique
bool isEqual = (x == y); // Utilisation d'un opérateur de comparaison
bool isBothTrue = (x < y) && (z > x); // Utilisation d'opérateurs logiques
x += 5; // Utilisation d'un opérateur d'assignation
y++; // Incrémentation de y

```

# 5) Contrôle de flux

## 5.1 Instructions conditionnelles

Les instructions conditionnelles permettent d'exécuter des blocs de code selon que certaines conditions sont vraies ou fausses. Elles sont essentielles pour diriger le flux du programme en fonction des données d'entrée ou des résultats intermédiaires.

**Variations possibles** :
- **`if`** : Exécute un bloc de code si une condition est vraie.
- **`else`** : Exécute un bloc de code si la condition précédente `if` est fausse.
- **`else if`** : Fournit une nouvelle condition à tester si les précédentes conditions `if` ou `else if` sont fausses.
- **`switch`** : Permet de tester une variable contre une série de valeurs et exécuter différents blocs de code en fonction de ces valeurs.

```cpp
int score = 85;

if (score > 90) {
    std::cout << "Excellent!";
} else if (score > 75) {
    std::cout << "Bien fait!";
} else {
    std::cout << "Vous pouvez faire mieux.";
}

char grade = 'B';

switch (grade) {
    case 'A':
        std::cout << "Parfait!";
        break;
    case 'B':
    case 'C':
        std::cout << "Bien!";
        break;
    default:
        std::cout << "Médiocre!";
        break;
}
```

## 5.2 Boucles

Les boucles permettent de répéter l'exécution d'un bloc de code tant que certaines conditions sont remplies, rendant le code plus compact et évitant la duplication.

**Variations possibles** :
- **`for`** : Exécute un bloc de code un nombre prédéterminé de fois, avec une variable de boucle qui s'incrémente ou se décrémente à chaque itération.
- **`while`** : Continue à exécuter un bloc de code tant que la condition est vraie.
- **`do-while`** : Similaire à `while`, mais garantit l'exécution du bloc de code au moins une fois avant de vérifier la condition.
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
