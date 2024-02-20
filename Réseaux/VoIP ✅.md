# Sommaire 
- [ ] VoIP et ToIP 
- [ ] Configuration cisco VoIP
- [ ] Ephone : Téléphone physique
- [ ] Ephones-dn : Numéro

# Topologie 
![[Pasted image 20240220112157.png]]

## Configuration de la VoIP Cisco
## Etape 1 : Paramètres de base des équipements
```
host [NOM]
no ip domain-lookup
line console 0 
	password cisco
line vty 0 15 
	password cisco
	login
```

## Etape 2 : Créer les sous interfaces du routeur GW
* On viens activer l'interface entre la GW et le SW sans lui renseigner d'IP
* On viens créer autant de sous interface que 2 vlan 
```
int F0/0
	no shut
	
int F0/0.[ID_VLAN_VOIX]
	ip address [GW_ID_VLAN_VOIX] [MASQUE]
	encapsulation dot1Q [ID_VLAN_VOIX]

int F0/0.[ID_VLAN_DATA]
	ip address [GW_ID_VLAN_DATA] [MASQUE]
	encapsulation dot1Q [ID_VLAN_DATA]
```
## Etape 2 : Créer et attribuer les VLANs sur SW
* On viens créer 2 VLAN : 
	* VOIX pour les téléphones
	* DATA pour les autres équipements
* On peut renseigner 1 VLAN telephonie et 1 VLAN classique sur un lien en meme temps sans faire de trunk
* On aura donc un switchport access vlan data et un switchport voice vlan voix sur un port
* On configure un simple lien trunk entre le SW et le serveur de téléphonie
```
vlan 10
	name VOIX
vlan 20
	name DATA
	
int range [VERS_EQUIP]
	switchport mode access
	switchport access vlan [ID_VLAN_DATA]
	switchport voice vlan [ID_VLAN_VOIX]
	
int range [VERS_ROUTEUR]
	switchport mode trunk
```
## Etape 2 : Configuration serveur DHCP 
* On viens configurer deux pool DHCP, chacun s'occupe d'attribuer les IP à des VLAN spécifique (VOIX, DATA)
* On renseigne le réseau du VLAN dans lequel le pool sera effectué
* On renseigne les informations IP qu'auront les équipement (GW)
* On renseigne le protocole de communication qu'utiliseront les téléphones pour communiquer (150 = Cisco SCCP, 66 = SIP)
```
ip dhcp pool VOICE
 network [NET_VLAN_VOIX] [MASQUE]
 default-router [GW_VLAN_VOIX] = sous interface vlan voix du routeur
 option 150 ip [GW_VLAN_VOIX]  = sous interface vlan voix du routeur
 
ip dhcp pool DATA
 network [NET_VLAN_DATA] [MASQUE]
 default-router [GW_VLAN_DATA] = sous interface vlan DATA du routeur
 option 150 ip [GW_VLAN_DATA]  = sous interface vlan DATA du routeur
```

## Etape 3 : Configuration serveur téléphonie
* On viens configurer le service téléphonique en renseignant des paramètres : 
	* max-ephones : nombre maximum de téléphones IP que peut prendre en charge ce routeur
	* max-dn : nombre maximum de numéros de téléphone que peut prendre en charge ce routeur
	* IP et port pour l'enregistrement des IP Phones
	* Optionnel : assignation automatique des IP Phones aux numéros (dn) disponibles
* On viens configurer les comptes d'abonnées (numéro = ephone-dn)
* On viens configurer les paramètres des téléphones physiques (ephone)
* On viens créer une route (dial peer) entre 2 réseau avec chacun un routeur téléphonie et on va renseigner les numéros accessibles dans l'autre réseau et commenta accéder à eux 
```
telephony-service
	device-security-mode none
	max-ephones [NUM_MAX_TEL_RESEAU]
	max-dn [PAREIL]
	ip source-address [IP_GW_VOIX] port 2000
	auto assign 4 to 6 # CAS CONFIG AUTOMATIQUE

ephone-dn [X]
	number [NUMERO]
ephone-dn [Y]
	number [NUMERO]

ephone [X]
	mac-address [MAC_TEL]
	type 7960
	button 1:1
ephone [Y]
	mac-address [MAC_TEL]
	type 7960 #modele
	button 1:2

dial-peer voice 1 voip
 destination-pattern 4...
 session target ipv4:10.0.0.1
	
```
--- 
1. Attribuer adresse IP sur interface routeur
```
interface FastEthernet0/0
 ip address [IP] 255.255.255.0
 no shut
```
1. Créer sous interface avec dot1Q sur routeur
```
interface FastEthernet0/0.[X]
 encapsulation dot1Q [X]
 ip address [IP] 255.255.255.0
```
1. Créer route vers réseau 2
```
ip route 0.0.0.0 0.0.0.0 [GW_NET2]
```
1. Créer liaison dial-peer avec routeur voisin (route statique pour les téléphones)
```
dial-peer voice 1 voip
 destination-pattern 5...
 session target ipv4:[GW_NET2]
```
1. Créer service telephony et définir paramètres
```
telephony-service
 max-ephones 5
 max-dn 5
 ip source-address 172.16.10.1 port 2000
```
1. Créer les ephone-dn avec un numero relié
```
ephone-dn 1 [OBJET DANS ANNUAAIRE]
 number 4001 # Numéro qu'on va composer
ephone-dn 2
 number 4002 # Numéro qu'on va composer
```
1. Créer un ephone par téléphone et assigner paramètres
```
ephone 1 []
 device-security-mode none
 mac-address 0001.63A6.998E
 type 7960
 button 1:1

ephone 2
 device-security-mode none
 mac-address 00D0.D383.4199
 type 7960
 button 1:2
```
## Checklist config SW
1. Configurer nom de la machine
2. Desactiver dns 
3. Configurer mot de passe console et vty
4. Créer vlan et leur nom
5. Associer vlan aux interfaces en mode access
6. Configurer lien vers routeur en mode trunk et switchport voice vlan 1
7. Créer route par défaut vers routeur sur une sous interface
--- 
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
