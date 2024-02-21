# Topologie 

![VOIP1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/TOPOLOGIE_VOIP1.png)

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
	no shut

int F0/0.[ID_VLAN_DATA]
	ip address [GW_ID_VLAN_DATA] [MASQUE]
	encapsulation dot1Q [ID_VLAN_DATA]
	no shut
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
	switchport mode trunk encapsulation dot1q
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
 option 150 ip [GW_VLAN_VOIX,[TFTP_SERVER]]  = sous interface vlan voix du routeur
 
ip dhcp pool DATA
 network [NET_VLAN_DATA] [MASQUE]
 default-router [GW_VLAN_DATA] = sous interface vlan DATA du routeur
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

# Topologie 2

![VOIP2.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/TOPOLOGIE_VOIP2.png)
* Configuration des équipements 
```
############### R1 CONFIG ############
no ip domain lookup
hostname R1
enable secret class

line vty 0 15 
	password cisco
	login
line console 0
	password cisco
int F0/0
	no shut
int F0/0.10
	ip address 172.16.10.1 255.255.255.0
	encapsulation dot1q 10
	no shut 
int F0/0.20
	ip address 172.16.20.1 255.255.255.0
	encapsulation dot1q 20
	no shut 
int F0/0.99
	ip address 172.16.99.1 255.255.255.0
	encapsulation dot1q 99
	no shut
int F0/1
	ip address 10.0.0.1 255.255.255.0
	no shut 

ip dhcp pool VOICE
	network 172.16.10.0 255.255.255.0
	default-router 172.16.10.1 
	option 150 ip 172.16.10.1 
ip dhcp pool DATA
	network 172.16.20.0 255.255.255.0
	default-router 172.16.20.1
ip dhcp pool MANAGEMENT
	network 172.16.99.0 255.255.255.0
	default-router 172.16.99.1

telephony-service 
	device-security-mode none
	max-ephones 2
	max-dn 2
	ip source-address 172.16.10.1 port 2000
ephone-dn 1
	number 4001
ephone 1
	mac-address 0001.63A6.998E
	type 7960
	button 1:1
ephone-dn 2 
	number 4002
ephone 2
	mac-address 00D0.D383.4199
	type 7960
	button 1:2

dial-peer voice 1 voip
	destination-pattern 5...
	session target ipv4:10.0.0.2


############### SW1 CONFIG ###########
no ip domain lookup
hostname SW1
enable secret class

line vty 0 15 
	password cisco
	login
line console 0
	password cisco

vlan 10
	name VOICE
vlan 20
	name DATA
vlan 99
	name MANAGEMENT

int range F0/2-3
	switchport mode access
	switchport access vlan 20
	switchport voice vlan 10
	power inline auto 
int F0/1
	switchport trunk encapsulation dot1q
	switchport mode trunk 
	switchport trunk allowed vlan 10,20,99

int F0/4
	switchport mode access
	switchport access vlan 20
int F0/5
	switchport mode access
	switchport access vlan 99
```
