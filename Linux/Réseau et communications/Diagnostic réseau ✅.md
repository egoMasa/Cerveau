# Sommaire 
* netstat et ss
* tcpdump
* tshark 
* ping
* traceroute
* dig
* host
* iperf

# **1. netstat**  && ss
_Utilité_: Affiche les tables de réseau, notamment les connexions réseau, les tables de routage, les statistiques d'interface, et les liaisons masquées.

**Usage de base:**
```bash
netstat
```

**Options avancées:**
```bash
netstat <options>
```

**Lister tous les ports et connexions, peu importe leur état:**
```bash
netstat -a
```

**Lister tous les ports TCP:**
```bash
netstat -at
```

**Lister tous les ports UDP:**
```bash
netstat -au
```

**Visualiser seulement les ports en écoute:**
```bash
netstat -l
```

**Lister les ports TCP en écoute:**
```bash
netstat -lt
```

**Lister les ports UDP en écoute:**
```bash
netstat -lu
```

**Lister les ports UNIX en écoute:**
```bash
netstat -lx
```

**Afficher les statistiques pour tous les ports:**
```bash
netstat -s
```

**Statistiques pour les ports TCP:**
```bash
netstat -st
```

**Voir les connexions TCP avec le PID/nom du programme:**
```bash
netstat -tp
```

**Trouver un processus qui utilise un port particulier:**
```bash
netstat -an | grep ':<port number>'
```

---

N'oubliez pas que les commandes doivent être exécutées avec les droits appropriés. Utilisez `sudo` si nécessaire.

_Utilité_: C'est une alternative moderne à netstat. ss peut fournir plus d'informations que netstat et est considéré comme plus rapide.

_Commandes de base_ :

- `ss -tuln`: Affiche les ports TCP et UDP en écoute.
- `ss -o`: Affiche les connexions et leurs timers.
- `ss -s`: Donne des statistiques sur le trafic.

---

# **2. tcpdump**  
* Outil puissant pour capturer et analyser le trafic réseau. Pour utiliser certaines de ses fonctions, vous devez avoir des privilèges root.

**Lister les Interfaces Disponibles pour la Capture:**
```bash
tcpdump -D
```

**Capturer le Trafic sur une Interface Spécifique (par exemple `eth0`):**
```bash
tcpdump -i eth0
```

**Capturer un Nombre Limité de Paquets (par exemple 10) sur `eth0`:**
```bash
tcpdump -i eth0 -c 10
```

**Capturer le Trafic d'un Hôte Spécifique (par exemple `8.8.8.8`):**
```bash
tcpdump -i eth0 -c 10 host 8.8.8.8
```

**Capturer le Trafic Provenant d'un Hôte Spécifique:**
```bash
tcpdump -i eth0 src host 8.8.8.8
```

**Capturer le Trafic à Destination d'un Hôte Spécifique:**
```bash
tcpdump -i eth0 dst host 8.8.8.8
```

**Capturer le Trafic d'un Réseau Spécifique:**
```bash
tcpdump -i eth0 net 10.1.0.0/24
```

**Capturer le Trafic Basé sur la Source d'un Réseau Spécifique:**
```bash
tcpdump -i eth0 src net 10.1.0.0/24
```

**Capturer le Trafic Basé sur la Destination d'un Réseau Spécifique:**
```bash
tcpdump -i eth0 dst net 10.1.0.0/24
```

**Capturer le Trafic d'un Port Spécifique (par exemple le port DNS 53):**
```bash
tcpdump -i eth0 port 53
```

**Capturer le Trafic d'un Hôte et d'un Port Spécifiques:**
```bash
tcpdump -i eth0 host 8.8.8.8 and port 53
```

**Capturer Uniquement le Trafic HTTPS (port 443) d'un Site Spécifique:**
```bash
tcpdump -i eth0 -c 10 host www.google.com and port 443
```

**Exclure Certains Ports de la Capture (par exemple ports 53 et 25):**
```bash
tcpdump -i eth0 port not 53 and not 25
```

---

`tcpdump` offre une multitude d'options et de filtres pour vous aider à affiner vos captures. Assurez-vous toujours de comprendre les implications en matière de sécurité et de confidentialité lorsque vous capturez du trafic réseau.

---

# **3. tshark**  
_Utilité_: La version en ligne de commande de Wireshark. Il peut capturer et analyser le trafic réseau, tout comme tcpdump, mais il fournit également des capacités d'analyse avancées.

_Commandes de base_ :

- `tshark -i eth0`: Capture et affiche les paquets sur l'interface eth0 en temps réel.
- `tshark -r file.pcap`: Analyse un fichier pcap existant.

# 4. Ping et traceroute
_Utilité_ ping : Teste la connectivité réseau vers une adresse IP ou un domaine.
_Utilité_ traceroute : Affiche le chemin que les paquets prennent pour atteindre une destination.
- Exemple : `ping google.com`
- Exemple : `traceroute google.com`

# 5. dig / nslookup**  
_Utilité_: Interroge les serveurs DNS pour récupérer des informations/enregistrement sur les domaines.

**Trouver l'enregistrement A d'un domaine (qui pointe généralement vers l'adresse IP du site web) :**
```bash
nslookup example.com
```

**Vérifier les enregistrements NS d'un domaine (qui indiquent quels sont les serveurs DNS responsables du domaine) :**
```bash
nslookup -type=ns example.com
```

**Trouver les enregistrements MX (qui sont responsables de l'échange d'e-mails pour le domaine) :**
```bash
nslookup -query=mx example.com
```

**Trouver tous les enregistrements DNS disponibles d'un domaine :**
```bash
nslookup -type=any example.com
```

**Vérifier l'utilisation d'un serveur DNS spécifique (dans ce cas, en interrogeant à l'aide du serveur de noms spécifique `ns1.nsexample.com`) :**
```bash
nslookup example.com ns1.nsexample.com
```

**Effectuer une recherche DNS inverse pour vérifier si une adresse IP est liée à un domaine spécifique :**
```bash
nslookup 10.20.30.40
```

---

Notez que l'exactitude et la complétude des résultats peuvent dépendre de la configuration du serveur DNS que vous interrogez et des enregistrements DNS du domaine cible. Utilisez toujours des outils comme `nslookup` en respectant les meilleures pratiques et en étant conscient des implications de sécurité et de vie privée.

# 6. Host 
_Utilité_: Effectue une recherche DNS pour un domaine.
- Exemple : `host google.com`

# 7. iperf
_Utilité_: Teste la vitesse et la performance de la bande passante entre deux hôtes.
- Serveur : `iperf -s`
- Client : `iperf -c server_ip_address`