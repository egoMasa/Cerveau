# Comprendre la différence entre la commutation et le routage

# I) Commutation
## Principe de commutation
- La commutation est une technique utilisée pour transmettre des données (trames) au sein d'un même réseau.
- Elle connecte plusieurs périphériques sur un réseau local (LAN).
- Les commutateurs (switches) sont responsables de cette opération.
- Elle est basée sur l'adresse MAC de la trame.
## Etapes d'envoi de trame
1. Le commutateur reçoit la trame sur un de ses ports.
2. Il extrait l'adresse MAC de destination.
3. Il la compare avec sa MAC Address Table (table des adresses MAC).
4. Si l'adresse MAC est trouvée, la trame est envoyée directement vers le port associé à cette adresse.
5. Si non, la trame est diffusée sur tous les ports sauf le port d'entrée.
6. Quand un hôte répond, le switch ajoute l'adresse MAC source de l'hôte à sa table.
## Etapes de réponse de trame
1. L'hôte destinataire reçoit la trame et répond.
2. Le switch utilise les adresses MAC pour acheminer cette réponse vers l'expéditeur initial.
## Exemple de commutation
- Lorsqu'un hôte A envoie une trame à un hôte B sur le même réseau, le switch utilise sa table pour déterminer le port auquel est connecté l'hôte B et achemine la trame directement vers celui-ci.
## Table d'adresse MAC
* Chaque commutateur possède sa propre table d'adresse MAC qui relie un port à l'adresse MAC du périphérique connecté sur ce port
* Une table d'adresse MAC peut être configuré dans 2 modes différents : 
	* ***Dynamique*** (défaut) :  Le commutateur apprendra automatiquement les adresses MAC et remplira sa table d'adresses MAC (table CAM) en examinant l'adresse MAC source des trames entrantes et des trames d'inondation s'il ne sait pas où transférer la trame
	* ***Statique*** : Pour empécher qu'un attaquant usurpe une certaine adresse MAC pour modifier les entrées de la table d'adresses MAC, on configure manuellement les entrées dans la table d'adresses MAC. Une entrée statique remplacera toujours les entrées dynamiques.
* Consulter la table d'adresse MAC d'un commutateur 
```
show mac address-table dynamic
show mac address-table dynamic [MAC]
show mac address-table dynamic interface [interface]
```
* Vider la table d'adresse MAC
```
clear mac address-table dynamic
```
* Afficher le temps de vieillissement en seconde d'une adresse MAC (durée pendant laquelle une adresse MAC reste dans la table d'adresses MAC du commutateur avant d'être automatiquement supprimée si elle n'est plus utilisée ou vue sur le réseau). Si le commutateur ne voit pas une adresse MAC particulière pendant X secondes, elle sera supprimée de la table d'adresses MAC
```
SW1#show mac address-table aging-time 
Global Aging Time:  300
Vlan    Aging Time
----    ----------
```
* Transformer une entrée dynamique en entrée statique
```
mac address-table static [MAC] [vlan X] interface [interface]
show mac address-table static
```
* Empecher le traffic vers une adresse MAC
```
SW1(config)#mac address-table static [MAC] vlan [NUM] drop
```

## Mode duplex et vitesse
* Pour une communication entre 2 ports fonctionne, il faut respecter 2 paramètres 
* **Mode Duplex** : Le mode duplex d'un port de commutateur fait référence à la manière dont les données sont transmises entre le commutateur et les appareils connectés.
    - **Full Duplex** : Permet la transmission de données dans les deux sens simultanément. Cela signifie que l'appareil peut envoyer et recevoir des données en même temps, ce qui améliore les performances.
    - **Half Duplex** : Limite la transmission de données à un seul sens à la fois. L'appareil ne peut soit envoyer soit recevoir des données à un moment donné, ce qui peut conduire à des collisions si plusieurs appareils tentent de communiquer simultanément.
- **Même Vitesse de Transmission** : Les deux ports doivent fonctionner à la même vitesse (par exemple, 10Mb/s, 100Mb/s, 1Gb/s, etc.). Si les vitesses sont différentes, la communication peut être altérée ou même impossible. La négociation automatique (auto-negotiation) permet souvent de résoudre ce problème en sélectionnant la vitesse maximale commune supportée par les deux appareils.
- Afficher le mode en cours et vitesse de transmission
```
show interfaces fa0/1

Auto-duplex, 10Mb/s, media type is 10/100BaseTX
Half-duplex, Auto-speed, media type is 10/100BaseTX
```
* Configurer vitesse du port et mode duplex
```
interface fa0/3
	speed [auto]
	duplex [auto]
```

## II) Routage

### Principe
- Le routage permet d'acheminer des paquets entre différents réseaux.
- Les routeurs sont les dispositifs responsables de cette opération.
- Ils utilisent les adresses IP pour prendre leurs décisions.
- Le chemin emprunté peut être déterminé à l'aide d'algorithmes de routage.
- Les informations de couche 2 (comme l'adresse MAC) sont remplacées à chaque saut par un routeur.
### Fonctionnement
1. L'hôte source construit un paquet avec une en-tête IP.
2. Le paquet est transmis à la passerelle par défaut (souvent un routeur).
3. Le routeur examine l'en-tête IP pour déterminer l'adresse de destination.
4. Il utilise sa table de routage pour déterminer le prochain saut.
5. Le paquet est ensuite envoyé à un autre routeur ou directement à l'hôte de destination.
### Cas particuliers
- **Routage sur liaison série** : Lors d'une connexion point-à-point, le routeur encapsule le paquet dans le format de trame approprié pour l'interface de sortie (par exemple, HDLC ou PPP). Les adresses de couche 2 ne sont pas nécessaires dans ce contexte.
- **Routage sur liaison normale** : Les adresses MAC source et destination changent à chaque passage par un routeur, tandis que les adresses IP restent constantes tout au long du chemin.
### Modifications des champs
- Quand un hôte A envoie un paquet vers un hôte B via un routeur :
    1. L'adresse MAC source est celle de l'hôte A, l'adresse MAC destination est celle de la passerelle (le routeur).
    2. Quand le routeur reçoit le paquet, il change l'adresse MAC source à celle de son interface de sortie et l'adresse MAC destination à celle du prochain saut ou de l'hôte B si celui-ci est sur le réseau directement connecté.
    3. Sur une liaison série, les informations de couche 2 peuvent ne pas être utilisées.
