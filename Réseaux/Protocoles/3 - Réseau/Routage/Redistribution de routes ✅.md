# Guide Redistribution de routes 
# 1) Introduction
* Dans les grands réseaux, il est fréquent de trouver plusieurs protocoles de routage fonctionnant simultanément. 
* La redistribution des routes est le processus de partage d'informations de routage entre ces différents protocoles. 
* Pour garantir une communication fluide, il est essentiel que ces protocoles puissent échanger des informations sur les routes qu'ils connaissent.
# 2)Principe de la redistribution
* La redistribution des routes permet à un routeur exécutant plusieurs protocoles de routage de partager des informations entre ces protocoles. 
* Si un routeur connaît une route grâce au protocole RIP, il peut la "redistribuer" pour la rendre accessible à un autre protocole, comme OSPF ou EIGRP.

![redistribute.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/redistribute.png)
# 3) Pourquoi redistribuer des routes ?
- **Interconnexion de réseaux** : Si deux réseaux d'entreprises fusionnent et utilisent des protocoles de routage différents, la redistribution est nécessaire pour assurer la connectivité.
- **Migration** : Si une organisation souhaite passer d'un protocole de routage à un autre, elle peut le faire progressivement en redistribuant les routes pendant la transition.
- **Optimisation** : Dans certains scénarios, un protocole peut être plus efficace ou approprié pour une partie du réseau, tandis qu'un autre protocole est préféré pour une autre partie. La redistribution garantit une connectivité transparente.
# 4) Comment ça marche ?
* Lorsqu'un protocole de routage apprend une route, cette route est ajoutée à la table de routage. 
* Lorsque la redistribution est configurée, le routeur prendra cette route et la partagera avec le(s) autre(s) protocole(s) selon les règles définies par l'administrateur réseau.
# 5) Exemple de configuration
- **Redistribuer les routes apprises par RIP dans OSPF** :
```
router ospf 1     
	redistribute rip subnets
```    
- **Redistribuer les routes apprises par OSPF dans RIP** :
```
router rip    
	redistribute ospf 1 metric 1`
```    
- **Redistribuer les routes apprises par OSPF dans EIGRP** :
```
router eigrp 1     
	redistribute ospf 1 metric 1`
```    
- **Redistribution statique/défaut** :
```
router ...     
	redistribute static
```

## **5. Points à considérer lors de la redistribution :**
- **Boucles de routage** : La redistribution peut potentiellement introduire des boucles. Il est donc essentiel de comprendre les mécanismes de prévention des boucles de chaque protocole et de configurer correctement les filtres.
- **Métriques** : Chaque protocole de routage a sa propre façon de calculer la métrique (distance) d'une route. Lors de la redistribution, il est souvent nécessaire de définir comment les métriques doivent être traduites entre les protocoles.
- **Sélection de routes** : Vous ne devez pas nécessairement redistribuer toutes les routes. Il est souvent judicieux de filtrer les routes que vous redistribuez pour éviter la surcharge de la table de routage.