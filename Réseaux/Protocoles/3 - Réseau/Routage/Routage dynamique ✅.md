## I) Principe et explication

- **Introduction** : Lorsqu'on travaille avec des réseaux complexes par leur taille et par le nombre d’équipements, le routage dynamique devient une solution incontournable pour faciliter la gestion des routes.
    
- **Définition** : Le routage dynamique permet aux routeurs de choisir automatiquement les routes optimales pour acheminer le trafic réseau. Les routeurs partagent et mettent à jour constamment leurs tables de routage pour réagir rapidement aux changements dans le réseau.
    
- **Fonctionnement** :
1. Les routeurs annoncent les réseaux auxquels ils sont connectés à leurs voisins.
2. Ces informations sont transmises de routeur en routeur, formant ainsi une image complète de la topologie du réseau.

- **Terminologies importantes** :
    - _**Convergence**_ : Le temps nécessaire pour que tous les routeurs aient des tables de routage à jour après un changement de topologie.
    - _**Répartition de charge**_ : Possibilité d'utiliser plusieurs chemins pour atteindre une même destination, optimisant ainsi l'utilisation des ressources réseau.
    - _**Distance administrative**_ : Indicateur de la fiabilité d'une source d'information de routage. Une valeur faible signifie une grande fiabilité.
    - _**Métrique**_ : Valeur utilisée par un protocole de routage pour déterminer le chemin optimal vers une destination.

- **Problématiques courantes** : Certaines routes peuvent être privilégiées par un protocole même si elles ne sont pas les plus optimales. C'est pourquoi il est parfois nécessaire d'ajuster manuellement les distances administratives.

## II) Routage Intérieur (IGP)

### 1) Vecteur de distance

- **Principe** : Les protocoles à vecteur de distance utilisent le cumul des distances pour déterminer le chemin optimal.
- **Caractéristiques** :
    - Basé sur le nombre de sauts.
    - Partage complet de la table de routage entre les routeurs voisins.
    - Conçu pour les réseaux de petite à moyenne taille.
    - Convergence relativement lente.
    - Mises à jour fréquentes, souvent via broadcast ou multicast.
- **Exemples de protocoles** :
    - _**EIGRP**_ : Utilise l'adresse multicast `224.0.0.10`.
    - _**RIP/RIPv2**_ : Utilise le port UDP 520 et les adresses `255.255.255.255` ou `224.0.0.9`.

### 2) État de lien (Link-State)

- **Principe** : Ces protocoles évaluent le coût de chaque lien pour déterminer le chemin le plus court.
- **Caractéristiques** :
    - Calcul basé sur des facteurs comme la bande passante.
    - Tous les routeurs ont une vision complète de la topologie.
    - Convergence rapide.
    - Mise à jour immédiate en cas de changement de topologie.
- **Exemples de protocoles** :
    - _**OSPF**_ : Utilise les adresses multicast `224.0.0.5` et `224.0.0.6`.
    - _**IS-IS**_ : Un protocole de routage interne basé sur l'état des liens.

## III) Routage Exterieur (EGP)

### I) Introduction et contexte

Lorsque des réseaux indépendants, également appelés Systèmes Autonomes (AS), souhaitent échanger des informations de routage, ils utilisent ce que l'on appelle des protocoles de routage extérieur (EGP). L'EGP le plus couramment utilisé aujourd'hui est BGP.

### II) Qu'est-ce que BGP ?

BGP, ou Border Gateway Protocol, est le protocole standard pour le routage entre différents systèmes autonomes (AS) sur Internet. Créé pour remplacer EGP (Exterior Gateway Protocol), BGP est crucial pour le bon fonctionnement d'Internet. Il est souvent qualifié de protocole qui "garde Internet en vie".

### Avantages :

1. **Scalabilité** : BGP est conçu pour être évolutif, capable de gérer un très grand nombre de routes. Il est essentiel pour le routage interdomaine, surtout compte tenu de la taille d'Internet aujourd'hui.
2. **Prévisibilité** : BGP ne dépend pas uniquement des métriques, comme le font d'autres protocoles, pour décider du meilleur chemin. Au lieu de cela, il utilise une combinaison d'attributs, de politiques et de préférences.
3. **Filtrage fin** : Le contrôle offert par BGP sur la sélection des routes et leur propagation est sans égal, permettant des décisions de routage précises et ciblées.

### III) Fonctionnement de BGP

#### Attributs de BGP :

Ce sont les éléments clés qui définissent les caractéristiques d'une route dans BGP :

- **AS_PATH** : Il s'agit d'une liste des AS traversés pour parvenir à une route. Cet attribut est crucial pour la prévention des boucles de routage.
- **NEXT_HOP** : Cette adresse IP signale le prochain routeur à utiliser pour atteindre la destination.
- **LOCAL_PREF** : Une valeur utilisée pour choisir une route parmi plusieurs lorsque plusieurs chemins sont disponibles au sein d'un même AS.
- **MED (Multi Exit Discriminator)** : Cet attribut est utilisé pour signaler à un AS voisin quelle entrée est préférée.

#### Décision de routage :

La décision de routage dans BGP n'est pas aussi simple que de choisir la route avec la métrique la plus basse. BGP évalue :

1. La valeur de `LOCAL_PREF`. La route avec la plus grande valeur est préférée.
2. En cas d'égalité, BGP examine `AS_PATH`. La route avec le chemin le plus court est choisie.
3. D'autres attributs comme `MED` peuvent également influencer la décision.

#### eBGP vs iBGP :

BGP peut fonctionner entre routeurs d'un même AS (iBGP) ou entre différents AS (eBGP). Les règles et les comportements peuvent varier entre ces deux modes :

- **eBGP** : Lorsqu'il est utilisé entre AS, il est essentiel pour partager les informations de routage à travers Internet.
- **iBGP** : Au sein d'un AS, iBGP assure la cohérence des informations de routage.

### IV) Enjeux et défis

1. **Sécurité** : BGP n'a pas été conçu avec des mécanismes de sécurité intégrés. Cela le rend vulnérable à certaines menaces, comme le détournement de préfixe. Des solutions telles que RPKI et BGPsec sont en cours de développement pour combler ces lacunes.
2. **Complexité** : La configuration et la gestion de BGP peuvent être délicates. Une mauvaise configuration peut avoir des effets indésirables, non seulement pour le réseau local mais aussi pour d'autres réseaux.
3. **Convergence** : Bien que BGP soit stable, il peut être lent à converger. Cela peut être problématique dans certains scénarios où la rapidité est essentielle.

### V) Conclusion

BGP est indéniablement l'épine dorsale du routage sur Internet. Son rôle est essentiel pour garantir la connectivité entre les nombreux AS qui composent Internet. Bien que complexe, avec les bons outils et une bonne compréhension, BGP offre une flexibilité et une puissance inégalées dans le monde du routage.