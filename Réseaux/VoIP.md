# Sommaire 
- [ ] VoIP et ToIP 
- [ ] Configuration cisco VoIP
## Switch 
1. Créer VLAN voix pour les téléphones et créer VLAN data pour les PCs
```
vlan [ID_VLAN_VOIX]
   name VOIX
vlan [ID_VLAN_DATA]
   name DATA
```
- `[ID_VLAN_VOIX]`: Numéro d'identification du VLAN pour la voix (e.g., 100).
- `[ID_VLAN_DATA]`: Numéro d'identification du VLAN pour les données (e.g., 200).
2. Mettre le port vers le routeur en mode trunk avec vlan native choisie 
```
interface [INTERFACE_TRUNK]
   switchport mode trunk
   switchport trunk native vlan [ID_VLAN_NATIVE]
```
- `[INTERFACE_TRUNK]`: L'interface connectée au routeur (e.g., `GigabitEthernet0/1`).
- `[ID_VLAN_NATIVE]`: Le VLAN natif sur le lien trunk (e.g., 1).
3. Mettre les ports vers les téléphones et PC en mode access vlan XX pour le vlan PC et voice vlan XX pour le vlan VOIX
```
interface [INTERFACE_ACCESS]
   switchport mode access
   switchport access vlan [ID_VLAN_DATA]
   switchport voice vlan [ID_VLAN_VOIX]
```
- `[INTERFACE_ACCESS]`: Interface connectée aux téléphones IP et aux PC (e.g., `FastEthernet0/1`).
- `[ID_VLAN_DATA]` et `[ID_VLAN_VOIX]`: Numéros des VLANs attribués précédemment pour les données et la voix.
## Routeur
1. Sur interface vers switchs créer sous interface pour le chaque VLAN (DOT1Q numvlan) et ajouter pour chaque sous-interface les IP, pour la sous interface du vlan native bien préciser DOT1Q XX native
```
interface [INTERFACE_PRINCIPALE].[ID_VLAN_DATA]
   encapsulation dot1Q [ID_VLAN_DATA]
   ip address [IP_INTERFACE_DATA] [MASQUE]
interface [INTERFACE_PRINCIPALE].[ID_VLAN_VOIX]
   encapsulation dot1Q [ID_VLAN_VOIX]
   ip address [IP_INTERFACE_VOIX] [MASQUE]
interface [INTERFACE_PRINCIPALE].[ID_VLAN_NATIVE]
   encapsulation dot1Q [ID_VLAN_NATIVE] native
   ip address [IP_INTERFACE_NATIVE] [MASQUE]
```
- `[INTERFACE_PRINCIPALE]`: Interface physique sur le routeur (e.g., `GigabitEthernet0/0`).
- `[ID_VLAN_DATA]`, `[ID_VLAN_VOIX]`, `[ID_VLAN_NATIVE]`: ID des VLANs.
- `[IP_INTERFACE_DATA]`, `[IP_INTERFACE_VOIX]`, `[IP_INTERFACE_NATIVE]`: Adresses IP pour les sous-interfaces.
- `[MASQUE]`: Masque de sous-réseau pour les adresses IP.
2. Ajouter le DHCP pour configurer automatiquement les réseaux VOIX et DATA en précisant le default-router pour chaque  + option qui fait télécharger l'image pour que les téléphones puissent boot
```
ip dhcp pool VOIX
   network [RESEAU_VOIX] [MASQUE]
   default-router [GATEWAY_VOIX]
   option 150 ip [TFTP_SERVER]

ip dhcp pool DATA
   network [RESEAU_DATA] [MASQUE]
   default-router [GATEWAY_DATA]
```
- `[RESEAU_VOIX]` et `[RESEAU_DATA]`: Réseaux IP pour la voix et les données.
- `[GATEWAY_VOIX]` et `[GATEWAY_DATA]`: Gateways par défaut pour les VLANs voix et données.
- `[TFTP_SERVER]`: Serveur TFTP pour le téléchargement d'images de téléphone.
1. Configurer le service telephonie avec le max-dn, max-ephones, ip source
```
telephony-service
   max-dn [MAX_DN]
   max-ephones [MAX_EPHONES]
   ip source-address [IP_SOURCE_ADDRESS] port [PORT]
```
- `[MAX_DN]`: Nombre maximum de Directory Numbers.
- `[MAX_EPHONES]`: Nombre maximum de téléphones IP.
- `[IP_SOURCE_ADDRESS]`: Adresse IP du service de téléphonie.
- `[PORT]`: Port du service (généralement 2000 pour SCCP).
1. Configurer les ephone DN avec leur number, les ephones avec le type,button
```
ephone-dn [ID_DN]
   number [NUMERO]
ephone [ID_EPHONE]
   mac-address [ADRESSE_MAC]
   type [TYPE_TEL]
   button [BOUTON]:[ID_DN]
```
- `[ID_DN]`: Identifiant unique pour ephone-dn.
- `[NUMERO]`: Numéro de téléphone attribué à ce ephone-dn.
- `[ID_EPHONE]`: Identifiant unique pour ephone.
- `[ADRESSE_MAC]`: Adresse MAC du téléphone.
- `[TYPE_TEL]`: Modèle du téléphone (e.g., 7960).
# Configuration cisco VoIP 

## Partie Routeur 
### Etape 1 : Créer un pool DHCP pour les téléphones
* Cette étape consiste à configurer un pool DHCP sur le routeur Cisco afin de fournir automatiquement les adresses IP, la passerelle par défaut, le serveur DNS et l'adresse du serveur TFTP (option 150) aux téléphones IP. L'exclusion d'adresses IP est utilisée pour éviter que le routeur ne distribue des adresses IP déjà utilisées par d'autres équipements statiquement configurés dans le réseau.
* Commande 
```
ip dhcp excluded-address [IP_DEBUT] [IP_FIN]
ip dhcp pool [NOM_POOL]
	network [IP_RESEAU] [MASQUE]
	default-routeur [IP_GATEWAY] # La gateway que doivent avoir les telephones dans ce network
	option 150 ip [IP_TFTP_SERVER]
	dns-server [IP_DNS]
```

## Etape 2 : Création de VLAN Voix
* Le VLAN de voix est créé pour séparer le trafic de données du trafic voix. Cela permet d'assurer la qualité de service nécessaire aux communications vocales en évitant que les paquets de voix ne soient mélangés avec d'autres types de trafic potentiellement encombrants.
* Commande 
```
vlan [NUMERO]
	name [NOM]
```
## Etape 5 : Atttribution VLAN voix à l'interface switch 
* Cette étape concerne la configuration des ports de switch pour qu'ils supportent à la fois un téléphone IP et un PC. Le téléphone IP est connecté directement au switch, et le PC est généralement connecté au téléphone IP (qui agit comme un switch à deux ports).
* Commande 
```
interface [INTERFACE]
	switchport mode access
	switchport access vlan [NUMERO] #Du PC
	switchport voice vlan [NUMERO] # Du Téléphone
```
## Etape 6 : Entre Switch et routeur 
* Pour connecter un switch à un routeur et transporter plusieurs VLANs, il faut configurer l'interface du switch en mode trunk. Le VLAN natif est le VLAN dont le trafic n'est pas tagué lorsqu'il traverse le trunk.
* Commande 
```
interface [INTERFACE]
	switchport mode trunk
	switchport trunk native vlan [NUMERO]
```
Bien sûr, je vais fournir des explications plus détaillées pour ces deux étapes.

## Étape 7 : Configurer un téléphone sur le routeur
* Dans un environnement de téléphonie Cisco utilisant CallManager Express, la configuration des téléphones IP se fait par les commandes `ephone` (pour electronic phone) et `ephone-dn` (pour electronic phone directory number).
* **ephone-dn** : Il s'agit de la configuration du numéro de répertoire qui sera assigné au téléphone. C'est en quelque sorte le "numéro de ligne" que le téléphone utilisera pour passer et recevoir des appels.
* **ephone** : C'est ici que l'on configure les paramètres spécifiques au téléphone, tels que son adresse MAC, le type de téléphone (par exemple, un softphone comme Cisco IP Communicator ou un modèle physique), et le bouton auquel le numéro de répertoire est associé.
* **Commande** :
```shell
ephone-dn [1]
   number [5501]
ephone [1]
   mac-address [1234.5678.9abc]
   type [CIPC]
   button [1:1]
```
**Champs modifiables** :
- `[1]` après `ephone-dn` et `ephone` est l'identifiant unique pour cet ephone-dn et ephone dans la configuration du routeur.
- `5501` est le numéro de téléphone qui sera utilisé pour appeler ce téléphone.
- `XXXX.XXXX.XXXX` est l'adresse MAC du téléphone physique. Cette adresse doit être trouvée sur le téléphone lui-même ou dans son interface web.
- `CIPC` indique le type de téléphone. Si vous utilisez un autre type de téléphone Cisco, le type ici serait différent (par exemple, `7960` pour un Cisco 7960).
- `1:1` signifie que le bouton numéro 1 sur le téléphone est associé à l'ephone-dn 1. Si vous aviez plusieurs lignes, vous pourriez avoir `button 1:2`, `button 2:1`, etc., pour les associer différemment.
# Étape 8 : Créer les dial-peers

Les dial-peers sont essentiels pour le routage des appels dans une configuration VoIP Cisco. Chaque dial-peer contient un ensemble de configurations qui définissent comment et où les appels doivent être acheminés basés sur le numéro composé.

* **Commande** :
```shell
dial-peer voice 1000 voip
   destination-pattern 5501
   session target ipv4:192.168.1.10
```
**Champs modifiables** :
- `1000` est l'ID du dial-peer.
- `5501` est le pattern. Si quelqu'un compose le numéro 5501, cet appel sera acheminé via ce dial-peer.
- `192.168.1.10` est l'adresse IP de destination pour le routage de l'appel (par exemple, le serveur CallManager Express ou un autre routeur avec lequel vous établissez une connexion VoIP).
