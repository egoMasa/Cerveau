# Guide VXLAN

# Sommaire 
- [ ] Différence entre VXLAN et VLAN
- [ ] Elements du VXLAN
- [ ] Cas d'utilisation
- [ ] Fonctionnement VXLAN
- [ ] Configuration VXLAN

# 1) Différence entre VXLAN et VLAN
* Le principe des VLANS et VXLAN sont de segmenter l'interaction des communications entre des personnes appartenant au meme ID

* VXLAN est un VLAN mais de couche 3 qui encapsule des trames Ethernet dans des paquets UDP [UDP[Ethrnet]] et est route entre 2 VTEPs. On l'utilise dans les datacenters principalement car l'architecture des spines leaf sont des liason L3 et car on doit avoir + de VLAN ID disponibles qui sont devenu des VNI

* VTEPs (VXLAN Tunnel EndPoints)
  * S'occupe de l'encapusulation et la désencapsulation des trames
  * 
* VNI (VXLAN Network Identifier) = Identifiant de segmentation réseau, 16 millions de VNI possibles
* VXLAN est utilisé dans les datacenters car l'architecture en spine LEAF utilise de la couche 3 et on a besoin d'un nombre de VLAN supérieur à 4096:
```
1. Serveur
2. Switch L2
3. LIEN L3
4. Switch L3
5. Routeur
```
