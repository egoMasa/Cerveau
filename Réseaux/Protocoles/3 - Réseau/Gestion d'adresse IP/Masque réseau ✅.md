# Principe 
* Un masque de sous-réseau est un élément essentiel de l'adressage du Protocole Internet (IP). Il agit comme un "masque" pour séparer la portion réseau d'une adresse IP de sa portion hôte. C'est un nombre de 32 bits composé d'une séquence de 1 suivie d'une séquence de 0, et il est utilisé pour définir la limite d'un sous-réseau dans une adresse IP donnée.

# Objectif

- Définir les limites du réseau.
- Faciliter le routage IP.
- Diviser de grands réseaux IP en sous-réseaux plus petits et gérables.

# Format 
* Le masque de sous-réseau est écrit dans le même format décimal pointé que les adresses IP (c'est-à-dire quatre octets séparés par des points). Par exemple, le masque de sous-réseau par défaut pour une adresse IP de classe A est 255.0.0.0, pour la classe B c'est 255.255.0.0, et pour la classe C c'est 255.255.255.0.

# Importance en cybersécurité 
- Aident à isoler différents segments de votre réseau, conduisant à un meilleur contrôle de la sécurité et une utilisation plus efficace des ressources.
- Facilitent la division des réseaux IP en sous-réseaux plus petits, qui peuvent ensuite être attribués à différents départements, groupes ou fonctions au sein d'une organisation.
- Augmentent l'efficacité du réseau en évitant le trafic de diffusion inutile.
- Améliorent la stabilité globale du réseau et les capacités de surveillance.

* Pour déterminer le masque de sous-réseau approprié en fonction de différents besoins, vous pouvez utiliser divers outils de sous-réseau disponibles en ligne. Une gestion appropriée des masques de sous-réseau est essentielle pour maintenir un réseau sécurisé, efficace et bien fonctionnel.

## **Masque générique (Wildcard mask) :** 
Il est important de noter qu'un masque générique est différent d'un masque de sous-réseau. Alors qu'un masque de sous-réseau est utilisé pour définir la portion réseau d'une adresse IP, un masque générique est souvent utilisé dans les configurations de routeur pour identifier une plage d'adresses. Dans un masque générique, un bit à "0" signifie qu'il doit être vérifié, tandis qu'un bit à "1" signifie qu'il peut être ignoré.

Un masque générique est souvent utilisé dans des situations où vous souhaitez autoriser ou refuser un certain groupe d'adresses. Par exemple, dans la configuration des listes de contrôle d'accès (ACL) sur les routeurs

# Tableau des masques 

| CIDR | [bits](https://fr.wikipedia.org/wiki/Bit "Bit") | Masque de sous-réseau | Wildcard Mask | Nombre d'hôtes par sous-réseau |
|------|-----------------------------------------------|-----------------------|---------------|--------------------------------|
| /1   | 31                                           | 128.0.0.0             | 127.255.255.255 | 2 147 483 646                 |
| /2   | 30                                           | 192.0.0.0             | 63.255.255.255  | 1 073 741 822                 |
| /3   | 29                                           | 224.0.0.0             | 31.255.255.255  | 536 870 910                   |
| /4   | 28                                           | 240.0.0.0             | 15.255.255.255  | 268 435 454                   |
| /5   | 27                                           | 248.0.0.0             | 7.255.255.255   | 134 217 726                   |
| /6   | 26                                           | 252.0.0.0             | 3.255.255.255   | 67 108 862                    |
| /7   | 25                                           | 254.0.0.0             | 1.255.255.255   | 33 554 430                    |
| /8   | 24                                           | 255.0.0.0             | 0.255.255.255   | 16 777 214                    |
| /9   | 23                                           | 255.128.0.0           | 0.127.255.255   | 8 388 606                     |
| /10  | 22                                           | 255.192.0.0           | 0.63.255.255    | 4 194 302                     |
| /11  | 21                                           | 255.224.0.0           | 0.31.255.255    | 2 097 150                     |
| /12  | 20                                           | 255.240.0.0           | 0.15.255.255    | 1 048 574                     |
| /13  | 19                                           | 255.248.0.0           | 0.7.255.255     | 524 286                       |
| /14  | 18                                           | 255.252.0.0           | 0.3.255.255     | 262 142                       |
| /15  | 17                                           | 255.254.0.0           | 0.1.255.255     | 131 070                       |
| /16  | 16                                           | 255.255.0.0           | 0.0.255.255     | 65 534                        |
| /17  | 15                                           | 255.255.128.0         | 0.0.127.255     | 32 766                        |
| /18  | 14                                           | 255.255.192.0         | 0.0.63.255      | 16 382                        |
| /19  | 13                                           | 255.255.224.0         | 0.0.31.255      | 8 190                         |
| /20  | 12                                           | 255.255.240.0         | 0.0.15.255      | 4 094                         |
| /21  | 11                                           | 255.255.248.0         | 0.0.7.255       | 2 046                         |
| /22  | 10                                           | 255.255.252.0         | 0.0.3.255       | 1 022                         |
| /23  | 9                                            | 255.255.254.0         | 0.0.1.255       | 510                           |
| /24  | 8                                            | 255.255.255.0         | 0.0.0.255       | 254                           |
| /25  | 7                                            | 255.255.255.128       | 0.0.0.127       | 126                           |
| /26  | 6                                            | 255.255.255.192       | 0.0.0.63        | 62                            |
| /27  | 5                                            | 255.255.255.224       | 0.0.0.31        | 30                            |
| /28  | 4                                            | 255.255.255.240       | 0.0.0.15        | 14                            |
| /29  | 3                                            | 255.255.255.248       | 0.0.0.7         | 6                             |
| /30  | 2                                            | 255.255.255.252       | 0.0.0.3         | 2                             |
| /31  | 1                                            | 255.255.255.254       | 0.0.0.1         | 2                             |
| /32  | 0                                            | 255.255.255.255       | 0.0.0.0         | 1                             |
