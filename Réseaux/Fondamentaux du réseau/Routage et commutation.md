# Comprendre la différence entre la commutation et le routage

## I) Commutation

### Principe

- La commutation est une technique utilisée pour transmettre des données (trames) au sein d'un même réseau.
- Elle connecte plusieurs périphériques sur un réseau local (LAN).
- Les commutateurs (switches) sont responsables de cette opération.
- Elle est basée sur l'adresse MAC de la trame.

### Etapes d'envoi de trame

1. Le commutateur reçoit la trame sur un de ses ports.
2. Il extrait l'adresse MAC de destination.
3. Il la compare avec sa MAC Address Table (table des adresses MAC).
4. Si l'adresse MAC est trouvée, la trame est envoyée directement vers le port associé à cette adresse.
5. Si non, la trame est diffusée sur tous les ports sauf le port d'entrée.
6. Quand un hôte répond, le switch ajoute l'adresse MAC source de l'hôte à sa table.

### Etapes de réponse de trame

1. L'hôte destinataire reçoit la trame et répond.
2. Le switch utilise les adresses MAC pour acheminer cette réponse vers l'expéditeur initial.

### Exemple de commutation

- Lorsqu'un hôte A envoie une trame à un hôte B sur le même réseau, le switch utilise sa table pour déterminer le port auquel est connecté l'hôte B et achemine la trame directement vers celui-ci.

## II) Routage

### Principe

- Le routage permet d'acheminer des paquets entre différents réseaux.
- Les routeurs sont les dispositifs responsables de cette opération.
- Ils utilisent les adresses IP pour prendre leurs décisions.
- Le chemin emprunté peut être déterminé à l'aide d'algorithmes de routage.
- Les informations de couche 2 (comme l'adresse MAC) sont remplacées à chaque saut par un routeur.

### Fonctionnement

1. L'hôte source construit un paquet avec une en-tête IP.
2. Le paquet est transmis à la passerelle par défaut (souvent un routeur).
3. Le routeur examine l'en-tête IP pour déterminer l'adresse de destination.
4. Il utilise sa table de routage pour déterminer le prochain saut.
5. Le paquet est ensuite envoyé à un autre routeur ou directement à l'hôte de destination.

### Cas particuliers

- **Routage sur liaison série** : Lors d'une connexion point-à-point, le routeur encapsule le paquet dans le format de trame approprié pour l'interface de sortie (par exemple, HDLC ou PPP). Les adresses de couche 2 ne sont pas nécessaires dans ce contexte.
- **Routage sur liaison normale** : Les adresses MAC source et destination changent à chaque passage par un routeur, tandis que les adresses IP restent constantes tout au long du chemin.

### Modifications des champs

- Quand un hôte A envoie un paquet vers un hôte B via un routeur :
    1. L'adresse MAC source est celle de l'hôte A, l'adresse MAC destination est celle de la passerelle (le routeur).
    2. Quand le routeur reçoit le paquet, il change l'adresse MAC source à celle de son interface de sortie et l'adresse MAC destination à celle du prochain saut ou de l'hôte B si celui-ci est sur le réseau directement connecté.
    3. Sur une liaison série, les informations de couche 2 peuvent ne pas être utilisées.