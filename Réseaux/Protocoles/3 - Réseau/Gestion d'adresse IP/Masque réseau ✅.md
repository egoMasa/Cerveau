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

# Tableau des maques 
|CIDR|[bits](https://fr.wikipedia.org/wiki/Bit "Bit") disponibles|Masque de sous-réseau|Nombre d'hôtes par sous-réseau|
|---|---|---|---|
|/1|31|128.0.0.0|231-2 = 2 147 483 646|
|/2|30|192.0.0.0|230-2 = 1 073 741 822|
|/3|29|224.0.0.0|229-2 = 536 870 910|
|/4|28|240.0.0.0|228-2 = 268 435 454|
|/5|27|248.0.0.0|227-2 = 134 217 726|
|/6|26|252.0.0.0|226-2 = 67 108 862|
|/7|25|254.0.0.0|225-2 = 33 554 430|
|/8|24|255.0.0.0|224-2 = 16 777 214|
|/9|23|255.128.0.0|223-2 = 8 388 606|
|/10|22|255.192.0.0|222-2 = 4 194 302|
|/11|21|255.224.0.0|221-2 = 2 097 150|
|/12|20|255.240.0.0|220-2 = 1 048 574|
|/13|19|255.248.0.0|219-2 = 524 286|
|/14|18|255.252.0.0|218-2 = 262 142|
|/15|17|255.254.0.0|217-2 = 131 070|
|/16|16|255.255.0.0|216-2 = 65 534|
|/17|15|255.255.128.0|215-2 = 32 766|
|/18|14|255.255.192.0|214-2 = 16 382|
|/19|13|255.255.224.0|213-2 = 8 190|
|/20|12|255.255.240.0|212-2 = 4 094|
|/21|11|255.255.248.0|211-2 = 2 046|
|/22|10|255.255.252.0|210-2 = 1 022|
|/23|9|255.255.254.0|29-2 = 510|
|/24|8|255.255.255.0|28-2 = 254|
|/25|7|255.255.255.128|27-2 = 126|
|/26|6|255.255.255.192|26-2 = 62|
|/27|5|255.255.255.224|25-2 = 30|
|/28|4|255.255.255.240|24-2 = 14|
|/29|3|255.255.255.248|23-2 = 6|
|/30|2|255.255.255.252|22-2 = 2|
|/31|1|255.255.255.254|21-0 =2|
|/32|0|255.255.255.255|20-0 =1|