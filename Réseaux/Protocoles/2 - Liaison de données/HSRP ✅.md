# Guide HSRP

L'HSRP est un protocole propriétaire Cisco utilisé pour fournir une disponibilité élevée du réseau en permettant à deux ou plusieurs routeurs de fonctionner en tant que groupe de basculement. Si le routeur actif tombe en panne, le routeur de secours prend le relais, garantissant ainsi une transition quasi transparente pour les hôtes du réseau. Voici une version corrigée et étendue de votre leçon sur l'HSRP :

## 1) Principe et fonctionnement

- **HSRP** est un protocole de redondance de passerelle qui permet d'assurer une disponibilité élevée pour le réseau. Il crée une passerelle virtuelle qui est utilisée comme passerelle par défaut pour les hôtes du réseau.
    
- **Répartition de charge** : Bien que l'HSRP fournisse principalement de la redondance, il est également possible de le configurer pour la répartition de charge en utilisant plusieurs groupes HSRP.

# 2) Différentes versions 
### HSRP Version 1:

1. **Plage de groupe** : La version 1 prend en charge des groupes HSRP allant de 0 à 255.
2. **Adresses multicast** : Elle utilise l'adresse multicast 224.0.0.2 pour envoyer les messages HSRP entre les routeurs du même groupe.
3. **Compatibilité** : Étant donné que c'est la première version, elle est largement prise en charge sur de nombreux équipements Cisco.
4. **Limitation** : Elle ne prend pas en charge l'authentification IPv6 ni le tracking IPv6.

### HSRP Version 2:

1. **Plage de groupe** : La version 2 étend la plage de groupes HSRP de 0 à 4095, offrant ainsi une plus grande flexibilité pour les grands réseaux.
2. **Adresses multicast** : Elle utilise l'adresse multicast 224.0.0.102 pour les messages HSRP, évitant ainsi les conflits avec d'autres protocoles qui utilisent l'adresse 224.0.0.2.
3. **Compatibilité** : La version 2 est compatible avec les versions ultérieures de l'IOS Cisco.
4. **Améliorations** :
    - Elle prend en charge l'authentification explicite de la trame HSRP pour une sécurité accrue.
    - Elle introduit un nouveau format de paquet pour une meilleure gestion et distinction des paquets.
    - La version 2 permet l'utilisation d'IPv6.
    - Elle prend en charge trois types d'authentification : texte en clair, MD5 et SHA-256.

### HSRP pour IPv6:

Avec l'avènement d'IPv6, Cisco a introduit la prise en charge d'HSRP pour IPv6, qui est basée sur les améliorations de la version 2.

1. **Adresses multicast** : HSRP pour IPv6 utilise l'adresse multicast FF02::66 pour les messages HSRP.
2. **Compatibilité** : Nécessite des versions d'IOS plus récentes qui prennent en charge IPv6.
3. **Configuration** : La configuration est presque identique à celle d'HSRP pour IPv4, mais elle est appliquée à une interface IPv6.
# 3) Configuration de HSRP
1. Configurer HSRP sur l'interface concerné en mettant l'adresse IP de la passerelle virtuelle
```
R1(config)#interface G0/1 
R1(config-if)#standby [group-number] ip [virtual-ip]
```
2. Spécifier la version du protocole
```
R1(config-if)#standby version [1|2]
```
3. Désigner le route actif 
* La valeur par défaut est 100. Une valeur plus élevée donne la priorité à ce routeur.
```
R1(config-if)#standby [group-number] priority [value]
```
4. Déterminer routeur relais en cas de panne
```
R1(config-if)#standby [group-number] preempt
```