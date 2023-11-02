# Guide VLSM et calcul réseau 

# Sommaire 
- [ ] Trouver la première et dernière adresse utilisable d'un réseau
- [ ] Trouver le nombre d'adresses disponibles dans un réseau/sous-réseau
- [ ] Trouver le nombre de sous réseaux possible selon une plage

# 1) Trouver la première et dernière adresse utilisable d'un réseau
## Cas simple : 10.0.0.0/24
* Plage d'adresse : 10.0.0.0/24
* Signification : Les 24 premiers bits réservés au réseau valent 1
```
10.0.0.0/24
1111 1111 1111 1111 1111 1111 | 0000 0000
```
* Calculer la première IP utilisable
* On laisse les bits restant (partie hôte) à zéro : 10.0.0.1 car 2^0 = 1
```
11111111 11111111 11111111 | 00000000
```
* Calculer la dernière IP utilisable
* On passent tout les bits de la partie hôte à 1 et on additionne les puissance partie hôte
```
10.0.0.254/24
11111111 11111111 11111111 | 11111111
```
## Cas plus dur : 10.0.0.0/28
* Signification : Les 28 premiers bits réservés au réseau valent 1
```
10.0.0.0/28
11111111 11111111 11111111 1111|0000
```
* Calculer la première IP utilisable : 10.0.0.1/28
```
10.0.0.0/28
11111111 11111111 11111111 1111|0000
```
* Calculer la dernière IP utilisable
* On passent tout les bits de la partie hôte à 1 et on additionne les puissance partie hôte
```
10.0.0.14/28
11111111 11111111 11111111 1111|1111
1+2+4+8 = 14
```
# 2) Trouver le nombre d'adresses disponibles dans un réseau/sous-réseau

# 3) Trouver le nombre de sous réseaux possible selon une plage
