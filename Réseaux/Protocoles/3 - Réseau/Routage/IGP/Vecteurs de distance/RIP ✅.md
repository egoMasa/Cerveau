
# Guide RIP
Le RIP est l'un des plus anciens protocoles de routage utilisés dans les réseaux IP. En raison de sa simplicité, il est généralement recommandé pour de petits réseaux. Toutefois, en raison de ses limitations, il n'est pas idéal pour les grands réseaux ou les réseaux complexes.

## Versions :

Il existe deux versions principales de RIP :

1. **RIP Version 1 (RIPv1) :**
    
    - **Diffusion** : RIPv1 envoie ses mises à jour de routage en utilisant le _**BROADCAST**_. Cela signifie que chaque mise à jour est envoyée à toutes les machines du réseau, qu'elles soient des routeurs ou non.
    - **Sous-réseaux** : RIPv1 ne supporte pas le CIDR (Classless Inter-Domain Routing) ou VLSM (Variable Length Subnet Masking). Ainsi, il ne peut pas gérer les sous-réseaux. C'est l'une des principales raisons pour lesquelles cette version est considérée comme obsolète pour les réseaux modernes.
    - **Authentification** : RIPv1 ne supporte pas l'authentification, ce qui peut poser des problèmes de sécurité.
2. **RIP Version 2 (RIPv2) :**
    
    - **Multidiffusion** : Contrairement à RIPv1, RIPv2 envoie ses mises à jour de routage en _**MULTICAST**_ à l'adresse 224.0.0.9. Cela signifie que seuls les dispositifs qui écoutent cette adresse (typiquement d'autres routeurs RIP) recevront et traiteront les mises à jour.
    - **Sous-réseaux** : RIPv2 supporte CIDR et VLSM, lui permettant de gérer efficacement les sous-réseaux.
    - **Authentification** : RIPv2 introduit un mécanisme d'authentification simple, améliorant ainsi la sécurité des mises à jour de routage.

## Limitations du RIP :

- **Comptage à l'infini** : RIP a une métrique maximale de 15, ce qui signifie que tout réseau situé à plus de 15 sauts est considéré comme inaccessible. C'est une limitation majeure pour les grands réseaux.
- **Temps de convergence** : RIP peut mettre beaucoup de temps à converger, surtout après un changement dans le réseau. Cela peut entraîner des périodes d'indisponibilité.
- **Mises à jour périodiques** : RIP envoie des mises à jour complètes à intervalles réguliers (toutes les 30 secondes pour RIPv1), ce qui peut générer beaucoup de trafic inutile sur le réseau.

## Configuration de RIP 

### IPv4

- **Activer RIP sur le routeur** :
```
R1(config)#router rip
```
- **Annoncer un réseau voisin** :
 ```
R1(config-router)#network @ip_reseau_voisin
```
- **Changer la version de RIP** :
 ```
R1(config-router)#version 2
``` 
- **Désactiver le résumé automatique des routes** :
```
R1(config-router)#no auto-summary
```
En désactivant le résumé automatique, vous permettez à RIP de prendre en charge VLSM et CIDR. C'est souvent recommandé pour éviter des surprises avec les résumés automatiques.
    
- **Partager la route par défaut** :
```
R1(config-router)#default-information originate
```
- **Empêcher une interface de partager les mises à jour de la table de routage** :
```
R1(config-router)#passive-interface @interface
```

### IPv6

- **Activer le routage IPv6** :
```
ipv6 unicast-routing
```
Cette commande est nécessaire pour activer le routage IPv6 sur le routeur.
- **Configurer RIP pour IPv6** :
```
ipv6 router rip @nom
```
Ici, `@nom` est le nom que vous donnez à votre processus RIPng (RIP pour IPv6).
- **Configurer une interface pour RIPng** :
```
int @int     
	ipv6 address 2001:db8:cafe::1/64     
	ipv6 rip @nom enable
```  
- **Configurer une adresse de résumé pour RIPng** :
```
ipv6 rip NOM summary-address PREFIX/MASQUE
```
Remplacez `NOM` par le nom du processus RIPng, `PREFIX` par l'adresse IPv6 de résumé, et `MASQUE` par le masque associé.

- **Vérifier les routes RIP pour IPv6** :
```
sh ipv6 route rip
```
- **Afficher les protocoles RIP actifs pour IPv6** :
```
sh ipv6 rip protocols
```
- **Voir un résumé des interfaces IPv6** :
```
sh ipv6 int brief
```