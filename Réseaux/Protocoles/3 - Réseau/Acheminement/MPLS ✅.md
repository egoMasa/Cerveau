# **Guide MPLS (Multiprotocol Label Switching)**

# **1) Principe MPLS**

- **Introduction**:
    
    - MPLS est un type de réseau privé qui offre un acheminement optimisé des paquets sur de grands réseaux.
    - Il se distingue par l'utilisation de labels pour guider les paquets, plutôt que de se fier uniquement aux adresses IP.
- **Caractéristiques Principales**:
    
    - Gestion **centralisée** et **simplifiée** par un opérateur.
    - Fluidifie le trafic réseau et garantit une qualité de service (QoS) supérieure.
    - Permet une mise en place facilitée de VPN à grande échelle.
    - Réduction du temps de recherche dans les tables de routage.
- **Types de routeurs MPLS**:
    
    - **CE (Customer Edge)** : Installé chez le client pour le connecter au réseau MPLS.
    - **PE (Provider Edge)** : Labelise en entrée du réseau les paquets IP et délabelise en sortie.
    - **P (Provider)** : Commute les paquets labelisés en utilisant la table LIB (Label Information Base).

# **2) Système d'étiquetage des paquets**

- **But**: Utiliser des labels pour séparer différents types de trafic au sein du réseau MPLS, tels que voix, vidéo, email, et VPN.
- **Fonctionnement**:
    - Les routeurs analysent le label de destination pour déterminer le chemin à prendre.
    - Le label est choisi en fonction de la destination du paquet.

## **Étapes de Commutation MPLS**:

1. **Entrée dans le réseau**:
    
    - Un paquet IP arrive au PE.
    - On détermine le protocole de routage IP.
    - Un label est assigné basé sur l'IP de destination.
    - L'en-tête (label) est ajouté et le paquet est envoyé au nœud suivant.
2. **Commutation dans le réseau**:
    
    - Le paquet labelisé arrive au routeur P.
    - Le protocole de routage est déterminé via la LIB.
    - Le label est modifié et le paquet est envoyé au nœud suivant.
3. **Sortie du réseau**:
    
    - Le paquet arrive au routeur PE de sortie.
    - Le label est retiré et le paquet est transmis au réseau de destination.

# **3) Comparaison entre MPLS et l'Internet**

- **Performance**: MPLS est plus rapide car il utilise des labels pour acheminer le trafic directement.
- **Sécurité**: MPLS offre une meilleure sécurité en étant géré privément et en évitant certains risques liés à l'Internet public.
- **Coût**: MPLS peut être plus coûteux mais offre de meilleurs avantages en performance et sécurité.
- **Flexibilité**: L'Internet est plus flexible car il permet une connexion à tout service, contrairement au MPLS qui est souvent limité à des sites spécifiques.

# **4) Glossaire**

- **LSR (Label Switch Router)**: Routeur avec capacités MPLS.
- **Label**: Information ajoutée entre la couche 2 et la couche 3 pour faciliter la commutation MPLS.
- **FEC (Forwarding Equivalent Class)**: Groupe de paquets ayant le même traitement MPLS.
- **LDP (Label Distribution Protocol)**: Protocole utilisé pour l'échange de labels.
- **LIB (Label Information Base)**: Table contenant les labels.
- **LFIB (Label Forwarding Information Base)**: Table de commutation extraite de la LIB.

# 5) Configuration de MPLS
* Activer MPLS
```
ip cef
```
* Assigner réseau MPLS à une interface
```
int G0/0
	mpls ip
```
* Afficher table de commutation (LFIB)
```
sh mpls forwarding-table
```
* Afficher table des labels (LIB)
```
sh mpls ldp bindings
```

# **6) VPN MPLS**

- **Principe**: Permet de séparer les flux VPN pour chaque utilisateur ou section.
- **Double Labelisation**:
    - **Label extérieur**: Identifie le chemin vers la destination.
    - **Label intérieur**: Identifie le VPN du client.
- **Rôles des routeurs dans un VPN MPLS**:
    - **Routeur CE**: Relie le client au PE, sans connaissance de MPLS ou du VPN.
    - **Routeurs PE**: Échangent des informations de routage avec le CE, isolent chaque CE avec une VRF et échangent des routes avec d'autres PE via MP-BGP.
    - **Routeur P**: Transmet les informations entre PE sans avoir connaissance du VPN.

## Configuration VPN

### Etape 1 : Configurer le Route Distinguisher sur un PE
```
ip vrf [NOM_VRF] 
	rd [ASN]:[NUMERO]
```
### Etape 2 : ### Configurer le Route Target sur un PE
```
ip vrf [NOM_VRF]
   # Pour l'exportation des routes
   route-target export [ASN]:[NUMERO_EXPORT]
   # Pour l'importation des routes
   route-target import [ASN]:[NUMERO_IMPORT]
   # Pour l'importation et l'exportation simultanées
   route-target both [ASN]:[NUMERO]
```