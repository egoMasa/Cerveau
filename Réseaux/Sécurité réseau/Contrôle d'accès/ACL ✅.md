# Guide ACL

## I) Principe et explication

* Une ACL est une liste de règles qui va être mise en place sur un réseau. Son but est de filtrer les paquets qui ont le droit de circuler ou non.  Elle intervient sur les couches Transport (UDP/TCP) et Réseau(IP).

❗On peut définir une seule ACL dans un sens par interface.

* Il existe deux types d’ACL : 

	-   ***ACL Standard*** = Placé près de destination, permet d’analyser le trafic qu’à partir de l’adresse IP source, donc faible précision. Elles sont numérotées de ***1-99*** et ***1300-1999***
    
	-   ***ACL Étendues*** = Placé près de source, permet d’analyser le trafic en fonction de plusieurs critères, donc plus grande précision. Elles sont numérotées de ***100-199*** et ***2000-2699***
    

* Elles permettent deux actions : ***permit/deny***. Selon nos besoins de filtrage on renseigne ce dont on a besoin. Exemple : Empêcher les requêtes TCP d’une source précise ou inversement.

## ACL IPv4
### Commandes ACL standard

1.  ***Création ACL***
```bash
R1(config)#access-list @numero @permit|deny @ip_source @masque_invert  
R1(config)#access-list @numero permit any
```

❗Il faut renseigner le fait que tous les autres traffic puissent passer malgré les ACL car par défaut il bloque tout le reste.

2.  ***Activation sur interface***
```bash
R1(config)#interface @interface  
R1(config-if)#ip access-group @num @in|out
```

### Commandes ACL Etendue

1.  ***Création ACL***
```bash
R1(config)#access-list @numero @permit|deny @protocole @ip_source @masque_invert @ip_desti @masque_invert  
R1(config)#access-list @numero permit any any
```
ou
```bash
R1(config)#access-list @numero @permit|deny @protocole host @ip_a host @ip_b 
R1(config)#access-list @numero permit any any
```

2.  ***Activation sur interface***
```bash
R1(config)#interface @interface  
R1(config-if)#ip access-group @num @in|out
```

### Commandes ACL Etendue nommée

1.  ***Création ACL***
```bash
R1(config)#ip access-list @extended|standard @nom  
R1(config-ext-nacl)#permit|deny @protocole @ip @masque_invert any eq @port
```

2.  ***Activation sur interface***
```bash
R1(config)#interface @interface  
R1(config-if)#ip access-group @num @in|out
```

3. Afficher différentes ACL 
```cisco
#show access-lists
```

## ACL IPv6

* Tout est interdit par défaut (deny any any)
* Il faut appliquer la liste sur une interface en entrée ou sortie
* A partir du moment où l'on autorise certains trafics, tout le reste qui n'est pas renseigné se retrouve bloqué
### Configuration
* Créer ACL
```
ipv6 access-list NOM
	deny @protocol @source @destination
	permit @protocol @source @destination
```
* Application ACL sur interface {IN/OUT}
```
interface G0/0/0
	ipv6 traffic-filter NOM
```
### Exemple 
```cisco
ipv6 access-list BLOCK_HTTPS
	deny tcp any host 2001:DB8:1:30::30 eq www 
	deny tcp any host 2001:DB8:1:30::30 eq 443
	permit ipv6 any any
interface gigabitEthernet 0/1
	ipv6 traffic-filter BLOCK_HTTPS in
```