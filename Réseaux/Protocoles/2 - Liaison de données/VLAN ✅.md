# Guide VLAN

## I) Principe et explication

- Les VLAN (Virtual Local Area Network) permettent de segmenter un réseau physique en plusieurs sous-réseaux logiques. Chaque VLAN est identifié par un identifiant unique, souvent appelé **VID** (VLAN ID). Cette segmentation offre plusieurs avantages tels que l'amélioration de la performance du réseau, l'augmentation de la sécurité, et la simplification de l'administration du réseau.
    
- L'idée principale est de regrouper des équipements réseau en fonction de critères logiques (par exemple, par département dans une entreprise) plutôt que physiques.
    

❗ **Mise en place d'un VLAN** :
1. _**Créer le VLAN**_ : Chaque VLAN doit avoir un identifiant unique (VID) et, optionnellement, un nom pour faciliter son identification.
2. _**Attribuer des ports/interfaces**_ à un VLAN : Chaque port d'un switch peut être assigné à un VLAN spécifique.

❗ **Rôles des ports sur un switch en relation avec les VLANs** :
1. _**Port d'accès**_ : Il s'agit d'un port destiné à la connexion d'un périphérique terminal (comme un ordinateur, une imprimante ou un serveur). Ce port appartient à un seul VLAN et ne marque pas les trames avec un identifiant de VLAN lorsqu'elles quittent le switch.
2. _**Port Trunk (ou de liaison)**_ : Ce port est conçu pour transporter les trames de plusieurs VLANs simultanément, généralement entre switches. Les trames transitant par un port trunk sont étiquetées avec un identifiant de VLAN, sauf si elles appartiennent au VLAN natif. Cela permet à l'équipement récepteur de savoir à quel VLAN appartient chaque trame.

## II) Protocoles associés

### **IEEE 802.1Q**_ 
* C'est la norme standard utilisée pour le marquage des trames VLAN sur un réseau Ethernet. Elle définit comment insérer un "tag" VLAN dans une trame Ethernet pour indiquer l'appartenance à un VLAN.
#### **Intérêt de 802.1Q**

1. **Inter-opérabilité** : 802.1Q est une norme ouverte, contrairement à certains protocoles de marquage VLAN qui sont propriétaires. Cela signifie que les équipements de différents fabricants peuvent travailler ensemble sans problème lorsqu'ils utilisent 802.1Q.
    
2. **Segmentation de réseau** : Avec 802.1Q, un réseau peut être divisé en plusieurs VLANs. Cela isole le trafic, améliorant la performance et la sécurité.
    
3. **Utilisation efficace des liens** : En utilisant un seul lien (trunk) pour transporter le trafic de plusieurs VLANs, il n'est pas nécessaire d'avoir des liens séparés pour chaque VLAN, économisant ainsi des ressources.
#### **Fonctionnement de 802.1Q**
1. **Marquage de trame** : Lorsqu'une trame doit être transportée sur un lien trunk, une balise 802.1Q est insérée dans la trame originale. Cette balise contient un identifiant VLAN (VLAN ID) qui indique à quel VLAN la trame appartient.
    
2. **ID VLAN** : L'identifiant VLAN est un nombre à 12 bits, ce qui signifie qu'il peut y avoir jusqu'à 4096 VLANs différents sur un réseau utilisant 802.1Q.
    
3. **Trame native** : Sur un lien trunk 802.1Q, une trame d'un certain VLAN (souvent le VLAN 1 par défaut) peut être configurée pour ne pas être marquée. Ce VLAN est connu sous le nom de VLAN natif. Cela peut être utile pour la compatibilité avec des équipements qui ne comprennent pas les balises 802.1Q.
    
4. **Isolation** : Les trames appartenant à un VLAN donné sont isolées des autres VLANs. Cela signifie qu'elles ne peuvent pas "parler" directement à des trames d'un autre VLAN sans passer par un dispositif de couche 3, comme un routeur ou une passerelle.

#### **Sécurité**
1. **Limitations** : Bien que 802.1Q fournisse une isolation au niveau de la couche 2, il ne s'agit pas d'un mécanisme de sécurité complet. Des attaques comme le VLAN hopping peuvent exploiter les configurations VLAN mal sécurisées.
    
2. **Pratiques recommandées** : Il est généralement conseillé de désactiver le VLAN natif ou de le changer à un VLAN inutilisé. Évitez également d'utiliser le VLAN 1 pour le trafic normal.
#### **Conclusion**

802.1Q est un outil essentiel pour la gestion moderne des réseaux, permettant une segmentation flexible et une utilisation efficace des ressources. Cependant, comme avec tous les outils de réseau, il doit être utilisé correctement pour garantir sécurité et performance.
### **DTP (Dynamic Trunking Protocol)**
* Protocole propriétaire de Cisco qui permet de négocier dynamiquement le mode trunk entre deux switches Cisco.
* Lorsque deux équipements Cisco compatibles avec le protocole DTP sont connectés, DTP tente de négocier automatiquement si le lien entre eux doit être configuré en mode trunk ou access.
* Par défaut, beaucoup de commutateurs Cisco ont leurs ports configurés en mode dynamique auto, ce qui signifie qu'ils essaieront de se mettre en mode trunk si l'autre extrémité est en mode trunk ou en mode dynamique désirable. Si aucune des conditions n'est remplie, ils reviendront en mode access.
* Le mode "nonegotiate" sert à fixer la configuration d'un port de commutateur en mode trunk ou en mode access, en empêchant toute négociation automatique avec d'autres équipements par le protocole DTP (Dynamic Trunking Protocol)
#### **Intérêt de DTP**
1. **Configuration Automatique**: Sans DTP, si un administrateur souhaite établir une liaison trunk entre deux switches, il doit configurer manuellement chaque côté du lien. DTP automatise ce processus en permettant aux switches de négocier dynamiquement le statut de trunk.
2. **Flexibilité**: Avec DTP, les administrateurs réseau n'ont pas besoin de changer manuellement le mode de fonctionnement de chaque port chaque fois qu'ils veulent changer la nature de la connexion (trunk ou access). Si les exigences changent, DTP peut s'adapter sans intervention manuelle.
3. **Réduction des erreurs**: La configuration manuelle des ports peut conduire à des erreurs, surtout dans de grands réseaux. DTP réduit ce risque en automatisant la négociation.
#### **Fonctionnement de DTP**
1. **Modes de Fonctionnement**: DTP opère en plusieurs modes, dont :
    - **Trunk**: Le port essaie activement de convertir le lien en trunk.
    - **Access**: Le port est configuré pour rester non-trunk, c'est-à-dire en mode d'accès.
    - **Dynamic Auto**: Le port est prêt à devenir un trunk si le port voisin est configuré en mode Trunk ou Dynamic Desirable.
    - **Dynamic Desirable**: Le port essaie activement de convertir le lien en trunk avec des ports en mode Dynamic Desirable, Dynamic Auto ou Trunk.
    - **Nonegotiate**: Le port ne participe pas à la négociation DTP et doit être configuré manuellement.
2. **Négociation**: Lorsque deux ports de switch sont connectés, ils envoient des paquets DTP pour comprendre le mode de fonctionnement du port voisin. Selon les modes des deux ports, une décision est prise quant à savoir si le lien doit être trunk ou non.
3. **Encapsulation**: Si un trunk est établi, DTP peut également négocier le type d'encapsulation VLAN à utiliser (ISL ou 802.1Q, bien que ISL soit devenu obsolète).
4. **Sécurité**: Il est crucial de comprendre que, même si DTP est pratique, il peut présenter des risques pour la sécurité. Un attaquant pourrait potentiellement exploiter DTP pour configurer un port en mode trunk et obtenir l'accès à tous les VLANs transitant par ce port. Pour cette raison, de nombreux administrateurs choisissent de désactiver DTP sur les ports où ils n'ont pas besoin de cette automatisation.
#### Conclusion

DTP est un outil précieux pour simplifier la configuration des liens trunk sur les réseaux Cisco. Cependant, comme pour tout outil automatique, il est essentiel de comprendre ses avantages et ses limites, et de l'utiliser judicieusement pour garantir la sécurité et la performance du réseau.

## III) Avantages des VLANs

1. _**Sécurité améliorée**_ : La segmentation réduit la portée des broadcasts et limite ainsi les attaques basées sur le broadcast.
2. _**Amélioration des performances**_ : En réduisant la taille des domaines de diffusion, on limite le trafic inutile sur le réseau.
3. _**Flexibilité et évolutivité**_ : Les utilisateurs peuvent être ajoutés ou déplacés sans nécessiter de modifications physiques du réseau.
4. _**Simplification de l'administration**_ : Les changements, ajouts ou suppressions de VLANs peuvent souvent être réalisés via une interface centralisée.

## IV) Considérations importantes

1. _**Routage entre VLANs/ Routage on stick**_ : Par défaut, les VLANs sont isolés les uns des autres. Pour permettre la communication entre différents VLANs, un routeur ou une fonction de routage sur un switch multicouche est nécessaire.
2. _**Prudence lors de la configuration**_ : Une mauvaise configuration des VLANs peut entraîner des boucles dans le réseau ou isoler accidentellement des utilisateurs.
## V) Routage entre VLANs

Bien que les VLANs soient conçus pour isoler le trafic, il peut être nécessaire de permettre une communication contrôlée entre eux. Voici pourquoi :

1. **Besoin fonctionnel** : Accès des utilisateurs à des ressources situées dans d'autres VLANs.
2. **Optimisation du réseau** : Communication contrôlée entre segments.
3. **Gestion des services** : Accès centralisé à des services comme DHCP ou DNS.
4. **Politiques de sécurité** : Contrôle précis des échanges via des ACLs.
5. **Economie et simplicité** : Moins de routeurs physiques nécessaires.
6. **Flexibilité** : Adaptation à des besoins évolutifs.
* Exemple : Des utilisateurs dans un VLAN "Comptabilité" pourraient avoir besoin d'accéder à un serveur situé dans un VLAN "Data Center".

❗ **Important** : Toute communication inter-VLAN nécessite une réflexion sur la sécurité et un contrôle rigoureux pour éviter les risques.

# VI ) Configuration router-on-stick (inter-VLAN)
* Router-on-stick est une méthode de routage inter-VLAN utilisant un seul lien physique. Elle est appelée ainsi car le routeur n'a qu'une seule interface physique pour gérer plusieurs VLANs, un peu comme un "bâton" avec plusieurs "branches".
### Configuration sur le switch

1. **Création du VLAN** :
```
SW(config)#vlan @numero
SW(config-vlan)#name @nom
```
2. **Affectation du VLAN aux interfaces** (en mode access) :
```
SW(config)#interface range fastEthernet 0/0-5
SW(config-if)#switchport mode access
SW(config-if)#switchport access vlan @num
```
3. **Configuration d'une interface en mode Trunk** :
```
SW(config)#interface @interface  
SW(config-if)#switchport mode trunk 
SW(config-if)#switchport trunk native vlan @vlan_id   # Choisir un VLAN natif différent du VLAN 1 pour des raisons de sécurité 
SW(config-if)#switchport trunk allowed vlan XX,XX,XX  # Indiquer la liste des VLAN autorisés sur la liaison trunk.`
```
4. **Configuration de l'interface du switch connectée au routeur** :
```
SW(config)#int @interface
SW(config-if)#switchport mode trunk 
SW(config-if)#switchport trunk allowed vlan XX,XX,XX
```
5. **Définir la passerelle par défaut sur le switch** (pour renvoyer le paquet vers le routeur pour le routage inter-VLAN) :
```
SW(config)#ip default-gateway X.X.X.X
```
### Configuration sur le routeur
1. **Création d'une sous-interface pour chaque VLAN** :
```
R(config)#int G0/1.@num_vlan 
R(config-if)#encapsulation dot1q @num_vlan    # Définir l'encapsulation (doit correspondre au VLAN) 
R(config-if)#ip add @ip_gw_vlanX @masque      # Définir l'adresse IP de la passerelle pour le VLAN. L'adresse doit être dans le même sous-réseau que les dispositifs du VLAN.`
```

**Conseils** :
- Assurez-vous que les ports sur les deux extrémités du lien (routeur et switch) sont bien configurés pour le trunking.
- Utilisez le commandement `show interfaces trunk` sur le switch pour vérifier que le trunking est correctement configuré et fonctionnel.
- Utilisez le commandement `show vlan` pour s'assurer que les ports sont bien assignés aux bons VLANs.
- Testez la connectivité entre les VLANs après configuration pour s'assurer que le routage inter-VLAN fonctionne correctement.

## VII) Distinction entre switch SW2 et switch MLS (comme SW3) avec SVI**

1. **Switch SW2 (Switch de couche 2)**:
    - Opère principalement dans la couche de liaison de données du modèle OSI (couche 2).
    - Peut créer et gérer des VLANs.
    - N'offre pas de fonctionnalités de routage IP.
    - Ne peut pas avoir d'interfaces VLAN SVI avec des adresses IP.
    - Requiert un routeur séparé pour le routage inter-VLAN.

2. **Switch MLS (Switch multicouche)**:
    - Opère à la fois dans la couche de liaison de données et la couche réseau du modèle OSI (couches 2 et 3).
    - Peut créer et gérer des VLANs.
    - Offre des fonctionnalités de routage IP intégrées, y compris le routage inter-VLAN.
    - Peut avoir des interfaces VLAN SVI avec des adresses IP qui agissent comme des passerelles par défaut pour les hôtes dans chaque VLAN.
    - N'a pas besoin d'un routeur externe pour le routage inter-VLAN (mais peut travailler avec des routeurs pour des topologies plus complexes).

# VIII) Configuration Switch MLS (Switch Multi-Couche)
## Étape 1: Création des VLANs
```
MLS(config)#vlan 10     
	name N1 
MLS(config)#vlan 20     
	name N2
```
## Étape 2: Création des interfaces VLAN SVI
* Ces interfaces représentent des interfaces virtuelles qui offrent une interface de routage pour chaque VLAN.
```
MLS(config)#interface vlan 10     
	description Default Gateway SVI for Network 1     
	ip add X.X.X.X @masque     
	no shut 
MLS(config)#interface vlan 20     
	description Default Gateway SVI for Network 2     
	ip add X.X.X.X @masque     
	no shut
```
## Étape 3: Configuration des ports d'accès

```
MLS(config)#int G0/0     
	switchport mode access     
	switchport access vlan 10 
MLS(config)#int G0/1     
	switchport mode access     
	switchport access vlan 20
```
## Étape 4: Active le routage entre les VLANs
```
MLS(config)#ip routing
```
## Étape 5 (cas particulier): Configuration d'un port routé, pour la connexion à un autre routeur
* Définir les routes nécessaires (si nécessaire) pour assurer une communication appropriée avec d'autres réseaux ou routeurs.
```
MLS(config)#int G0/2     
	no switchport     
	ip address X.X.X.X @masque     
	no shut
```
