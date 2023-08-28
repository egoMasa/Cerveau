# EIGRP (gros réseaux)

EIGRP est un protocole avancé de routage interne conçu pour les grands réseaux. Comparé à d'autres protocoles tels que RIP, il offre de nombreux avantages en termes de performance, de fiabilité et de flexibilité.

## Fonctionnement :

* EIGRP est souvent décrit comme un protocole **hybride**. Bien qu'il soit principalement basé sur un ***vecteur de distance***, il emprunte également certaines caractéristiques des protocoles à ***état de lien***.
* Il offre une ***convergence rapide*** grâce à son algorithme DUAL.
* EIGRP supporte le ***VLSM*** (Variable Length Subnet Masking), offrant une flexibilité accrue dans la conception du réseau.
* Pour la communication entre routeurs voisins, EIGRP utilise le ***RTP (Reliable Transport Protocol)*** assurant la livraison fiable des ***messages EIGRP***.
* L'algorithme ***DUAL (Diffusing Update Algorithm)*** est utilisé pour assurer que les chemins choisis sont exempts de boucles.

* Trois types de mises à jour sont envoyés :
	* Limitées : Envoi uniquement vers les routeurs concernés.
	* Partielles : Seules les routes ayant subi des modifications sont incluses.
	* Non périodiques : Envoi uniquement lors de changements dans la topologie.

* EIGRP utilise ***trois tables principales*** :
	* 1. ***Neighbor Table*** : Liste des routeurs EIGRP voisins.
	* 2. ***Topology Table*** : Contient toutes les routes apprises par EIGRP.
	* 3. ***Routing Table*** : Contient la meilleure route pour chaque destination.

### Commandes EIGRP pour IPv4 :

- **Activer EIGRP sur le routeur** :
```bash
R1(config)#router eigrp 1
```

- **Rendre une interface passive** :
```bash
R1(config-router)#passive-interface @interface
```

- **Modifier l'ID EIGRP du routeur** :
```bash
R1(config-router)#eigrp router-id @id
```

- **Annoncer un réseau** :
```bash
R1(config-router)#network @ip_reseau @masque_invert
```

- **Vérifier la configuration EIGRP** :
```bash
R1#show ip protocols | begin eigrp
```

- **Configurer l'intervalle "Hello"** :
```bash
R1(config-if)#ip hello-interval eigrp @instance @secondes
```

- **Configurer l'intervalle "Hold-time"** :
```bash
R1(config-if)#ip hold-time eigrp @instance @secondes
```

- **Modifier la métrique (bande passante) d'une interface** :
```bash
R1(config-if)#bandwidth @num
```

- **Résumer des routes** :
```bash
R1(config-if)#ip summary-address eigrp ASN PREFIX/MASQUE
```

### EIGRP pour IPV6 :

* Les adjacences EIGRP pour IPv6 sont établies via des adresses ***link-local***.
* EIGRP pour IPv6 utilise le groupe multicast ***FF02::A***.
* Par défaut, EIGRP pour IPv6 est en état "shutdown". Il faut explicitement l'activer.

### Commandes EIGRP pour IPv6 :

```cisco
ipv6 unicast-routing
ipv6 router eigrp 1
    eigrp router-id 1.1.1.1
    no shutdown

int @int
    ipv6 address 2001:db8:cafe::1/64
    ipv6 eigrp 1
    ipv6 summary-address eigrp ASN PREFIX/MASQUE

sh ipv6 route eigrp
sh ipv6 eigrp neighbor
sh ipv6 int brief
```
