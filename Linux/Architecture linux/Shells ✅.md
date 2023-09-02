# Guide shell 

Un **shell** est une interface qui permet aux utilisateurs d'interagir avec le système d'exploitation. Il peut être graphique (comme les interfaces utilisateur de Windows, macOS, ou certaines versions de Linux) ou basé sur le texte (comme le terminal sur UNIX ou le prompt de commande sur Windows). Dans le contexte du pentesting (test de pénétration) et de la sécurité informatique en général, le terme "shell" est souvent utilisé pour désigner une interface commandée à distance qui a été obtenue sur un système cible, généralement à la suite d'une exploitation.

Quand on parle de shells dans le contexte du pentesting et qu'on dit que certains sont "moins stables" que d'autres, cela peut signifier plusieurs choses :

1. **Durabilité** : Certains shells peuvent se déconnecter ou crasher facilement en fonction de ce que vous faites. Par exemple, un shell obtenu par une exploitation simple pourrait ne pas résister à des tâches comme le transfert de gros fichiers.
    
2. **Interaction** : Certains shells peuvent ne pas supporter toutes les fonctionnalités qu'un pentester pourrait souhaiter, comme le tab-completion, ou pourraient ne pas rendre correctement certaines sorties.
    
3. **Dépendance à l'environnement** : Un shell pourrait être dépendant d'un service ou d'un processus spécifique sur le système cible. Si ce service ou processus est arrêté, le shell pourrait être perdu.
    
4. **Visibilité** : Certains shells, en fonction de la manière dont ils sont instaurés ou maintenus, pourraient être plus visibles pour les outils de détection ou pour un administrateur système vigilant. Un shell "stable" dans ce contexte pourrait être un shell qui est discret et ne déclenche pas d'alertes.
    
5. **Fonctionnalités avancées** : Certains shells, comme les "reverse shells" ou "bind shells", peuvent avoir des limitations en fonction du protocole ou des outils utilisés pour les établir. Par exemple, un simple netcat reverse shell pourrait être considéré comme moins "stable" ou fonctionnel qu'un shell Meterpreter établi via Metasploit, qui offre une multitude de fonctionnalités avancées.
    

C'est pourquoi, dans le monde du pentesting, après avoir obtenu un shell initial, il est courant d'essayer d'améliorer ce shell (par exemple, en l'upgradant vers un shell plus stable ou en établissant une persistance) ou d'utiliser le shell initial comme point d'entrée pour déployer des outils ou des payloads plus avancés et stables sur la cible.

# 2. Reverse/bind shells
Un "reverse shell" et un "bind shell" sont deux types courants de shells à distance utilisés en sécurité informatique, en particulier lors des tests de pénétration et des activités d'exploitation.

1. **Bind Shell** :
    
    - Dans un bind shell, le système cible (la machine compromise) ouvre un port sur lequel il écoute. L'attaquant se connecte ensuite à ce port pour obtenir un shell.
    - Il est appelé "bind" parce que le système cible "lie" un shell à un port d'écoute spécifique.
    - La principale faiblesse de cette approche est qu'elle nécessite que le port sur lequel le système cible écoute soit accessible à l'attaquant. Les pare-feux, les listes de contrôle d'accès et d'autres mécanismes de sécurité peuvent bloquer ces connexions.
2. **Reverse Shell** :
    
    - Dans un reverse shell, c'est l'inverse: après l'exploitation, le système cible établit une connexion sortante vers l'attaquant, qui fournit alors un shell à travers cette connexion.
    - Il est appelé "reverse" parce que c'est le système cible qui initie la connexion vers l'attaquant, contrairement à la norme.
    - Cette méthode est souvent utilisée pour contourner les pare-feux ou les listes de contrôle d'accès qui peuvent bloquer les connexions entrantes mais qui sont moins restrictives pour les connexions sortantes.

**Stabilité** :

- Lorsque l'on parle de la "stabilité" d'un reverse shell ou d'un bind shell, cela peut faire référence à plusieurs facteurs :
    1. **Fiabilité de la connexion** : La connexion peut être interrompue pour diverses raisons (par exemple, en raison de problèmes réseau, de la fin du processus hôte, etc.).
    2. **Détection** : Les mécanismes de détection et de prévention des intrusions (IDPS) peuvent détecter et bloquer ces types de connexions, surtout si elles sont effectuées sans chiffrement ou obfuscation.
    3. **Fonctionnalité** : Certains shells simples peuvent ne pas offrir toutes les fonctionnalités qu'un attaquant pourrait souhaiter (comme le transfert de fichiers, le contrôle de la webcam, etc.), ou pourraient avoir des problèmes d'interaction (par exemple, ne pas traiter correctement la sortie standard ou les erreurs).
    4. **Persistance** : La capacité du shell à rester actif ou à être réactivé après un redémarrage du système ou la fermeture d'une session.

Il est important de noter que le choix entre un reverse shell et un bind shell, ainsi que la considération de leur stabilité, dépendra fortement du contexte de l'attaque, de la configuration de la cible et de l'environnement réseau.

# 3. Attribution de shells 
Lors de la création d'un utilisateur sur un système Linux, un shell est généralement attribué à cet utilisateur. Ce shell détermine l'interface que l'utilisateur verra lorsqu'il se connectera au système via une session terminal ou SSH.

Il existe différents types de shells pour diverses raisons, notamment la compatibilité historique, les préférences des utilisateurs, les fonctionnalités et les besoins en matière de sécurité. Voici quelques-uns des shells les plus courants :

1. **sh (Bourne Shell)** : C'est l'un des premiers shells Unix. Il offre un ensemble de fonctionnalités de base et est généralement disponible sur la plupart des systèmes pour des raisons de compatibilité. Des scripts écrits pour `sh` sont généralement portables entre différents systèmes Unix-like.
    
2. **bash (Bourne Again Shell)** : C'est une amélioration et une extension de `sh`. `bash` est le shell par défaut sur de nombreuses distributions Linux. Il offre de nombreuses améliorations et fonctionnalités supplémentaires par rapport à `sh`, comme la complétion des noms de fichiers, les alias, l'historique des commandes, etc.
    
3. **csh (C Shell)** : Comme son nom l'indique, sa syntaxe est plus proche du langage C. Il y a eu des débats sur sa convenance pour la programmation de scripts, mais il a ses partisans.
    
4. **tcsh** : Une amélioration de `csh` avec des fonctionnalités supplémentaires comme une meilleure complétion automatique et un historique des commandes.
    
5. **ksh (KornShell)** : Fusionne des fonctionnalités de `sh` et `csh`. Il est connu pour ses capacités de script avancées.
    
6. **zsh (Z Shell)** : C'est un shell très extensible avec beaucoup de fonctionnalités qui peuvent être personnalisées. Il combine certaines des meilleures fonctionnalités de `bash`, `ksh`, et `tcsh`.
    
7. **fish (Friendly Interactive Shell)** : Un shell relativement nouveau conçu pour être interactif et convivial, avec une configuration et une coloration syntaxique améliorées, ainsi qu'une complétion automatique sophistiquée.
    
8. **dash** : Une version plus légère de `sh` qui est souvent utilisée pour exécuter des scripts système car elle démarre plus rapidement que `bash`.
    
9. **rbash (Restricted Bash)** : Une version restreinte de `bash` qui limite ce que les utilisateurs peuvent faire. Par exemple, il empêche les utilisateurs de changer de répertoire, de définir des chemins, etc.
    
10. **nologin** : Ce n'est pas vraiment un shell interactif. Lorsqu'un utilisateur a `/usr/sbin/nologin` comme shell, il ne peut pas se connecter au système. C'est utile pour les comptes système qui n'ont pas vocation à être utilisés interactivement.
    

En termes de **fonctionnalités**, `zsh`, `bash` et `fish` sont parmi les plus riches en fonctionnalités, offrant une expérience utilisateur améliorée, une meilleure complétion, des plug-ins, etc.

Pour ce qui est de la **restriction**, `rbash` est une version de `bash` conçue pour être restreinte, et `nologin` empêche complètement la connexion. Il existe aussi `rsh` (Restricted Shell) qui est une version restreinte de `sh`.

Le choix du shell dépend des préférences de l'utilisateur, des besoins en matière de sécurité, et des tâches spécifiques à accomplir.