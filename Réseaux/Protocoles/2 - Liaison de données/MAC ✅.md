# **Guide du Contrôle d'Accès Média (MAC)**

## **Introduction à MAC**

L'adresse MAC (Media Access Control) est un identifiant unique assigné à chaque interface réseau pour la communication au niveau de la couche de liaison de données dans les réseaux. Elle fonctionne principalement dans le sous-couche MAC du modèle OSI.

## **Caractéristiques des adresses MAC**

- **Longueur** : 48 bits, généralement représentée en hexadécimal.
- **Unique** : Chaque adresse MAC est supposée être unique au monde.
- **Assignation** : Fabriquants de matériel réseau reçoivent des blocs d'adresses de l'IEEE.

## **Structure d'une adresse MAC**

- **OUI (Organizational Unique Identifier)** : Les 24 premiers bits. Identifient le fabricant de l'adaptateur.
- **Identifiant unique** : Les 24 bits restants. Attribués par le fabricant à chaque pièce de matériel.

## **Types d'adresses MAC**

- **Unicast** : Adresse d'une seule interface.
- **Broadcast** : Adresse atteignant toutes les interfaces (`FF:FF:FF:FF:FF:FF`).
- **Multicast** : Adresse destinée à un groupe d'interfaces.

## **MAC vs. IP**

- **MAC** : Identifiant statique et unique lié au matériel.
- **IP** : Adresse logique attribuée par le réseau, pouvant être dynamique.

## **Table MAC ou CAM Table**

Dans les commutateurs (switches), une table MAC est utilisée pour mémoriser quelles adresses MAC sont associées à quels ports. Ceci facilite la commutation efficace des trames.

## **Sécurité MAC - Filtrage d'adresses MAC**

- **Objectif** : Permettre ou refuser l'accès au réseau basé sur l'adresse MAC d'un dispositif.
- **Utilité** : Fournit une couche de sécurité supplémentaire, bien que pas aussi robuste que d'autres méthodes.

## **ARP (Address Resolution Protocol)**

Le protocole ARP est utilisé pour mapper une adresse IP vers une adresse MAC dans un réseau local. Lorsqu'un appareil souhaite communiquer avec une autre machine sur le réseau local, il utilise ARP pour obtenir l'adresse MAC associée à l'adresse IP de cette machine.