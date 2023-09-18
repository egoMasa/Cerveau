# Présentation 

🎯 Cette section est destiné à de l'apprentissage et à pour but de résumer et répertorier toutes les notions et concepts abordé lors de mes études en cybersécurité, que ce soit en réseau avec de la configuration Cisco, du pentesting ou de l'administration système 

🗂 Toutes les notions sont triés par sections en fonction de leur intérêt et de leur famille, ci dessous l'arborescence actuelle 

✅ Les lecons avec cette marque sont considéres comme partiellement complet, certaines modifications pourront être apportés.
# Sommaire 
```
Cerveau
├── Cybersécurité
│   ├── Attaques
│   │   ├── Malware.md
│   │   └── Types d'attaques réseau.md
│   ├── Cyberdéfense
│   │   ├── Antimalware.md
│   │   ├── Antivirus.md
│   │   ├── DLP.md
│   │   ├── EDR.md
│   │   ├── Firewall.md
│   │   ├── HIPS.md
│   │   ├── IDS IPS.md
│   │   ├── SIEM.md
│   │   ├── SOAR.md
│   │   └── SOC.md
│   ├── Forensic
│   │   └── test.md
│   ├── Pentesting
│   │   ├── 1) Reconnaissance
│   │   │   ├── Enumération par services
│   │   │   │   ├── DNS.md
│   │   │   │   ├── Enumération.md
│   │   │   │   ├── FTP.md
│   │   │   │   ├── HTTP.md
│   │   │   │   ├── LDAP.md
│   │   │   │   ├── NFS.md
│   │   │   │   ├── SMB.md
│   │   │   │   ├── SMTP.md
│   │   │   │   └── SSH.md
│   │   │   ├── Méthodologie de reconnaissance.md
│   │   │   └── Outils
│   │   │       ├── Autorecon.md
│   │   │       ├── Dirb.md
│   │   │       ├── Dirbuster.md
│   │   │       ├── Enum4Linux.md
│   │   │       ├── Gobuster.md
│   │   │       ├── Masscan.md
│   │   │       └── Nmap.md
│   │   ├── 2) Détection et exploitation de vulnérabilités
│   │   │   ├── 2.1) Détection de vulnérabilités.md
│   │   │   ├── 2.2) Exploitation de vulnérabilités.md
│   │   │   ├── Méthodologie de détection et exploitation de vulnérabilités.md
│   │   │   └── Outils
│   │   │       ├── Burpsuite.md
│   │   │       ├── Exploit-DB.md
│   │   │       ├── Metasploit.md
│   │   │       ├── Nessus.md
│   │   │       ├── NSE Scripts.md
│   │   │       ├── OpenVAS.md
│   │   │       ├── OWASP ZAP.md
│   │   │       └── Rapid7.md
│   │   ├── 3) Elévation de privilèges
│   │   │   ├── Elevation de privilèges Linux.md
│   │   │   └── Elevation de privilèges Windows.md
│   │   ├── 4) Mouvement latéral et persistance
│   │   │   └── test.md
│   │   ├── 5) Rapport d'intrusion
│   │   │   └── test.md
│   │   └── Notes CTF.md
│   ├── Réglementation
│   │   ├── ISO 27001 - Information Security Management.md
│   │   ├── ISO 27001.md
│   │   ├── ISO 27032 Cyber Security.md
│   │   ├── ISO 27035 Incident Management.md
│   │   ├── ISO 27701 - Privacy Information Management.md
│   │   ├── NISE.md
│   │   ├── NIS.md
│   │   └── RGPD.md
│   └── Steganographie
│       └── Analyse d'images.md
├── Linux
│   ├── Administration système
│   │   ├── Configuration générale.md
│   │   ├── Fichiers log ✅.md
│   │   ├── Gestion des droits ✅.md
│   │   ├── Gestionnaire d'installation ✅.md
│   │   └── Utilisateurs et groupes ✅.md
│   ├── Architecture linux
│   │   ├── Boots et processus d'initialisation ✅.md
│   │   ├── Différentes distributions ✅.md
│   │   ├── Kernel (noyau) ✅.md
│   │   └── Shells ✅.md
│   ├── Automatisation et supervision
│   │   ├── Ansible.md
│   │   ├── Bash.md
│   │   ├── Crontab.md
│   │   ├── Grafana.md
│   │   ├── Icinga.md
│   │   └── Zabbix.md
│   ├── Configuration de services
│   │   ├── Accès à distance
│   │   │   ├── RDP.md
│   │   │   ├── SSH.md
│   │   │   ├── Telnet.md
│   │   │   └── VNC.md
│   │   ├── Authentification
│   │   │   ├── FreeRADIUS.md
│   │   │   ├── MIT Kerberos.md
│   │   │   └── OpenLDAP.md
│   │   ├── Base de données
│   │   │   ├── MongoDB (NoSQL).md
│   │   │   ├── MySQL.md
│   │   │   ├── Oracle Database.md
│   │   │   ├── PostgreSQL.md
│   │   │   └── Redis.md
│   │   ├── DNS-DHCP
│   │   │   └── dnsmasq.md
│   │   ├── Mails
│   │   │   ├── Evolution.md
│   │   │   ├── Kmail.md
│   │   │   └── Thunderbird.md
│   │   ├── Partage de fichiers
│   │   │   ├── FTP-FTPS-SFTP ✅.md
│   │   │   ├── NFS.md
│   │   │   ├── SCP.md
│   │   │   └── SMB-SAMBA ✅.md
│   │   ├── Proxy
│   │   │   ├── NGINX.md
│   │   │   └── Squid.md
│   │   ├── Sauvegarde et stockage
│   │   │   └── RSYNC.md
│   │   ├── Téléphonie
│   │   │   └── Asterisk.md
│   │   ├── Virtualisation
│   │   │   ├── Docker.md
│   │   │   ├── KVM.md
│   │   │   └── QEMU.md
│   │   ├── VPN
│   │   │   ├── OpenVPN.md
│   │   │   └── WireGuard.md
│   │   └── Web
│   │       ├── Apache.md
│   │       └── Nginx.md
│   ├── Réseau et communications
│   │   ├── Diagnostic réseau ✅.md
│   │   ├── Firewall.md
│   │   ├── NAT-PAT.md
│   │   ├── Paramètres réseaux ✅.md
│   │   └── Routage ✅.md
│   ├── Sauvegarde et archivage
│   │   ├── Amanda.md
│   │   ├── Archivage.md
│   │   ├── Bacula.md
│   │   ├── Dump-Restore.md
│   │   └── Rsync.md
│   ├── Sécurité
│   │   ├── Firewalls.md
│   │   ├── Gestion des ports.md
│   │   └── Monitoring.md
│   └── Système de fichiers
│       ├── Gestion de l'espace disque et quotas.md
│       ├── Gestion des périphériques.md
│       ├── Logical Volume Manager.md
│       └── Types de systèmes de fichiers.md
├── Microsoft
│   ├── Active Directory
│   │   ├── AD.md
│   │   ├── Kerberos.md
│   │   ├── LDAP.md
│   │   └── NTLM.md
│   ├── Gestion des mises à jours & déploiement
│   │   ├── MDT.md
│   │   ├── SCCM.md
│   │   ├── Windows Installer.md
│   │   └── WSUS.md
│   ├── Gestion de stratégies
│   │   └── Group Policy.md
│   ├── Gestion de surveillance
│   │   ├── Event Viewer.md
│   │   ├── Nagios.md
│   │   ├── Performance Monitor.md
│   │   ├── SCCM.md
│   │   ├── SCOM.md
│   │   └── SolarWinds.md
│   ├── Journalisation
│   │   ├── Event Viewer.md
│   │   ├── Graylog.md
│   │   └── Splunk.md
│   ├── Sauvegarde et reprise
│   │   ├── Azure Backup.md
│   │   ├── Veeam.md
│   │   └── Windows Server Backup.md
│   ├── Service base de données
│   │   └── Microsoft SQL Server.md
│   ├── Service d'annuaire
│   │   ├── AD CS.md
│   │   ├── AD DS.md
│   │   ├── AD FS.md
│   │   └── AD LDS.md
│   ├── Service Messagerie
│   │   └── Exchange Server.md
│   ├── Services de fichiers et stockage
│   │   ├── DFS.md
│   │   ├── Fibre Channel.md
│   │   ├── iSCSI.md
│   │   └── Storage Spaces.md
│   ├── Services réseau
│   │   ├── Gestion des accès distants
│   │   │   ├── DirectAccess.md
│   │   │   ├── RDP.md
│   │   │   ├── RDS.md
│   │   │   ├── RRAS.md
│   │   │   └── VPN.md
│   │   └── Gestion d'IP
│   │       ├── DNS-DHCP.md
│   │       └── IPAM.md
│   ├── Service Web
│   │   └── IIS.md
│   ├── Systèmes d'exploitation
│   │   ├── Windows client.md
│   │   └── Windows Server.md
│   └── Virtualisation
│       ├── Hyper-V.md
│       └── VMware.md
├── README.md
└── Réseaux
    ├── Automatisation & Sauvegarde
    │   ├── Ansible.md
    │   ├── Jenkins.md
    │   ├── Puppet.md
    │   ├── Salt.md
    │   ├── SolarWinds.md
    │   ├── Terraform.md
    │   └── Veeam.md
    ├── Cloud Computing
    │   ├── CDN.md
    │   ├── Développement d'applications pour le cloud.md
    │   ├── Gestion des coûts et tarification.md
    │   ├── Gestion et orchestration de conteneurs.md
    │   ├── IaC.md
    │   ├── Migration vers le cloud.md
    │   ├── Modèles de services.md
    │   ├── Optimisation des performances.md
    │   ├── Outils et services spécifiques des fournisseurs de cloud.md
    │   ├── Récupération après sinistre et continuité des activités.md
    │   ├── Sécurité dans le cloud.md
    │   ├── Stockage dans le cloud.md
    │   ├── Stratégies de déploiement.md
    │   ├── Types de cloud.md
    │   └── Virtualisation.md
    ├── Fondamentaux du réseau
    │   ├── Architecture réseau et équipement ✅.md
    │   ├── Modèles de référence OSI ✅.md
    │   ├── Ports ✅.md
    │   └── Routage et commutation ✅.md
    ├── Protocoles
    │   ├── 1 - Physique
    │   │   ├── Cablage fibre.md
    │   │   ├── Câbles réseau ✅.md
    │   │   └── DSL.md
    │   ├── 2 - Liaison de données
    │   │   ├── EtherChannel ✅.md
    │   │   ├── Ethernet ✅.md
    │   │   ├── MAC ✅.md
    │   │   ├── PPP-HDLC ✅.md
    │   │   ├── STP ✅.md
    │   │   └── VLAN ✅.md
    │   ├── 3 - Réseau
    │   │   ├── Acheminement
    │   │   │   └── MPLS ✅.md
    │   │   ├── Controle
    │   │   │   └── ICMP ✅.md
    │   │   ├── Gestion d'adresse IP
    │   │   │   ├── ARP ✅.md
    │   │   │   ├── IGMP ✅.md
    │   │   │   ├── IPV4 ✅.md
    │   │   │   ├── IPV6 ✅.md
    │   │   │   ├── Localhost et Loopback ✅.md
    │   │   │   ├── Masque réseau ✅.md
    │   │   │   ├── NAT PAT ✅.md
    │   │   │   └── VLSM.md
    │   │   ├── MLS ✅.md
    │   │   ├── Routage
    │   │   │   ├── EGP
    │   │   │   │   └── BGP ✅.md
    │   │   │   ├── IGP
    │   │   │   │   ├── Etat de liaison
    │   │   │   │   │   ├── ISIS.md
    │   │   │   │   │   └── OSPF ✅.md
    │   │   │   │   └── Vecteurs de distance
    │   │   │   │       ├── EIGRP ✅.md
    │   │   │   │       └── RIP ✅.md
    │   │   │   ├── Redistribution de routes ✅.md
    │   │   │   ├── Routage dynamique ✅.md
    │   │   │   └── Routage statique ✅.md
    │   │   └── VRF ✅.md
    │   ├── 4 - Transport
    │   │   ├── RTP ✅.md
    │   │   ├── TCP ✅.md
    │   │   └── UDP ✅.md
    │   └── 5 - Application
    │       ├── Connexion
    │       │   ├── RDP ✅.md
    │       │   ├── SSH ✅.md
    │       │   ├── Telnet ✅.md
    │       │   └── VNC ✅.md
    │       ├── Gestion réseau
    │       │   ├── NTP ✅.md
    │       │   └── SNMP ✅.md
    │       ├── Liaison IP
    │       │   ├── DHCP ✅.md
    │       │   └── DNS ✅.md
    │       ├── Messagerie et communication
    │       │   ├── MQTT ✅.md
    │       │   ├── SIP ✅.md
    │       │   ├── SMTP-IMAP-POP3 ✅.md
    │       │   └── XMPP ✅.md
    │       ├── Transferts de fichiers
    │       │   ├── FTP-FTPS-SFTP.md
    │       │   ├── FTP ✅.md
    │       │   ├── NFS ✅.md
    │       │   ├── NFS.md
    │       │   ├── SFTP ✅.md
    │       │   ├── SMB ✅.md
    │       │   └── SMB-SAMBA.md
    │       └── Web
    │           ├── HTTP-HTTPS ✅.md
    │           └── HTTP-HTTPS.md
    ├── Sans fil
    │   ├── 5G ✅.md
    │   ├── Bluetooth ✅.md
    │   ├── NFC ✅.md
    │   ├── RCS ✅.md
    │   ├── RFID ✅.md
    │   └── Wifi ✅.md
    └── Sécurité réseau
        ├── Authentification
        │   ├── 802.1X ✅.md
        │   ├── Kerberos ✅.md
        │   ├── LDAP ✅.md
        │   ├── RADIUS ✅.md
        │   ├── SSO ✅.md
        │   └── TACACS+ ✅.md
        ├── Contrôle d'accès
        │   ├── ACL ✅.md
        │   ├── NAC ✅.md
        │   ├── Port Security ✅.md
        │   └── RBAC ✅.md
        ├── Cryptographie
        │   ├── Chiffrement et certificats ✅.md
        │   └── PKI ✅.md
        ├── Equipements
        │   ├── Firewall ✅.md
        │   ├── IDS IPS ✅.md
        │   ├── Proxy ✅.md
        │   ├── VPN ✅.md
        │   ├── WAF ✅.md
        │   └── ZBF.md
        └── Protocoles de sécurité
            ├── IPsec ✅.md
            └── TLS ✅.md
```