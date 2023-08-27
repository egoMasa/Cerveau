## I) NAT (Network Address Translation)

### Principe et explications :

- Le NAT (Network Address Translation) est un mécanisme permettant à plusieurs machines d'un réseau local d'accéder à Internet à l'aide d'une seule adresse IP publique. C'est une technique indispensable dans le contexte actuel où les adresses IPv4 se font rares. Le routeur, qui est l'équipement central de ce mécanisme, est responsable de la traduction des adresses.
    
- À l'intérieur d'un réseau, chaque machine possède une adresse IP privée, généralement dans les plages 192.168.x.x, 10.x.x.x ou 172.16.x.x à 172.31.x.x. Lorsqu'une machine de ce réseau souhaite accéder à Internet, le routeur remplace l'adresse IP source du paquet (l'adresse privée) par son propre adresse IP publique.
    
- L'utilisation du NAT présente plusieurs avantages. Outre la conservation des adresses IP, le NAT offre un niveau de sécurité supplémentaire car les machines du réseau interne ne sont pas directement accessibles depuis l'extérieur. Seuls les services explicitement autorisés par le routeur sont accessibles.
    

### Types de NAT :

- **NAT Statique** : Il associe une adresse IP interne fixe à une adresse IP externe fixe. Chaque machine du réseau local a une correspondance spécifique et constante avec une adresse IP publique. Cette méthode est coûteuse en termes d'adresses IP et peut présenter des risques de sécurité car la relation entre les adresses internes et externes est toujours la même.
    
- **NAT Dynamique** : Il associe une adresse IP interne à une adresse IP externe à partir d'un pool d'adresses disponibles. La correspondance n'est pas constante et peut changer à chaque nouvelle connexion. C'est le type de NAT le plus couramment utilisé, car il permet de partager une petite plage d'adresses IP publiques avec un grand nombre de machines internes.

### Configuration NAT Statique
1. Définir les interfaces internes et externes
```bash
R1(config)#interface @interface  
R1(config-if)#ip nat inside

R1(config)#interface @interface  
R1(config-if)#ip nat outside
```
1. Configurer la translation statique 
```
R1(config)#ip nat inside source static @ip_reseau_interne @ip_exterieur
```

### Commandes NAT dynamique :

```bash
R1(config)#interface @interface  
R1(config-if)#ip nat inside

R1(config)#interface @interface  
R1(config-if)#ip nat outside

#Définir les adresses qui nécessitent la translation
R1(config)#access-list 1 permit @ip_interne @masque  

#Créer un pool d'adresses IP pour la translation
R1(config)#ip nat pool @nom @ip_debut @ip_fin netmask @masque  

#Associer l'access-list et le pool d'adresses
R1(config)#ip nat inside source liste 1 pool @nom
```

## II) PAT (Port Address Translation)

### Principe et explications :

- Le PAT, souvent considéré comme une extension du NAT, ajoute une autre dimension à la traduction : le port. Cela signifie que plusieurs machines peuvent partager une seule adresse IP publique, non seulement en fonction de leur adresse IP, mais aussi du port sur lequel elles établissent une connexion.
    
- Lorsque les données reviennent au routeur depuis l'Internet, le routeur regarde le port de destination et utilise cette information pour déterminer à quelle machine du réseau interne il doit envoyer ces données.
    
- Cette méthode est largement utilisée dans les réseaux domestiques où de nombreux périphériques peuvent avoir besoin d'accéder à Internet via une seule adresse IP fournie par le fournisseur de services Internet.
    

### Avantages du PAT :

- **Économie d'adresses IP** : Plusieurs hôtes peuvent partager une seule adresse IP pour accéder à Internet.
    
- **Sécurité** : Les hôtes internes sont masqués par l'adresse IP du routeur, rendant difficile pour les acteurs externes malveillants de déterminer la structure du réseau interne.

### Types de PAT :

#### 1. **PAT Dynamique avec un Pool d'adresses :**

- **Principe** : Dans ce type de configuration, le routeur dispose d'un pool d'adresses IP publiques et utilise différentes adresses de ce pool pour remplacer l'adresse IP source des paquets sortants. Le port source est également modifié. Si le pool d'adresses est épuisé et qu'une nouvelle translation doit être effectuée, la demande est généralement mise en file d'attente ou rejetée.
    
- **Avantages** : Permet à un grand nombre d'hôtes internes d'accéder à Internet tout en utilisant une plage d'adresses IP publiques limitée.
    

#### 2. **PAT Dynamique avec une seule adresse :**

- **Principe** : Dans cette méthode, une seule adresse IP publique est utilisée pour tous les hôtes du réseau interne. Le routeur différencie chaque session de communication en modifiant le port source. Chaque hôte interne est associé à un port unique lorsqu'il accède à Internet. Cette technique est également appelée "NAT Overload" car une seule adresse IP est "surchargée" avec plusieurs sessions.
    
- **Avantages** : Economie maximale d'adresses IP. Idéal pour les situations où l'organisation dispose d'une seule adresse IP publique.
    

#### 3. **PAT Statique :**

- **Principe** : Comme son nom l'indique, le PAT statique est une configuration où l'adresse IP et le port sont associés de manière fixe à un hôte interne. Par exemple, un serveur web interne pourrait toujours être traduit en utilisant une adresse IP publique spécifique et le port 80, garantissant que le trafic destiné à ce serveur arrive toujours comme prévu.
    
- **Avantages** : Il est idéal pour les services qui doivent être accessibles publiquement, comme un serveur web ou un serveur de messagerie, car il garantit que l'adresse et le port ne changent jamais.
    

### Exemple :

Imaginez que vous ayez un serveur web interne que vous souhaitez rendre accessible depuis l'extérieur. Vous pourriez configurer un PAT statique pour que tout le trafic entrant sur une adresse IP publique spécifique avec le port 80 soit toujours redirigé vers ce serveur.

### Configuration PAT Statique
1. **Définir les interfaces internes et externes** :
```
R1(config)#interface @interface  
R1(config-if)#ip nat inside

R1(config)#interface @interface 
R1(config-if)#ip nat outside
```
2. Configurer la translation PAT statique (Traduction de port spécifique d'une adresse IP interne vers une adresse IP externe.)
```
R1(config)#ip nat inside source static @protocol @ip_interne @port_interne @ip_externe @port_externe
```
### Configuration PAT pool
1. **Définir les interfaces internes et externes** :
```
R1(config)#interface @interface  
R1(config-if)#ip nat inside

R1(config)#interface @interface 
R1(config-if)#ip nat outside
```
2. **Créer un pool d'adresses IP pour la translation** :
```
R1(config)#ip nat pool @nom @ip_debut @ip_fin netmask @masque
```
3. **Définir les adresses qui nécessitent la translation** :
```
R1(config)#access-list 1 permit @ip_interne @masque_invert
```
4. **Configurer le PAT dynamique pour utiliser le pool d'adresses** :
```
R1(config)#ip nat inside source list 1 pool @nom overload
```
### Configuration PAT sur une adresse 
1. **Définir les interfaces internes et externes** :
```
R1(config)#interface @interface  
R1(config-if)#ip nat inside

R1(config)#interface @interface 
R1(config-if)#ip nat outside
```
2. **Définir les adresses qui nécessitent la translation** :
```
R1(config)#access-list 1 permit @ip_interne @masque_invert
```
3. **Configurer le PAT dynamique pour utiliser l'adresse de l'interface externe** :
```
R1(config)#ip nat inside source list 1 interface @interface overload
```