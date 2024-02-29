# Guide sur le Routage Statique

# I) Principe et explication
* Le routage statique est l'une des méthodes les plus élémentaires pour guider le trafic à travers un réseau. 
* Idéal pour les réseaux de petite taille ou dans des situations où la topologie du réseau ne change pas fréquemment
* Se repose sur des configurations manuelles plutôt que sur des protocoles automatisés.
# 2) Routage statique :
* Dans un routage statique, les routes vers les réseaux ou sous-réseaux sont définies manuellement. 
* Cette configuration, une fois mise en place, ne change pas sauf si l'administrateur la modifie. 
* On peut lire comme ceci : Pour atteindre le réseau X il faut envoyer le paquet au saut suivant
* Si aucunes routes statique ne correspond au réseau de destination, alors la route par défaut prendra le relais si elle est configuré, sinon le paquet sera drop.

![STATIC_ROUTE1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/STATIC_ROUTE1.png)
# 3) Route par défaut :
* La route par défaut `0.0.0.0/0` est une instruction spéciale qui indique au routeur comment gérer un paquet destiné à une adresse pour laquelle il n'a pas de route spécifique. 
* On peut voir ca comme une sortie de secours si aucunes route statique a été configurée : "si vous ne savez pas où aller, allez par là".

![STATIC_ROUTE2.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/STATIC_ROUTE2.png)
# 4) Règles essentielles du routage statique
Le routage statique, malgré sa simplicité, nécessite le respect de certaines règles essentielles pour fonctionner correctement :

1. **Connaissance mutuelle** : La passerelle (ou routeur) de votre machine source doit connaître la route pour atteindre le réseau de destination. De la même manière, la passerelle (ou routeur) de la machine de destination doit avoir une route de retour vers le réseau de la machine source. Ceci est crucial pour assurer un échange bidirectionnel d'informations.
    
2. **Mise à jour manuelle** : Contrairement aux protocoles de routage dynamique qui s'ajustent automatiquement aux changements de réseau, le routage statique nécessite une intervention manuelle pour chaque modification. Si un chemin devient indisponible, il ne sera pas réparé tant que l'administrateur réseau n'aura pas apporté de modifications.
    
3. **Simplicité vs Scalabilité** : Pour les petits réseaux, le routage statique peut être simple et direct. Cependant, à mesure que le réseau grandit, la gestion des routes statiques devient plus complexe et peut être difficile à gérer.

# 5) Avantages et inconvénients

## Avantages :
- **Prévisibilité** : Comme les routes sont définies manuellement, il n'y a pas de surprises concernant la manière dont les paquets seront routés.
- **Pas de surcharge du protocole** : Contrairement aux protocoles de routage dynamique, il n'y a pas de trafic supplémentaire généré par l'échange d'informations sur les routes.
## Inconvénients :
- **Manque de résilience** : Si un lien échoue, le routeur ne peut pas rediriger le trafic à moins que l'administrateur n'intervienne.
- **Gestion difficile à grande échelle** : Dans de grands réseaux, le maintien de routes statiques peut être une tâche ardue.

# 6) Configuration routage statique

- Ajouter une route statique
```shell
R1(config)#ip route [NET_DESTI] [MASQUE] [NEXT_HOP]
R1(config)#ipv6 route [NET_DESTI]/[MASQUE] [NEXT_HOP]
```
- Ajouter une host static route
```shell
R1(config)#ip route [IP_HOST] 255.255.255.255 [NEXT_HOP]
R1(config)#ipv6 route [IP_HOST]/128 [NEXT_HOP]
```
- Afficher table de routage (les routes)
```shell
R1#sh ip route
R1#sh ipv6 route
```
- Ajouter une route statique par défaut
```shell
R1(config)#ip route 0.0.0.0 0.0.0.0 [NEXT_HOP]
R1(config)#ipv6 route ::/0 [NEXT_HOP]
```
