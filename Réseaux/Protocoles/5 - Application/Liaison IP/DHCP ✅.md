DHCP, pour "Dynamic Host Configuration Protocol", est un protocole de gestion de réseau qui facilite l'attribution d'adresses IP et d'autres détails de configuration réseau aux dispositifs dans un réseau. Il attribue automatiquement des adresses IP aux appareils en fonction de leurs adresses MAC lorsqu'ils se connectent au réseau. Cette approche dynamique de l'allocation d'adresses IP élimine le suivi et la configuration manuels, facilitant ainsi la gestion des réseaux par les administrateurs.

## **Caractéristiques clés :**

1. **Attribution automatique d'adresses IP :** DHCP utilise une plage d'adresses IP, communément appelée "pool" ou "scope", pour attribuer automatiquement des adresses IP aux dispositifs du réseau. Ceci permet d'éviter les conflits d'adresses IP et assure une utilisation efficace des adresses IP disponibles.
2. **Gestion des baux :** DHCP propose une attribution temporaire d'adresses IP, appelées "baux". Ces baux ont une durée d'expiration, après laquelle les adresses IP sont restituées au pool pour être réattribuées à d'autres dispositifs.
3. **Configuration centralisée :** DHCP fournit également un mécanisme de gestion centralisée des paramètres du réseau, tels que les serveurs DNS, les passerelles par défaut et les masques de sous-réseau. Ceci contribue à maintenir une configuration réseau cohérente et réduit le potentiel d'erreurs.

## **Avantages :**

1. **Réduction de l'effort administratif :** DHCP minimise le temps et l'effort nécessaires pour gérer les attributions d'adresses IP dans un réseau, car il attribue et récupère automatiquement les adresses IP en fonction de la gestion des baux.
2. **Scalabilité :** DHCP est utile pour les réseaux, petits et grands. Il permet une intégration facile et la suppression de nouveaux dispositifs, sans attributions manuelles d'adresses IP.
3. **Cohérence :** DHCP permet une gestion cohérente des paramètres réseau, ce qui aide à réduire les erreurs et garantit que les dispositifs du réseau peuvent accéder aux ressources nécessaires.

## **Ports utilisés :** 
Le protocole DHCP utilise deux ports UDP pour communiquer. Le port 67 est utilisé par le serveur DHCP pour écouter les requêtes des clients, et le port 68 est utilisé par les clients pour écouter les réponses du serveur.

## **Méthodes d'attribution :**

1. **Statique :** Dans ce mode, une machine dispose toujours de la même adresse IP fixe, ce qui est défini manuellement par l'administrateur réseau.
2. **Dynamique :** Dans ce mode, une machine reçoit une adresse IP disponible et non fixe du pool d'adresses DHCP pour une durée déterminée.
3. **Adresse APIPA (Automatic Private IP Addressing) :** Si un client ne parvient pas à obtenir une adresse IP du serveur DHCP, le système d'exploitation peut attribuer automatiquement une adresse IP dans la plage 169.254.0.0 à 169.254.255.255.

## **Fonctionnement du DHCP :** 
Quand un dispositif se connecte à un réseau, le processus DHCP suit généralement ces étapes:

1. **Découverte (DHCP Discover) :** L'appareil envoie une requête DHCP Discover pour rechercher un serveur DHCP.
2. **Offre (DHCP Offer) :** Le serveur DHCP répond avec une offre DHCP contenant une adresse IP disponible.
3. **Demande (DHCP Request) :** L'appareil demande officiellement l'adresse IP proposée.
4. **Accusé (DHCP Ack) :** Le serveur DHCP confirme l'attribution de l'adresse IP à l'appareil.

## **Sécurité et considérations :** 
Tout en étant extrêmement utile, le DHCP peut être exploité s'il n'est pas sécurisé. Les attaques DHCP, comme les serveurs DHCP voyous qui fournissent des informations incorrectes, peuvent être dévastatrices pour un réseau. Il est donc essentiel d'assurer une gestion sécurisée et de mettre en place des mesures pour détecter et prévenir de telles menaces.

## Configuration 

### Étape 1 : Définir le pool d'adresses DHCP

Un "pool" est une plage d'adresses IP que le serveur DHCP attribuera aux clients. Pour définir un pool :
```
Router(config)# ip dhcp pool [NOM_DU_POOL]
```
### Étape 2 : Configurer la plage d'adresses IP à distribuer

Pour définir la plage d'adresses IP que le serveur distribuera aux clients :
```
Router(dhcp-config)# network [ADRESSE_RESEAU] [MASQUE]
```

### Étape 3 : Configurer la passerelle par défaut (Gateway)
```
Router(dhcp-config)# default-router [ADRESSE_GATEWAY]
```

### Étape 4 : Configurer le serveur DNS (si nécessaire)
```
Router(dhcp-config)# dns-server [ADRESSE_DNS]
```
### Étape 5 : Définir la durée du bail

La durée du bail est la période pendant laquelle une adresse IP attribuée à un client reste valide. Une fois cette période écoulée, l'adresse est retournée au pool pour être réattribuée.
```
Router(dhcp-config)# lease [JOURS] [HEURES] [MINUTES]
```
Par exemple, pour un bail de 1 jour, 12 heures et 30 minutes :
```
Router(dhcp-config)# lease 1 12 30
```

### Étape 7 : Exclure des adresses IP

Il est courant d'exclure certaines adresses IP du pool DHCP pour éviter des conflits avec des équipements ayant des adresses IP fixes.
```
Router(config)# ip dhcp excluded-address [DEBUT_PLAGE] [FIN_PLAGE]
```
Par exemple, pour exclure les adresses de `192.168.1.1` à `192.168.1.9` :
```
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.9
```

### Étape 8 : Enregistrer la configuration et quitter
Après avoir configuré tous les paramètres nécessaires, enregistrez la configuration et quittez le mode de configuration.
```
Router(config)# end
Router# write memory
```

## **Conclusion :** 
En résumé, le DHCP simplifie la gestion des adresses IP et la configuration du réseau pour les administrateurs réseau, garantissant une utilisation efficace des adresses IP et rationalisant l'administration du réseau. Ceci est particulièrement précieux dans les grands réseaux comprenant de nombreux dispositifs ou lorsque les dispositifs doivent fréquemment se connecter ou se déconnecter du réseau.