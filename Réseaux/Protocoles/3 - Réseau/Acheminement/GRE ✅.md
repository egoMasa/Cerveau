
# 1) Principes de base de GRE
## Encapsulation des paquets
* Certains protocoles réseau de couches 3 (protocole LAN,IGP) ne sont pas pris en charge par les réseaux intermédiaires
* GRE permet d'encapsuler ces paquets de couches 3 non supportés sur le réseau publique comme OSPF dans un paquet GRE qui lui sera pris en charge
* Comparaison : C'est comme un convoi qui prend en charge les paquets non autorisé à transiter sur le réseau publique et qui autorise leur transit vers une autre zone qui pourra les prendre en charge
* De ce fait on peut transmettre des paquets entre 2 réseaux LAN au travers d'un tunnel GRE reliant les deux points d'accès
## Structure d'en tête GRE
1. **Flags et Version** : Ces champs sont généralement définis à zéro, car les versions actuelles de GRE n'utilisent pas ces options.
    
2. **Type de Protocole** : Indique le type de paquet encapsulé (par exemple, IPv4, IPv6, OSPF).
    
3. **Clés GRE (Optionnel)** : Peuvent être utilisées pour identifier uniques les tunnels GRE ou pour d'autres fonctions spécifiques.
    
4. **Sequence Number (Optionnel)** : Utilisé pour maintenir l'ordre des paquets à l'intérieur du tunnel GRE.
## Fonctionnement de GRE 
1. **Création de Tunnels Point-à-Point** : GRE établit des tunnels point-à-point entre les routeurs source et destination, permettant la transmission de données sur des réseaux qui ne prennent pas en charge directement ces données.
    
2. **Transparence des Protocoles de Routage** : Le GRE permet le passage transparent de divers protocoles de routage à travers un réseau intermédiaire. Par exemple, les paquets OSPF ou BGP peuvent être transmis à travers un réseau IPv4.
    
3. **Prestations sur Réseaux Non-Sécurisés** : Bien que GRE ne fournisse pas de chiffrement, il peut être combiné avec IPsec pour sécuriser les données transmises à travers des réseaux publics.
    
4. **Flexibilité et Compatibilité** : Le GRE peut transporter une variété de types de trafic, ce qui le rend compatible avec de nombreux scénarios réseau différents.

# 2) Configuration d'un tunnel GRE

### Configuration du Tunnel GRE sur le Routeur 1

1. **Créer l'interface du tunnel GRE** :
```plaintext
Router1(config)# interface Tunnel [NUMÉRO_TUNNEL]
Router1(config-if)# ip address [ADRESSE_IP_TUNNEL_1] [MASQUE]
Router1(config-if)# tunnel destination [ADRESSE_IP_ROUTEUR_2]
Router1(config-if)# tunnel source [INTERFACE_EXTERNE] ou [ADRESSE_IP_SOURCE]
```

2. **Enregistrer la configuration** :
```plaintext
Router1(config-if)# end
Router1# write memory
```
### Commandes de Vérification

1. **Vérifier l'état du tunnel** :
```plaintext
Router# show interface Tunnel [NUMÉRO_TUNNEL]
```

2. **Vérifier la connectivité** :
```plaintext
Router# ping [ADRESSE_IP_TUNNEL_AUTRE_ROUTEUR]
```

3. **Afficher les détails du tunnel** :
```plaintext
Router# show ip interface Tunnel [NUMÉRO_TUNNEL]
```

# 3) Configuration avec IPsec 

### Étape 1 : Configuration de la Phase 1 (ISAKMP)

#### Sur les deux routeurs :

1. **Configurer la politique ISAKMP** :
```plaintext
Router(config)# crypto isakmp policy 10
Router(config-isakmp)# encryption aes
Router(config-isakmp)# hash sha
Router(config-isakmp)# authentication pre-share
Router(config-isakmp)# group 2
Router(config-isakmp)# lifetime 3600
Router(config-isakmp)# exit
```

2. **Définir une clé prépartagée ISAKMP** :
```plaintext
Router(config)# crypto isakmp key [MOT_DE_PASSE] address [ADRESSE_IP_AUTRE_ROUTEUR]
```

### Étape 2 : Configuration de la Phase 2 (IPsec)

1. **Créer un IPsec transform-set** :
```plaintext
Router(config)# crypto ipsec transform-set MYSET esp-aes esp-sha-hmac 
Router(cfg-crypto-trans)# exit
```

2. **Créer une ACL pour spécifier le trafic GRE** :
```plaintext
Router(config)# access-list 100 permit gre host [ADRESSE_IP_SOURCE_TUNNEL] host [ADRESSE_IP_DESTINATION_TUNNEL]
```

### Étape 3 : Créer et Appliquer une Crypto Map

1. **Créer une crypto map et associer la transform-set** :
```plaintext
Router(config)# crypto map MYMAP 10 ipsec-isakmp
Router(config-crypto-map)# set peer [ADRESSE_IP_AUTRE_ROUTEUR]
Router(config-crypto-map)# set transform-set MYSET
Router(config-crypto-map)# match address 100
Router(config-crypto-map)# exit
```

2. **Appliquer la crypto map à l'interface externe** :
```plaintext
Router(config)# interface [INTERFACE_EXTERNE]
Router(config-if)# crypto map MYMAP
Router(config-if)# exit
```

### Étape 4 : Vérification

1. **Vérifier les SAs ISAKMP** :
```plaintext
Router# show crypto isakmp sa
```

2. **Vérifier les SAs IPsec** :
```plaintext
Router# show crypto ipsec sa
```

Assurez-vous de remplacer `[MOT_DE_PASSE]`, `[ADRESSE_IP_AUTRE_ROUTEUR]`, `[ADRESSE_IP_SOURCE_TUNNEL]`, `[ADRESSE_IP_DESTINATION_TUNNEL]`, et `[INTERFACE_EXTERNE]` par les valeurs réelles correspondant à votre réseau. Cette configuration ajoute un chiffrement IPsec au tunnel GRE, ce qui améliore considérablement la sécurité des données transitant à travers le tunnel.