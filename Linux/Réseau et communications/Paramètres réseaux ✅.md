# Sommaire 
1. Gestion des interfaces 
2. Configuration des interfaces 
3. Configuration DNS
4. Configuration DHCP 
5. Configuration gateway
6. Configuration WIFI
7. Commande IP 
# Gestion des interfaces 
* Lister les interfaces
```
ifconfig
ip a
```
* Activer/désactiver interface
```
sudo ip link set eth0 up
sudo ip link set eth0 down
```
* Redémarrer le service réseau 
```
sudo systemctl restart networking
```
# Configuration des interfaces 
## Temporaire 
* Ajouter une configuration d'interface temporaire 
```
sudo ip addr add [IP]/[SUBNET] dev [INTERFACE]
```
## Définitive
* Editez le fichier /etc/network/interfaces
```
iface eth0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	gateway 192.168.1.1
```

# Configuration du DNS 
* Editez le fichier /etc/resolv.conf
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

# Configuration du DHCP 
## Temporaire
* Modifier interface en tant que DHCP
```
sudo dhclient [INTERFACE]
```
## Définitive 
* Editez le fichier /etc/network/interfaces
```
iface [INTERFACE] inet dhcp
```

# Configuration gateway
## Temporaire
* Ajouter une route par défaut
```
sudo ip route add default via [IP_GATEWAY]
```
## Définitive 
* Editez le fichier /etc/network/interfaces
```
iface eth0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	gateway [IP_GATEWAY]
```

# Configuration WIFI

**1. Vérifiez que votre carte Wi-Fi est reconnue :**  
```bash
lspci | grep Wireless
iwconfig
```

**2. Lever l'interface (remplacez `wlan0` par le nom de votre interface, si différent) :**
```bash
sudo ip link set wlan0 up
```

**3. Scannez les réseaux disponibles :**
```bash
sudo iwlist wlan0 scan | grep ESSID
```

**4. Connectez-vous à un réseau :**

Si le réseau est ouvert :
```bash
sudo iwconfig wlan0 essid "NOM_DU_RÉSEAU"
```

Si le réseau est sécurisé avec WPA/WPA2 (ce qui est courant) :
a. Créez un fichier de configuration pour wpa_supplicant. Ce fichier contiendra les informations nécessaires pour se connecter au réseau :
```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

b. Ajoutez les informations suivantes à ce fichier :
```
network={
    ssid="NOM_DU_RÉSEAU"
    psk="MOT_DE_PASSE_DU_RÉSEAU"
}
```

c. Enregistrez et fermez le fichier.

d. Utilisez `wpa_supplicant` pour se connecter au réseau :
```bash
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
```

**5. Demandez une adresse IP via DHCP (si le réseau utilise DHCP) :**
```bash
sudo dhclient wlan0
```

Une fois connecté, vous devriez pouvoir ping ou accéder à d'autres ressources sur le réseau.

**Notes:**
- Pour une configuration persistante, vous pouvez configurer l'interface Wi-Fi dans des fichiers de configuration spécifiques à votre distribution, par exemple `/etc/network/interfaces` sur Debian/Ubuntu.
- L'utilisation de `NetworkManager` ou d'autres outils graphiques est souvent plus simple pour la gestion quotidienne des connexions Wi-Fi, surtout si vous changez régulièrement de réseau.

# Commande IP 

La commande `ip` est l'un des outils fondamentaux pour tout administrateur systèmes. Elle permet de visualiser et de configurer les interfaces, adresses IP, routes, et bien d'autres aspects du réseau.

**Syntaxe générale :**
```bash
ip <OPTIONS> <OBJECT> <COMMAND>
```

**Objets couramment utilisés avec la commande `ip` :**
- `address` : pour gérer les adresses IP (IPv4 et IPv6) d'une interface.
- `route` : pour gérer les entrées de la table de routage.
- `link` : pour gérer les états et les propriétés des interfaces.
- `tunnel`, `rule`, `vrf`, `xfrm` : pour des fonctionnalités avancées comme le tunneling, la politique de routage, etc.

**Commandes courantes avec la commande `ip` :**

**Afficher les adresses IP des interfaces :**
```bash
ip address show
```

**Ajouter une adresse IP à une interface (exemple pour `enps03`) :**
```bash
ip address add 192.168.1.254/24 dev enps03
```

**Supprimer une adresse IP d'une interface :**
```bash
ip address del 192.168.1.254/24 dev enps03
```

**Activer l'interface `eth0` :**
```bash
ip link set eth0 up
```

**Désactiver l'interface `eth0` :**
```bash
ip link set eth0 down
```

**Modifier le MTU de l'interface `eth0` :**
```bash
ip link set eth0 mtu 9000
```

**Activer le mode promiscuité pour `eth0` :**
```bash
ip link set eth0 promisc on
```

**Ajouter une route par défaut via la passerelle `192.168.1.254` sur `eth0` :**
```bash
ip route add default via 192.168.1.254 dev eth0
```

**Ajouter une route vers `192.168.1.0/24` via la passerelle `192.168.1.254` :**
```bash
ip route add 192.168.1.0/24 via 192.168.1.254
```

**Ajouter une route vers `192.168.1.0/24` accessible via l'interface `eth0` :**
```bash
ip route add 192.168.1.0/24 dev eth0
```

**Supprimer la route pour `192.168.1.0/24` via la passerelle `192.168.1.254` :**
```bash
ip route delete 192.168.1.0/24 via 192.168.1.254
```

**Afficher la route pour l'IP `10.10.1.4` :**
```bash
ip route get 10.10.1.4
```
