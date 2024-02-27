# Guide VLSM et calcul réseau 

# Sommaire 
- [ ] Trouver la première et dernière adresse utilisable d'un réseau
- [ ] Déterminer combien d'adresses IP uniques peuvent être attribuées aux hôtes dans un réseau ou un sous-réseau donné
- [ ] Déterminer combien de sous-réseaux logiques distincts peuvent être créés à partir d'une plage d'adresses IP
- [ ] Faire le résumé de routes entre plusieurs réseaux 

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
# 2) Déterminer combien d'adresses IP uniques peuvent être attribuées aux hôtes dans un réseau ou un sous-réseau donné
* Une adresse IPV4 est sur 32
* On prend la valeur du masque réseau de la plage : N
* On soustrait pour obtenir le nombre de bits disponibles pour les hôtes : X = 32-N
* On calcul le nombre d'adresses disponibles : 2^X

# 3) Trouver le nombre de sous réseaux possible selon une plage
* On prend la valeur du masque réseau de la plage : N
* On soustrait pour obtenir le nombre de bits disponibles pour les sous-réseaux : Y = 32-N
* On calcule le nombre de sous-réseaux possibles : 2^Y

# 4) Faire le résumé de routes entre plusieurs réseaux 
* Réseau 1 : 192.168.1.0/26
* Réseau 2 :192.168.1.64/26
* Réseau 3 :192.168.1.128/26
1. Traduire les adresses IP en binaire
```
192.168.1.0   -> 11000000.10101000.00000001.00000000
192.168.1.64  -> 11000000.10101000.00000001.01000000
192.168.1.128 -> 11000000.10101000.00000001.10000000
```
2. Définir le nombre de bits en commun
```
11000000.10101000.00000001.|00|000000
11000000.10101000.00000001.|01|000000
11000000.10101000.00000001.|10|000000
```
3. Définir la route résumée finale
* Adresse binaire : `11000000.10101000.00000001.xx000000`
* Adresse IP : `192.168.1.0/24`
* Le résumé de route pour ces trois réseaux est donc 192.168.1.0/24
