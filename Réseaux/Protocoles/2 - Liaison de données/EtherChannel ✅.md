# Guide EtherChannel

# 1) Principe et Concept

- **EtherChannel** est une technologie Cisco qui permet de combiner plusieurs liaisons physiques Fast Ethernet, Gigabit Ethernet, ou même 10 Gigabit Ethernet en une seule liaison logique. Cette liaison composite permet une bande passante cumulée et une redondance.

- **STP (Spanning Tree Protocol)** considère normalement un EtherChannel comme une seule liaison, évitant ainsi les blocages de ports redondants et augmentant la bande passante utilisable entre les commutateurs.

- Une fois qu'un EtherChannel est établi, une interface virtuelle, appelée **port-channel**, est créée. Cette interface représente l'EtherChannel entier et permet de configurer l'ensemble du groupe.
    
- La technologie EtherChannel fournit :
	- **Redondance** : Si l'un des liens physiques tombe, le trafic est simplement redirigé sur les autres liens actifs de l'EtherChannel sans interruption perceptible.
	- **Accroissement de la bande passante** : La bande passante de tous les liens est combinée, offrant des vitesses plus élevées entre les commutateurs ou les routeurs.
	- **Équilibrage de charge** : Le trafic est distribué sur les différents liens physiques, en fonction de divers critères comme l'adresse MAC source/destination, l'adresse IP, ou le numéro de port.

# 2) Protocoles de négociation d’EtherChannel

## PAgP (Port Aggregation Protocol) :
- Protocole propriétaire Cisco.
- **Modes** :
    - **On** : Force l'interface à entrer dans un EtherChannel sans utiliser PAgP.
    - **Desirable** : État actif de négociation. Initie la négociation PAgP.
    - **Auto** : État passif. Attends un paquet PAgP pour répondre.
- **Combinaisons pour former un EtherChannel** :
    - On <-> On
    - Desirable <-> Desirable/Auto
    - Auto <-> Desirable

## LACP (Link Aggregation Control Protocol) :
- Norme IEEE 802.3ad.
- Plus universel que PAgP et peut être utilisé avec des équipements non-Cisco.
- **Modes** :
    - **On** : Force la liaison à entrer dans un EtherChannel sans utiliser LACP.
    - **Active** : État actif de négociation. Envoie des paquets LACP.
    - **Passive** : État passif. Attend les paquets LACP pour répondre.
- **Combinaisons pour former un EtherChannel** :
    - On <-> On
    - Active <-> Active/Passive
    - Passive <-> Active
# 3) Conditions pour former un EtherChannel réussi

- Tous les ports doivent avoir la même vitesse et le même duplex.
- Tous les ports doivent être dans le même VLAN ou être configurés comme des ports trunk.
- Les paramètres natifs du VLAN doivent être identiques sur tous les ports pour les liaisons trunk.
- Les ports doivent avoir la même politique de sécurité de port, s'ils sont configurés avec PortFast, etc.
- Si un port est configuré avec une commande, tous les ports de l'EtherChannel doivent avoir cette commande.

# 4) Configuration EtherChannel
## Étape 1: Spécification des interfaces qui composent l'EtherChannel

* Pour configurer les ports que vous souhaitez inclure dans l'EtherChannel:
```
Switch(config)# interface range F0/1-2
```
- **Pour PAgP**:
```
Switch(config-if-range)# channel-protocol pagp 
Switch(config-if-range)# channel-group 1 mode {auto|desirable|on}
```
- **Pour LACP**:
```
Switch(config-if-range)# channel-protocol lacp 
Switch(config-if-range)# channel-group 1 mode {active|passive|on}
```
`channel-protocol` spécifie le protocole à utiliser, tandis que `channel-group` définit le groupe EtherChannel et le mode.

## Étape 2: Configuration de l'interface Port-Channel
* Après avoir configuré les interfaces physiques, une interface Port-Channel virtuelle est automatiquement créée. Cette interface permet de configurer les paramètres applicables à l'ensemble du groupe EtherChannel:
```
Switch(config)# interface port-channel 1
```
* Configurer comme ports trunks les interfaces:
```
Switch(config-if)# switchport mode trunk 
Switch(config-if)# switchport trunk allowed vlan {VLAN range} 
Switch(config-if)# switchport trunk native vlan {VLAN ID}
```
## Etape 3 : Activer et verifier le loadbalancing 
```
Switch(config)port-channel load-balance src-dst-ip
```
## Étape 3: Vérification de la configuration EtherChannel

- Pour afficher un résumé des groupes EtherChannel:
```
Switch# show etherchannel summary
```
- Pour afficher la configuration de l'interface Port-Channel:
```
Switch# show run interface port-channel 1
```
Ou, comme vous l'avez mentionné, pour voir la configuration à partir de la première occurrence de "interface port-channel":
```
Switch# show run | begin interface port-channel
```
