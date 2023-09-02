- Compilation et installation d'un nouveau noyau.
- Gestion des modules du noyau.
# Guide sur le kernel
Le noyau (ou "kernel" en anglais) est l'un des éléments fondamentaux d'un système d'exploitation. Dans l'architecture Linux, le noyau a un rôle central et revêt une importance primordiale.

# **Définition**:
Le noyau est le cœur du système d'exploitation. Il fait le lien entre le matériel de l'ordinateur et les logiciels. Il fournit des services essentiels pour le contrôle des ressources matérielles et l'exécution des programmes.

# **Rôles principaux du noyau Linux**:

1. **Gestion des processus** : Le noyau crée, planifie et termine les processus. Un processus est une instance d'un programme en cours d'exécution.

2. **Gestion de la mémoire** : Il contrôle la mémoire RAM, alloue la mémoire aux processus et gère la mémoire virtuelle pour assurer une utilisation efficace de la RAM et du disque.

3. **Gestion des périphériques** : Le noyau interagit avec les périphériques matériels via des pilotes. Les pilotes sont des programmes intégrés au noyau ou ajoutés à celui-ci qui permettent de communiquer avec des périphériques spécifiques.

4. **Gestion des systèmes de fichiers** : Il permet la lecture, l'écriture, la création et la suppression de fichiers et de dossiers sur différents types de systèmes de fichiers (comme ext4, btrfs, xfs).

5. **Gestion des entrées/sorties** : Le noyau gère la communication entre le système et les périphériques externes, que ce soit pour lire un disque ou afficher des informations à l'écran.

6. **Gestion des droits et de la sécurité** : Il définit qui peut faire quoi, contrôlant l'accès aux fichiers et aux ressources système.

# **Comment fonctionne un noyau ?**:

- **Mode utilisateur et mode noyau** : Pour garantir la stabilité et la sécurité, le noyau opère en "mode noyau" (aussi appelé mode superviseur), qui lui donne un accès direct aux ressources matérielles et lui permet d'exécuter des instructions privilégiées. Les applications, quant à elles, fonctionnent en "mode utilisateur", un mode d'exécution plus restreint. Lorsqu'une application a besoin d'accéder à une ressource ou à un service du noyau, elle effectue ce qu'on appelle un "appel système" pour passer du mode utilisateur au mode noyau.

- **Modularité** : Le noyau Linux est modulaire, ce qui signifie qu'il peut charger et décharger des modules (ou des pilotes) à la volée. Cela permet une flexibilité dans la prise en charge du matériel et des fonctionnalités.

- **Monolithique mais modulaire** : Bien que Linux soit souvent décrit comme un noyau monolithique (car tout est inclus dans un noyau unique), sa capacité à charger et décharger des modules le rend également modulaire.

- **Interruptions** : Lorsqu'un périphérique a besoin de l'attention du noyau (par exemple, une touche est pressée ou un paquet réseau arrive), il envoie une interruption. Le noyau répond en suspendant temporairement ce qu'il fait, en traitant l'interruption, puis en revenant à sa tâche précédente.

En résumé, le noyau Linux est le cœur du système d'exploitation, contrôlant tout, des processus aux périphériques matériels. Sa conception et son fonctionnement assurent que les ressources du système sont utilisées efficacement et que les logiciels peuvent fonctionner de manière fiable.

# Compilation et installation d'un nouveau noyau

## Qu'est-ce que la compilation?

La compilation est le processus par lequel du code source, écrit dans un langage de programmation de haut niveau (comme le C ou le C++), est traduit en code machine ou en code intermédiaire, exécutable par un ordinateur. 

Un ordinateur ne comprend directement que le code machine (instructions binaires). Les langages de haut niveau, cependant, sont conçus pour être plus compréhensibles et pratiques pour les humains. Ces langages permettent aux développeurs de créer des programmes sans avoir à se soucier des détails de bas niveau du matériel.

Le compilateur est un logiciel qui prend en entrée le code source et produit un fichier exécutable ou une bibliothèque. Ce fichier exécutable est spécifique à une plateforme et peut être directement exécuté par le système d'exploitation.

## Pourquoi compiler?

1. **Traduction en code exécutable** : Les ordinateurs ne "comprendront" et n'exécuteront que du code machine. Les humains, cependant, trouvent plus facile d'écrire du code dans des langages de haut niveau. La compilation est donc nécessaire pour transformer ce code "humainement compréhensible" en code "machine exécutable".

2. **Optimisation** : Les compilateurs modernes effectuent de nombreuses optimisations lors de la transformation du code source en code machine, garantissant que le programme final est aussi rapide et efficace que possible.

3. **Vérification** : La compilation permet aussi de détecter certaines erreurs dans le code. Si le code source contient des erreurs qui empêchent sa compilation, le compilateur les signalera.

4. **Portabilité** : Le code source écrit dans un langage de haut niveau peut souvent être compilé pour différents systèmes d'exploitation ou architectures matérielles avec peu ou pas de modification. C'est ainsi que le même programme peut fonctionner sur Windows, Linux, macOS, etc.

## Dans le contexte du noyau Linux

Quand on parle de compiler le noyau Linux, il s'agit de prendre le code source du noyau et de le compiler pour créer une version exécutable du noyau adaptée à votre matériel et à vos besoins.

**Pourquoi compilerait-on un noyau Linux ?**

1. **Fonctionnalités spécifiques** : Pour activer ou désactiver certaines fonctionnalités qui ne sont pas configurées de cette manière dans la version standard du noyau fournie par votre distribution.

2. **Support matériel** : Si vous avez du matériel spécifique qui n'est pas pris en charge par le noyau standard ou si vous souhaitez utiliser une version plus récente d'un pilote.

3. **Optimisation** : Vous pourriez vouloir optimiser le noyau pour votre matériel spécifique, en éliminant des composants inutiles pour votre utilisation, ce qui pourrait potentiellement améliorer les performances ou réduire la consommation d'énergie.

4. **Éducation** : Pour ceux qui étudient les systèmes d'exploitation, compiler et modifier le noyau est un excellent moyen d'apprendre comment les choses fonctionnent "sous le capot".

En résumé, la compilation est le processus de transformation du code source en un format que la machine peut exécuter. Dans le contexte du noyau Linux, la compilation vous permet de créer un noyau sur mesure pour vos besoins spécifiques.

## **Étapes de compilation et d'installation d'un nouveau noyau**:

1. **Obtenir le code source** :
- Vous pouvez télécharger le code source du noyau depuis le site officiel du projet Linux ou via des gestionnaires de paquets de votre distribution.

2. **Préparation pour la compilation** :
- Installer les outils nécessaires, tels que le compilateur GCC et d'autres paquets essentiels pour la compilation.

3. **Configuration** :
- Avant de compiler le noyau, vous devez le configurer. Linux offre `make menuconfig`, `make xconfig`, ou `make gconfig` pour cela, qui sont des interfaces pour sélectionner ou désélectionner différentes fonctionnalités, modules et pilotes. Cette étape détermine ce qui sera inclus directement dans le noyau et ce qui sera disponible sous forme de modules.

4. **Compilation** :
- Après la configuration, la compilation proprement dite est lancée avec la commande `make`. Cette étape peut être assez longue, car elle construit le noyau ainsi que tous les modules sélectionnés.

5. **Installation** :
- Une fois la compilation terminée, installez le noyau et ses modules. Cela se fait généralement avec `make modules_install` pour installer les modules, puis `make install` pour installer le noyau lui-même.

6. **Mise à jour du chargeur de démarrage** :
- Après l'installation du noyau, le chargeur de démarrage (comme GRUB) doit être informé de ce nouveau noyau afin que vous puissiez le démarrer. Cela peut souvent être fait automatiquement, mais parfois, vous devrez le configurer manuellement.

7. **Redémarrage** :
- Enfin, redémarrez votre machine. Si tout se passe bien, vous pourrez démarrer avec votre nouveau noyau. Gardez toujours un ancien noyau fonctionnel dans votre chargeur de démarrage comme sauvegarde en cas de problème avec le nouveau.

# Modules du noyau 
Les modules du noyau, souvent simplement appelés "modules", sont des morceaux de code qui peuvent être chargés et déchargés du noyau à la volée, sans avoir besoin de redémarrer le système. Ils permettent une forme de modularité, rendant le noyau Linux extensible.

## C'est quoi un module du noyau?

Un module du noyau est essentiellement un pilote ou une extension du noyau. Au lieu d'inclure toutes les fonctionnalités possibles directement dans le noyau principal (ce qui le rendrait énorme et potentiellement moins efficace), les fonctionnalités optionnelles ou moins courantes sont souvent réalisées sous forme de modules. Ces modules peuvent être chargés quand ils sont nécessaires et déchargés quand ils ne le sont pas.

Par exemple, si vous avez une carte réseau particulière dans votre ordinateur, le pilote pour cette carte peut être un module. Lorsque la carte est présente et que le système démarre, le module est chargé. Si vous retirez la carte ou n'avez plus besoin du pilote, le module peut être déchargé.

## Comment ça marche?

1. **Chargement**: Lorsque le système a besoin d'une fonctionnalité particulière, il peut charger le module correspondant à l'aide de la commande `insmod` ou, plus couramment, `modprobe`. `modprobe` est plus intelligent dans le sens où il peut gérer les dépendances entre les modules.

2. **Liste des modules**: Vous pouvez voir quels modules sont actuellement chargés dans le système à l'aide de la commande `lsmod`.

3. **Déchargement**: Si un module n'est plus nécessaire, il peut être déchargé du noyau à l'aide de la commande `rmmod` ou `modprobe -r`.

4. **Dépendances**: Certains modules dépendent d'autres modules pour fonctionner correctement. Par exemple, un module pilote pour un type particulier de carte réseau pourrait dépendre d'un module de gestion générique Ethernet. La commande `modprobe` est capable de gérer ces dépendances automatiquement.

5. **Automatisation**: Dans les systèmes Linux modernes, l'ajout et le retrait de matériel peuvent déclencher automatiquement le chargement et le déchargement de modules grâce à des systèmes tels qu'`udev`.

6. **Paramètres du module**: Certains modules acceptent des paramètres pour modifier leur comportement. Ces paramètres peuvent être passés lors du chargement du module avec `modprobe` ou définis de manière persistante dans des fichiers de configuration.

7. **Compilation**: Les modules sont généralement compilés en même temps que le noyau lui-même. Cependant, il est également possible de compiler des modules séparément, tant qu'ils sont compatibles avec la version actuelle du noyau en cours d'exécution.

## Pourquoi utiliser des modules?

1. **Taille du noyau**: Garder le noyau lui-même petit et léger, en ne chargeant que les fonctionnalités nécessaires à un moment donné.
   
2. **Flexibilité**: Permettre l'ajout de nouveaux pilotes ou fonctionnalités sans avoir à recompiler ou redémarrer le noyau.

3. **Maintenance et développement**: Les développeurs peuvent travailler sur des modules spécifiques, les tester et les charger sans perturber le reste du système.

4. **Support matériel**: Dans un monde où le matériel change et évolue rapidement, les modules permettent une prise en charge plus facile et plus rapide des nouveaux dispositifs, sans attendre la prochaine version majeure du noyau.

En résumé, les modules du noyau offrent une manière modulaire et flexible d'ajouter des fonctionnalités au noyau Linux sans alourdir le noyau principal. Ils jouent un rôle crucial dans la prise en charge du matériel, l'extensibilité et l'efficacité générale des systèmes Linux.