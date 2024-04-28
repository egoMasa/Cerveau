# Sommaire 

1. Introduction à l'assembleur
	- **Architecture du processeur** : Comprendre le modèle de l'architecture ciblée (registres, pile, file d'instructions, etc.).
	- **Syntaxe de base** : Notation, conventions d'écriture, et structure des programmes en assembleur.
 2. Variables et Types de données
	- **Déclaration** : Comment définir des variables en assembleur (mots, double mots, etc.).
	- **Accès et manipulation** : Accès direct et indirect via des registres et des adresses.
3. Opérations de base
	- **Opérations arithmétiques** : ADD, SUB, MUL, DIV, et leurs spécificités en assembleur.
	- **Opérations logiques** : AND, OR, XOR, NOT.
	- **Déplacement de données** : Instructions MOV, PUSH, POP.
4. Contrôle de flux
	- **Instructions conditionnelles** : JMP, JE (jump if equal), JNE (jump if not equal), et autres instructions de saut conditionnel.
	- **Boucles** : Création de boucles avec des sauts conditionnels et des étiquettes (labels).
5. Fonctions et procédures
	- **Définition** : Comment définir des fonctions en assembleur.
	- **Appel et retour de fonction** : CALL, RET, et la gestion de la pile pour passer des arguments.
6. Gestion de la mémoire
	- **Allocation** : Réserver de l'espace mémoire avec des directives comme DB, DW, DD pour déclarer des variables de différentes tailles.
	- **Accès mémoire** : Instructions pour lire et écrire dans la mémoire.
7. Entrées et sorties
	- **Accès aux périphériques** : Manipulation des ports et des interruptions pour lire et écrire des données.
	- **Utilisation des interruptions systèmes** : Utiliser des interruptions pour les entrées/sorties avec le système d'exploitation.
8. Debugging et optimisation
	- **Techniques de debugging** : Suivi de l'exécution, points d'arrêt, et inspection de la pile et des registres.
	- **Optimisation du code** : Techniques pour rendre le code assembleur plus rapide et plus compact.
9. Aspects avancés
	- **Programmation Inline** : Mélanger l'assembleur avec d'autres langages comme C ou C++ pour des opérations spécifiques à haute performance.
	- **Assembleur pour différentes architectures** : Differences entre les assembleurs pour ARM, x86, x64, etc.
10. Conclusion
	- **Meilleures pratiques** : Conventions de codage en assembleur et conseils pour maintenir la lisibilité et la maintenabilité du code.

# 1) Introduction à l'assembleur

## Différentes architectures de processeur

Les architectures de processeur définissent comment les processeurs sont conçus pour exécuter des instructions machine. Ces architectures influencent directement la manière dont le logiciel, en particulier les systèmes d'exploitation et les applications bas niveau, est écrit et exécuté. Voici une vue d'ensemble des deux principales catégories d'architectures de processeur : RISC (Reduced Instruction Set Computer) et CISC (Complex Instruction Set Computer), ainsi que quelques architectures spécifiques notables.

## Pourquoi différentes architectures existent-elles ?

1. **Optimisation pour différents usages** : Certaines architectures sont optimisées pour la performance générale, d'autres pour la consommation énergétique ou le coût.
2. **Héritage et compatibilité** : Les anciennes architectures souvent continuent d'évoluer pour maintenir la compatibilité avec les logiciels existants.
3. **Innovation technologique** : Les nouvelles technologies peuvent mener à de nouvelles architectures ou sous-architectures pour mieux exploiter ces avancées.

## CISC (Complex Instruction Set Computer)

- **Caractéristiques** : Les architectures CISC ont des instructions de taille variable et des modes d'adressage complexes. Elles peuvent exécuter des commandes de haut niveau via une seule instruction.
- **Avantages** : Moins de travail pour le compilateur, puisque les instructions sont plus proches des constructions de haut niveau.
- **Inconvénients** : Plus complexe en termes de conception de matériel, potentiellement moins efficace en termes de cycles d'exécution par instruction.
- **Exemple typique** : x86 (utilisé dans la plupart des PC).

## RISC (Reduced Instruction Set Computer)

- **Caractéristiques** : Les architectures RISC utilisent des instructions de taille fixe et un nombre limité de modes d'adressage simples. Chaque instruction est conçue pour être exécutée en un seul cycle d'horloge.
- **Avantages** : Plus simple à implémenter au niveau du silicium, peut offrir de meilleures performances grâce à une exécution plus prévisible et rapide des instructions.
- **Inconvénients** : Demande plus de travail du compilateur pour optimiser le code source en instructions simples.
- **Exemple typique** : ARM (utilisé dans la plupart des smartphones), MIPS (utilisé dans des systèmes embarqués).

## Comparaison entre quelques architectures spécifiques

|Architecture|Type|Usage Typique|Instructions|Performance|Économie d'énergie|
|---|---|---|---|---|---|
|**x86**|CISC|Ordinateurs de bureau et portables, serveurs|Complexes, de taille variable|Très haute|Modérée|
|**ARM**|RISC|Smartphones, tablettes, systèmes embarqués|Simples, de taille fixe|Haute|Excellente|
|**MIPS**|RISC|Systèmes embarqués, académique|Simples, de taille fixe|Modérée|Bonne|
|**PowerPC**|RISC|Serveurs, consoles de jeu, systèmes embarqués|Simples, de taille fixe|Haute|Bonne|

## Pourquoi ces différences sont-elles importantes ?

- **Développement logiciel** : Les programmeurs doivent comprendre les architectures pour optimiser le logiciel, particulièrement pour des applications sensibles à la performance ou à l'énergie.
- **Sélection de matériel** : Choisir le bon type de processeur peut affecter la performance générale, le coût, et la consommation énergétique d'un système.
- **Éducation et recherche** : Les chercheurs et étudiants en informatique étudient ces différences pour innover et améliorer les technologies existantes.

Les architectures de processeur sont donc cruciales non seulement pour les concepteurs de matériel informatique mais aussi pour les développeurs de logiciels, les décideurs en technologie, et les chercheurs. Comprendre les forces et les limites de chaque architecture aide à mieux choisir et utiliser la technologie appropriée pour des besoins spécifiques.

## 1.1 Architecture du processeur

L'architecture du processeur définit comment le processeur est construit et fonctionne, incluant les registres, la pile (stack), et la file d'instructions. Les registres sont des emplacements de mémoire très rapides directement dans le CPU, utilisés pour des calculs rapides et le stockage temporaire de données. La pile est une structure de données de type LIFO (Last In, First Out) utilisée pour gérer les appels de fonctions, y compris les paramètres passés et les adresses de retour. Comprendre comment ces éléments interagissent est crucial pour écrire un code assembleur efficace.

**Exemple en code** (x86) :
```assembly
; Exemple simple en assembleur x86
section .text
global _start

_start:
    mov edx, len    ; Longueur de la chaîne pour l'appel système write
    mov ecx, msg    ; Message à écrire
    mov ebx, 1      ; Descripteur de fichier (1 pour stdout)
    mov eax, 4      ; Numéro de l'appel système pour write
    int 0x80        ; Interruption pour appeler le système

    mov eax, 1      ; Numéro de l'appel système pour exit
    int 0x80        ; Sortie du programme

section .data
msg db 'Bonjour, monde!',0xa ; Chaîne à imprimer
len equ $ - msg             ; Calcul de la longueur de la chaîne
```

## 1.2. Syntaxe de base

La syntaxe de l'assembleur varie entre les différentes architectures, mais il y a des conventions communes. Les programmes en assembleur sont divisés en sections telles que `.text` (code), `.data` (données statiques), et `.bss` (données non initialisées). Les instructions elles-mêmes consistent généralement en un mnémonique suivi par des opérandes. Le mnémonique est une abréviation qui représente l'opération à effectuer, tandis que les opérandes indiquent où trouver les données à traiter ou où les stocker.

**Exemple en code** (x86) :
```assembly
section .data
    hello db 'Hello, world!', 0 ; Chaîne terminée par null

section .text
global _start

_start:
    mov eax, 1      ; Code de l'appel système sys_exit
    mov ebx, 0      ; Code de sortie
    int 0x80        ; Appel au système pour terminer le programme
```

Dans cet exemple, le programme en assembleur imprime simplement une chaîne de caractères sur la console et se termine. Les directives `mov` placent des valeurs dans des registres, et `int 0x80` est utilisé pour faire des appels système à l'OS Linux.

**Variations possibles** :
- **Syntaxe Intel vs AT&T** : En assembleur x86, la syntaxe Intel est la plus couramment utilisée sous Windows et par NASM, tandis que la syntaxe AT&T est utilisée par les compilateurs GNU GCC sur les systèmes UNIX/Linux.
- **Différents assembleurs** : NASM, MASM, GAS, et d'autres ont des syntaxes légèrement différentes et des directives spécifiques à l'assembleur.

L'étude de l'architecture du processeur et de la syntaxe de l'assembleur fournit la fondation nécessaire pour écrire des programmes efficaces qui interagissent directement avec le matériel de l'ordinateur.

# 2) Variables et Types de données

## 2.1 Déclaration

En assembleur, les variables sont déclarées en réservant explicitement de l'espace dans la mémoire. Vous pouvez définir des variables de différents types selon la taille des données que vous souhaitez stocker. Les types de données communs incluent :
- **Byte (db)** : Pour stocker un seul octet. Utilisé pour les caractères ou de petites valeurs.
- **Word (dw)** : Pour stocker un mot (2 octets sur les architectures 16 bits).
- **Double word (dd)** : Pour stocker un double mot (4 octets sur les architectures 32 bits).
- **Quad word (dq)** : Pour stocker un quad mot (8 octets sur les architectures 64 bits).
- **Ten bytes (dt)** : Pour stocker 10 octets, souvent utilisé pour les données à virgule flottante étendues.

**Exemple en code** (NASM) :
```assembly
section .data
    unByte db 0x55             ; Déclare un byte
    unMot dw 0x1234            ; Déclare un mot
    doubleMot dd 0x789ABCDE    ; Déclare un double mot
    quadMot dq 0x123456789ABCDEF00 ; Déclare un quad mot

section .bss
    buffer resb 64             ; Réserve 64 bytes sans initialisation
```

Dans cet exemple, différentes variables sont déclarées avec différentes tailles dans la section `.data`, où les données sont initialisées, et un espace mémoire est réservé dans la section `.bss` pour un buffer sans initialisation initiale.

## 2.2 Accès et manipulation

L'accès aux données en assembleur peut être direct (en utilisant directement des adresses ou des valeurs) ou indirect (en utilisant des registres pour pointer vers des adresses). La manipulation des données peut inclure lire, écrire ou modifier les valeurs stockées dans la mémoire.

- **Accès direct** : Spécifiez directement l'adresse ou la valeur lors de l'écriture des instructions.
- **Accès indirect** : Utilisez des registres qui contiennent des adresses pointant vers les données. Cela permet des opérations plus dynamiques et puissantes, comme l'indexation de tableaux ou la manipulation de structures de données complexes.

**Exemple en code** (NASM) :
```assembly
section .data
    valeur dd 0x07

section .text
global _start

_start:
    mov eax, [valeur]    ; Accès direct à 'valeur'
    add eax, 1           ; Incrémente la valeur
    mov [valeur], eax    ; Stocke la valeur incrémentée

    ; Utilisation de l'accès indirect
    lea ebx, [valeur]    ; Charge l'adresse de 'valeur' dans ebx
    mov ecx, [ebx]       ; Move la valeur à l'adresse contenue dans ebx vers ecx
    add ecx, 1           ; Incrémente la valeur
    mov [ebx], ecx       ; Met à jour la valeur à l'adresse stockée dans ebx

    ; Terminaison du programme (Linux)
    mov eax, 1           ; syscall pour terminer le programme
    xor ebx, ebx         ; status 0
    int 0x80
```

Dans cet exemple, `valeur` est manipulée directement puis indirectement à l'aide de registres. Ces techniques montrent comment les données peuvent être manipulées en mémoire de manière flexible et puissante en assembleur.


# 3) Opérations de base

## 3.1 Opérations arithmétiques

Les opérations arithmétiques en assembleur permettent de réaliser des calculs basiques comme l'addition, la soustraction, la multiplication, et la division. Chaque opération a ses propres spécificités, et il est important de noter que la gestion des erreurs (comme la division par zéro) doit être explicitement contrôlée par le programmeur.
- **ADD** : Additionne deux valeurs.
- **SUB** : Soustrait deux valeurs.
- **MUL** : Multiplie deux valeurs. Attention, `MUL` peut rapidement générer des valeurs qui dépassent la taille des registres si on ne prend pas garde.
- **DIV** : Divise deux valeurs. Le dividende est généralement dans `AX` (ou `EAX`, `RAX` selon la taille du registre), et le résultat est placé dans `AX` avec le reste dans `DX`.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov eax, 5
    mov ebx, 2

    add eax, ebx    ; eax = eax + ebx -> 5 + 2 = 7
    sub eax, 1      ; eax = eax - 1 -> 7 - 1 = 6
    mul ebx         ; eax = eax * ebx -> 6 * 2 = 12
    ; Diviser dx:ax par ebx, résultat dans eax, reste dans edx
    mov edx, 0      ; Nettoyer edx pour la division
    div ebx         ; eax = 12 / 2 = 6, reste = 0

    ; Terminaison du programme (Linux)
    mov eax, 1      ; syscall pour terminer le programme
    xor ebx, ebx    ; status 0
    int 0x80
```

## 3.2 Opérations logiques

Les opérations logiques manipulent les bits des données. Ces opérations sont cruciales pour le contrôle des flux, les tests de conditions, et la manipulation de masques de bits.
- **AND** : Effectue un ET logique bit à bit.
- **OR** : Effectue un OU logique bit à bit.
- **XOR** : Effectue un OU exclusif logique bit à bit.
- **NOT** : Inverse les bits d'une valeur.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov eax, 0x0F        ; eax = 00001111
    mov ebx, 0x33        ; ebx = 00110011

    and eax, ebx         ; eax = 00001111 AND 00110011 = 00000011
    or eax, 0x04         ; eax = 00000011 OR 00000100 = 00000111
    xor eax, 0x07        ; eax = 00000111 XOR 00000111 = 00000000
    not eax              ; eax = NOT 00000000 = FFFFFFFF

    ; Terminaison du programme (Linux)
    mov eax, 1           ; syscall pour terminer le programme
    xor ebx, ebx         ; status 0
    int 0x80
```

## 3.3 Déplacement de données

Les instructions de déplacement de données sont utilisées pour transférer des données d'un emplacement à un autre sans les modifier. Cela inclut les opérations de copie entre registres, de la mémoire aux registres, et vice-versa.
- **MOV** : Copie une valeur de la source vers la destination.
- **PUSH** : Pousse une valeur sur la pile.
- **POP** : Retire la dernière valeur poussée de la pile et la place dans un registre.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov eax, 10         ; Met 10 dans eax
    push eax            ; Pousse la valeur de eax sur la pile
    mov ebx, 20         ; Met 20 dans ebx
    pop ecx             ; Passe la valeur du sommet de la pile dans ecx (10)
    mov edx, ebx        ; Copie ebx (20) dans edx

    ; Terminaison du programme (Linux)
    mov eax, 1          ; syscall pour terminer le

 programme
    xor ebx, ebx        ; status 0
    int 0x80
```

Ces exemples illustrent comment manipuler les données et effectuer des opérations basiques en assembleur, fondamentaux pour la programmation à ce niveau de bas niveau.



# 4) Contrôle de flux 

## 4.1 Instructions conditionnelles

Les instructions conditionnelles en assembleur sont utilisées pour contrôler le flux d'exécution du programme en fonction de l'état des flags dans le registre des flags. Ces flags sont mis à jour suite à des opérations arithmétiques ou logiques précédentes. Les sauts conditionnels permettent d'exécuter des sections de code seulement si certaines conditions sont remplies.
- **JMP** (Jump) : Effectue un saut inconditionnel à l'adresse ou à l'étiquette spécifiée.
- **JE/JZ** (Jump if Equal/Jump if Zero) : Saute à l'étiquette si le résultat de la dernière opération était zéro (égalité).
- **JNE/JNZ** (Jump if Not Equal/Jump if Not Zero) : Saute à l'étiquette si le résultat de la dernière opération n'était pas zéro.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov eax, 1
    cmp eax, 2       ; Compare eax avec 2
    je equal         ; Saute à 'equal' si eax est égal à 2
    jne notequal     ; Saute à 'notequal' si eax n'est pas égal à 2

equal:
    mov ebx, 1
    jmp end

notequal:
    mov ebx, 0

end:
    ; Terminaison du programme (Linux)
    mov eax, 1       ; syscall pour terminer le programme
    int 0x80
```

Dans cet exemple, le programme saute aux blocs de code marqués par les étiquettes `equal` ou `notequal` en fonction du résultat de la comparaison entre `eax` et `2`.
## 4.2 Boucles

Les boucles en assembleur sont créées en utilisant des instructions de saut pour répéter des sections de code. Les boucles nécessitent généralement un compteur ou une condition de terminaison pour éviter que la boucle devienne infinie.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov ecx, 5       ; Initialise le compteur à 5

loop_start:
    ; Effectuer des opérations ici
    dec ecx          ; Décrémente ecx de 1
    jnz loop_start   ; Continue la boucle si ecx n'est pas zéro

    ; Terminaison du programme (Linux)
    mov eax, 1       ; syscall pour terminer le programme
    xor ebx, ebx     ; status 0
    int 0x80
```

Dans cet exemple, la boucle continue de s'exécuter jusqu'à ce que le compteur (`ecx`) atteigne zéro. Chaque passage dans la boucle décrémente le compteur de 1. L'instruction `jnz` (Jump if Not Zero) est utilisée pour répéter la boucle tant que `ecx` n'est pas égal à zéro.


# 5) Fonctions et procédures

## 5.1 Définition

En assembleur, les fonctions sont définies comme des blocs de code isolés qui peuvent être appelés depuis différentes parties du programme. Les fonctions sont utiles pour organiser le code en unités logiques réutilisables. En assembleur, les fonctions sont souvent désignées par des étiquettes et peuvent être composées de n'importe quelle séquence d'instructions terminée par un `RET` pour retourner au point d'appel.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

; Définition de la fonction
add_numbers:
    mov eax, [esp+4]  ; Premier argument
    add eax, [esp+8]  ; Additionne avec le deuxième argument
    ret               ; Retourne avec le résultat dans eax

_start:
    push 3            ; Pousse le deuxième argument
    push 2            ; Pousse le premier argument
    call add_numbers  ; Appelle la fonction add_numbers
    add esp, 8        ; Nettoie la pile

    ; Terminaison du programme (Linux)
    mov eax, 1        ; syscall pour terminer le programme
    int 0x80
```

Dans cet exemple, une fonction `add_numbers` est définie pour additionner deux nombres. Les arguments sont passés par la pile et l'instruction `ret` renvoie le contrôle au point d'appel.

## 5.2 Appel et retour de fonction

L'appel à une fonction en assembleur est réalisé avec l'instruction `CALL`, qui pousse l'adresse de retour (l'adresse suivante dans le code après l'appel) sur la pile et transfère le contrôle à l'adresse de la fonction. Le retour de la fonction est géré par l'instruction `RET`, qui pop l'adresse de retour de la pile et transfère le contrôle à cette adresse.

**Gestion de la pile pour passer des arguments** :
Les arguments peuvent être passés à la fonction en les empilant avant d'appeler la fonction. Après l'appel, il est courant que la fonction ou le code appelant nettoie la pile en ajustant le pointeur de pile (`esp`).

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

; Fonction pour multiplier deux nombres
multiply:
    mov eax, [esp+4]  ; Charge le premier argument dans eax
    imul eax, [esp+8] ; Multiplie eax par le deuxième argument
    ret               ; Retourne avec le résultat dans eax

_start:
    push 10           ; Pousse le deuxième argument
    push 5            ; Pousse le premier argument
    call multiply     ; Appelle la fonction multiply
    add esp, 8        ; Nettoie la pile après l'appel

    ; Terminaison du programme (Linux)
    mov eax, 1        ; syscall pour terminer le programme
    int 0x80
```

Dans cet exemple, une fonction `multiply` multiplie deux nombres passés en arguments sur la pile. L'instruction `imul` est utilisée pour la multiplication, et `ret` renvoie au point d'appel. Après l'appel à `multiply`, le code appelant nettoie la pile en ajustant `esp`.


# 6) Gestion de la mémoire

## 6.1 Allocation

En assembleur, l'allocation de mémoire statique est réalisée en réservant explicitement de l'espace dans la mémoire lors de la compilation. Les directives comme `DB` (Define Byte), `DW` (Define Word), `DD` (Define Doubleword), et `DQ` (Define Quadword) sont utilisées pour déclarer des variables de différentes tailles dans les sections de données du programme.
- **DB** : Réserve un ou plusieurs bytes.
- **DW** : Réserve un ou plusieurs mots de 16 bits.
- **DD** : Réserve un ou plusieurs double mots de 32 bits.
- **DQ** : Réserve un ou plusieurs quad mots de 64 bits.

**Exemple en code** (NASM) :
```assembly
section .data
    monByte db 0xFF                 ; Réserve un byte
    monMot dw 0xFFFF                ; Réserve un mot (2 bytes)
    monDoubleMot dd 0xFFFFFFFF      ; Réserve un double mot (4 bytes)
    monQuadMot dq 0xFFFFFFFFFFFFFFFF; Réserve un quad mot (8 bytes)

section .bss
    buffer resb 64                  ; Réserve 64 bytes sans initialisation
```

Dans cet exemple, différentes tailles de variables sont déclarées et réservées dans la section `.data` pour les données initialisées et `.bss` pour les données non initialisées.

## 6.2 Accès mémoire

L'accès à la mémoire en assembleur se fait principalement par des instructions qui permettent de lire ou d'écrire dans la mémoire à des adresses spécifiques. Les opérations les plus courantes sont réalisées à l'aide des instructions `MOV`, qui transfèrent les données entre la mémoire et les registres, ainsi que d'autres instructions qui manipulent directement les adresses mémoire.
- **MOV** : Transfère les données entre les registres et la mémoire.
- **LEA** (Load Effective Address) : Charge l'adresse effective d'une variable dans un registre.
- **PUSH** et **POP** : Utilisés pour empiler et dépiler des données sur la pile du processeur.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .data
    valeur dd 12345678h

section .text
global _start

_start:
    mov eax, [valeur]  ; Charge le contenu de 'valeur' dans eax
    mov ebx, valeur    ; Charge l'adresse de 'valeur' dans ebx
    lea ecx, [valeur]  ; Charge l'adresse effective de 'valeur' dans ecx

    ; Manipulation des données
    add eax, 1         ; Incrémente la valeur dans eax
    mov [valeur], eax  ; Met à jour la mémoire avec la nouvelle valeur

    ; Terminaison du programme (Linux)
    mov eax, 1         ; syscall pour terminer le programme
    xor ebx, ebx       ; status 0
    int 0x80
```

Dans cet exemple, `eax` est utilisé pour lire la valeur depuis la mémoire, et `ebx` est utilisé pour stocker l'adresse de la variable. `LEA` est utilisé pour obtenir l'adresse effective d'une variable, ce qui est utile pour des calculs d'adresse plus complexes ou pour passer des adresses à des fonctions.

# 7) Entrées et sorties

## 7.1 Accès aux périphériques

En assembleur, l'accès direct aux périphériques se fait souvent par la manipulation des ports d'entrée/sortie et des interruptions matérielles. Chaque périphérique connecté à l'ordinateur, comme le clavier ou la souris, est accessible via des ports spécifiques. Les instructions `IN` et `OUT` sont utilisées pour lire et écrire des données à ces ports.
- **IN** : Lit des données du port d'entrée/sortie spécifié dans un registre.
- **OUT** : Envoie des données à un port d'entrée/sortie spécifié à partir d'un registre.

**Exemple en code** (NASM, architecture x86) :
```assembly
section .text
global _start

_start:
    mov dx, 0x60    ; Port du clavier (port de données)
    in al, dx       ; Lit un byte du clavier et le stocke dans al

    mov dx, 0x64    ; Port de commande du clavier
    out dx, al      ; Envoie le byte lu précédemment au port de commande

    ; Terminaison du programme (Linux)
    mov eax, 1      ; syscall pour terminer le programme
    xor ebx, ebx    ; status 0
    int 0x80
```

## 7.2 Utilisation des interruptions systèmes

Les interruptions systèmes sont des mécanismes par lesquels le logiciel peut interrompre le flux normal du processeur pour exécuter un code spécifique, souvent pour gérer les entrées/sorties comme les lectures de disque, écritures d'écran, etc. Cela inclut l'utilisation d'interruptions logicielles pour invoquer les services du système d'exploitation.
- **INT** : Déclenche une interruption logicielle spécifique, qui est gérée par le système d'exploitation pour effectuer diverses tâches système.

**Exemple en code** (NASM, architecture x86 pour Linux) :
```assembly
section .text
global _start

_start:
    mov eax, 4      ; syscall numéro pour sys_write
    mov ebx, 1      ; descripteur de fichier (1 pour stdout)
    mov ecx, msg    ; adresse du message à écrire
    mov edx, len    ; longueur du message à écrire
    int 0x80        ; exécute le syscall

    mov eax, 1      ; syscall numéro pour sys_exit
    xor ebx, ebx    ; code de sortie
    int 0x80        ; exécute le syscall

section .data
    msg db 'Bonjour, monde!', 0xA
    len equ $ - msg
```

Dans cet exemple, les interruptions système `int 0x80` sont utilisées pour appeler les fonctions du système d'exploitation Linux pour écrire sur la sortie standard et terminer le programme. Le premier appel à `int 0x80` utilise le syscall `sys_write` pour écrire le message "Bonjour, monde!" sur la console, et le second utilise `sys_exit` pour terminer le programme.
