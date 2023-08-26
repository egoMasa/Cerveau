## **Introduction à Ethernet**

Ethernet est une technologie de réseau basée sur la transmission de trames, principalement utilisée dans les réseaux locaux (LAN). Elle est initialement basée sur une méthode d'accès appelée CSMA/CD, bien que cette méthode soit moins pertinente dans les réseaux modernes.

## **Caractéristiques principales d'Ethernet**

- **Technologie support partagé** : Dans ses débuts, Ethernet utilisait un bus partagé. Cependant, avec les commutateurs modernes, ce support n'est plus partagé.
- **Accès concurrentiel** : Tout dispositif peut essayer de transmettre à tout moment.
- **Principe du premier arrivé, premier servi** : Le dispositif qui détecte le médium comme étant libre en premier commence la transmission.
- **Gestion des collisions** : Des mécanismes existent pour détecter et gérer les collisions sur le réseau.

## **Méthode d'accès MAC (CSMA/CD)**

- Bien que de moins en moins utilisé dans les environnements actuels, le CSMA/CD était essentiel pour gérer l'accès au médium dans les anciens réseaux Ethernet half-duplex.
- Si le canal est libre, la station place son trafic. Sinon, elle attend.
- Pas de fonction de fiabilité comme les accusés de réception (ACK), la gestion des erreurs ou le contrôle de flux.

## **Fonctionnement du CSMA**

1. Une interface veut communiquer et écoute le support.
2. Si une porteuse est détectée, elle retarde sa communication.
3. Si aucune porteuse n'est détectée, elle considère que le support est libre, attend un instant puis commence la transmission.
4. En cas de média partagé, toutes les interfaces reçoivent les trames et gardent celles qui leur sont destinées.

## **Gestion des collisions (CD)**

- Les collisions surviennent lorsque deux dispositifs tentent de transmettre simultanément.
- Dans les réseaux modernes avec des commutateurs Ethernet fonctionnant en full-duplex, les collisions sont pratiquement inexistantes.

## **Ethertype**

L'Ethertype indique le protocole encapsulé dans la trame. Par exemple :

* ***0x0800*** : Internet Protocol version 4 (***IPv4***)
* ***0x0806*** : Address Resolution Protocol (***ARP***)
* ***0x8100*** : VLAN-tagged frame (***IEEE 802.1Q***)
* ***0x86DD*** : Internet Protocol Version 6 (***IPv6***)
* 0x8863 : PPPoE Discovery Stage
* 0x8864 : PPPoE Session Stage
* 0x8870 : Jumbo Frames
* 0x888E : EAP over LAN (IEEE 802.1X)
* 0x9100 : Q-in-Q

## **Adressage MAC**

- Chaque interface réseau dispose d'une adresse MAC unique de 48 bits.
- Les 24 premiers bits, appelés OUI, identifient le fabricant.
- Les 24 derniers bits sont attribués par le fabricant à chaque interface.

### **Types d'adresses MAC**

- **Unicast** : Adresse d'une seule interface.
- **Broadcast** : Adresse atteignant toutes les interfaces (`FF:FF:FF:FF:FF:FF`).
- **Multicast** : Adresse destinée à un groupe d'interfaces.

## **Normes et vitesses d'Ethernet**

- **10Base-T** : 10 Mbps
- **100Base-T** (Fast Ethernet) : 100 Mbps
- **1000Base-T** (Gigabit Ethernet) : 1 Gbps ... et ainsi de suite jusqu'au 100G Ethernet et au-delà.

## **Topologies Ethernet**

- **Bus** : Dans les premiers jours d'Ethernet.
- **Étoile** : Avec des commutateurs ou des hubs au centre, utilisée dans les réseaux modernes.

## **Full Duplex vs Half Duplex**

- **Half Duplex** : Les dispositifs ne peuvent pas envoyer et recevoir simultanément, ce qui peut entraîner des collisions.
- **Full Duplex** : Les dispositifs peuvent envoyer et recevoir en même temps, éliminant la possibilité de collisions.