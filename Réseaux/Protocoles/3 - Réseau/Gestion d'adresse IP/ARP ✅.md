# Guide ARP
# 1) Introduction et Objectif du Protocole ARP

- **ARP (Address Resolution Protocol)** est un protocole qui permet de résoudre des adresses de protocole de couche réseau (comme les adresses IP) en adresses de liaison de données de couche 2 (comme les adresses MAC) sur des réseaux locaux (LAN)
- Alors que la communication sur Internet utilise des adresses IP, les échanges à l'intérieur d'un réseau local se basent sur des adresses MAC. ARP joue donc un rôle crucial dans la conversion entre ces deux types d'adresses.
- ARP opère uniquement au sein d'un réseau local (LAN) et n'est pas impliqué dans la transmission de paquets à travers des routeurs dans des réseaux étendus (WAN)
# **2) Fonctionnement de ARP**

1. **Détermination de l'Adresse MAC** :
    - Lorsqu'un appareil (par exemple, PC1) veut envoyer un paquet à un autre appareil sur le même réseau local (LAN), il a besoin de connaître l'adresse MAC de destination associée à l'adresse IP de destination.
2. **Requête ARP** :
    - Si l'adresse MAC de destination n'est pas déjà dans sa table ARP, PC1 envoie une requête ARP sur le réseau. Cette requête est une diffusion (broadcast) demandant « Qui a l'adresse IP X, dites-le à Y », où X est l'adresse IP de destination et Y est l'adresse MAC de PC1.
3. **Réponse ARP** :
    - L'appareil sur le réseau qui possède l'adresse IP X répond avec une réponse ARP, indiquant « L'adresse IP X est à l'adresse MAC Z ». Cette réponse est envoyée directement à l'adresse MAC de PC1.
4. **Mise à Jour de la Table ARP** :
    - PC1 met ensuite à jour sa table ARP avec cette nouvelle association entre l'adresse IP et l'adresse MAC, lui permettant d'encapsuler les paquets IP dans des trames Ethernet et de les envoyer sur le réseau local.
## **3) Table ARP**
- **Rôle de la Table ARP** :
    - Les terminaux utilisent la table ARP pour mapper les adresses IP des appareils sur le même réseau local (LAN) à leurs adresses MAC correspondantes.
    - Chaque fois qu'un terminal doit envoyer un paquet à une autre machine sur le LAN, il consulte sa table ARP pour trouver l'adresse MAC correspondant à l'adresse IP de destination.
- **Gestion de la Table ARP** :
    - La table ARP est dynamiquement mise à jour à mesure que l'appareil apprend de nouvelles associations entre les adresses IP et MAC, soit par des réponses ARP, soit par des requêtes ARP qu'il initie.
- **Mise à Jour et Expiration** :
    - Les entrées ARP sont souvent mises à jour et peuvent expirer après un certain temps d'inactivité, nécessitant des requêtes ARP fraîches pour les renouveler.
- **Sécurité de la Table ARP** :
    - La table ARP peut être sujette à certaines attaques de sécurité, comme le ARP spoofing, nécessitant parfois des mesures de sécurité supplémentaires.

## **5) Commandes cisco**
1. **Voir la Table ARP**
```
show arp
show ip arp
```
2. **Vider la Table ARP**
```
clear arp-cache
```
3. **Configurer une Entrée ARP Statique**
```
arp <ip-address> <mac-address> ARPA
```
4. **Configurer le Timeout ARP**
```
arp timeout <seconds>
```
Permet de définir la durée pendant laquelle une entrée ARP reste dans la table ARP avant d'expirer. Par défaut, cette valeur est souvent réglée à 14400 secondes (4 heures) sur les appareils Cisco.

5. **Vérifier les Statistiques ARP**
```
show arp summary
```