# Guide sur le routage linux

**1. Afficher la table de routage actuelle:**
```bash
route -n
ip route
```
Cette commande affiche la table de routage du système. `-n` signifie "numérique" et indique à la commande d'afficher les adresses sous forme numérique (c'est-à-dire IP) plutôt que d'essayer de les résoudre en noms.

2. Configuration de la table de routage 

```bash
ip route add [IP_NETWORK_DESTI/SUBNET] via [IP_GATEWAY]
```
