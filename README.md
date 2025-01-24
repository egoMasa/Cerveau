# Présentation 

🎯 Cette section est destinée à de l'apprentissage. et à pour but de résumer et répertorier toutes les notions et concepts abordé lors de mes études en cybersécurité, que ce soit en réseau avec de la configuration Cisco, du pentesting ou de l'administration système 

🗂 Toutes les notions sont triés par sections en fonction de leur intérêt et de leur famille, ci-dessous l'arborescence actuelle 

✅ Les leçons avec cette marque sont considérés comme partiellement complet, certaines modifications pourront être apportés.
# Sommaire 
```
.  
├── Cybersécurité  
│   ├── Défensif  
│   │   ├── SOC.md  
│   │   └── ThreatHunting.md  
│   ├── Forensic  
│   │   └── Stéganographie.md  
│   ├── Gouvernance  
│   │   ├── Analyse de risques EBIOS  
│   │   │   ├── Guides officiels ANSSI  
│   │   │   │   ├── Fiches-EBIOS-ANSSI.pdf  
│   │   │   │   └── Guide-EBIOS-ANSSI.pdf  
│   │   │   ├── Méthodologie EBIOS RM.md  
│   │   │   └── Template EBIOS RM  
│   │   │       ├── 0 - Document réponse analyse de risques.odt  
│   │   │       ├── 1 - Etude de risques EBIOS.doc  
│   │   │       ├── Liste-EBIOS.ods  
│   │   │       └── Mesures de sécurité  
│   │   │           ├── Mesures ANSSI.ods  
│   │   │           └── Mesures ISO27002.ods  
│   │   ├── Homologation  
│   │   │   ├── Aides et ressources externes  
│   │   │   │   ├── Guide ANSSI  
│   │   │   │   │   ├── 1 - Etapes de l'homologation.pdf  
│   │   │   │   │   └── 2  - Structure du dossier.pdf  
│   │   │   │   └── Mesures de sécurité  
│   │   │   │       ├── Mesures ANSSI.ods  
│   │   │   │       └── Mesures ISO27002.ods  
│   │   │   ├── Documents réponses  
│   │   │   │   ├── 0 - Liste documentation et informations.ods  
│   │   │   │   ├── 1 - Document réponse stratégie homologation.odt  
│   │   │   │   ├── 2 - Document réponse analyse de risques.odt  
│   │   │   │   ├── 3 - Document réponse PES.odt  
│   │   │   │   └── 4 - Document réponse socle de sécurité.ods  
│   │   │   ├── Dossier d'homologation template  
│   │   │   │   ├── 0 - Evaluation-de-la-demarche-dhomologation.xls  
│   │   │   │   ├── 1 - Stratégie-Homologation.doc  
│   │   │   │   ├── 2 - Etude de risques EBIOS rapide.doc  
│   │   │   │   ├── 3 - Procédures-exploitation-sécurité(PES).odt  
│   │   │   │   ├── 5 - Rapport-audit.odt  
│   │   │   │   ├── 6 - Avis-commission-homologation.doc  
│   │   │   │   └── 7 - Décision-homologation.doc  
│   │   │   ├── Guide d'homologation pour les équipes.md  
│   │   │   └── Méthodologie d'homologation.md  
│   │   ├── NIS2  
│   │   │   └── NIS2.md  
│   │   ├── Normes ISO 27001.md  
│   │   └── RGPD  
│   │       ├── Ateliers  
│   │       │   └── CNIL.md  
│   │       └── Fiche registre  
│   │           └── Template fiche registre.md  
│   └── Offensif  
│       ├── Pentesting  
│       │   ├── 1 - Reconnaissance  
│       │   │   ├── Active (scan)  
│       │   │   │   ├── Active Directory  
│       │   │   │   │   └── BloodHound.md  
│       │   │   │   ├── Enumération web  
│       │   │   │   │   ├── Dirb.md  
│       │   │   │   │   ├── Dirbuster.md  
│       │   │   │   │   ├── FFUF.md  
│       │   │   │   │   ├── Gobuster.md  
│       │   │   │   │   └── Wappalyser.md  
│       │   │   │   ├── Méthodologie reconnaissance active.md  
│       │   │   │   ├── Nom de domaine  
│       │   │   │   │   ├── Dnsenum.md  
│       │   │   │   │   └── Dnsrecon.md  
│       │   │   │   ├── Partage de fichiers  
│       │   │   │   │   ├── Enum4Linux (Samba).md  
│       │   │   │   │   ├── NFS-common.md  
│       │   │   │   │   ├── Rpcclient.md  
│       │   │   │   │   └── Smbclient.md  
│       │   │   │   └── Réseau & Hôte  
│       │   │   │       ├── Masscan.md  
│       │   │   │       ├── Netcat.md  
│       │   │   │       └── Nmap.md  
│       │   │   └── Passive (OSINT)  
│       │   │       ├── Exploration générale  
│       │   │       │   ├── Censys.md  
│       │   │       │   ├── Shodan.md  
│       │   │       │   └── ZoomEye.md  
│       │   │       ├── Méthodologie reconnaissance passive.md  
│       │   │       ├── Nom de domaine & WHOIS  
│       │   │       │   ├── Amass.md  
│       │   │       │   ├── Dnsdumpster.md  
│       │   │       │   ├── Recon-ng.md  
│       │   │       │   ├── Sublist3r.md  
│       │   │       │   └── Whois.md  
│       │   │       └── Réseaux sociaux & emails  
│       │   │           ├── Holehe.md  
│       │   │           ├── Pimeyes.md  
│       │   │           ├── Sherlock.md  
│       │   │           └── TheHarvester.md  
│       │   ├── 2 - Détection de vulnérabilités  
│       │   │   ├── Active Directory  
│       │   │   │   ├── Méthodologie AD.md  
│       │   │   │   └── Outils  
│       │   │   │       └── Impacket.md  
│       │   │   ├── Méthodologie de détection générale.md  
│       │   │   ├── Scanners & Outils  
│       │   │   │   ├── Nessus.md  
│       │   │   │   ├── NSE Script.md  
│       │   │   │   ├── Nuclei.md  
│       │   │   │   ├── OpenVAS.md  
│       │   │   │   └── ZAP.md  
│       │   │   └── Web  
│       │   │       ├── Méthodologie application web.md  
│       │   │       └── Outils  
│       │   │           ├── BurpSuite.md  
│       │   │           ├── Nikto.md  
│       │   │           └── WPScan.md  
│       │   ├── 3 - Exploitation de vulnérabilités  
│       │   │   ├── Méthodologie d'exploitation générale.md  
│       │   │   └── Outils  
│       │   │       ├── Hydra.md  
│       │   │       ├── Metasploit.md  
│       │   │       ├── Searchsploit.md  
│       │   │       └── SQLMap.md  
│       │   ├── 3 - PrivEsc  
│       │   │   ├── Linux.md  
│       │   │   └── Windows.md  
│       │   ├── 4 - Latéralisation & persistance  
│       │   │   └── Test.md  
│       │   ├── 5 - Rapport d'intrusion & audit  
│       │   │   └── Test.md  
│       │   └── Techniques diverses CTF.md  
│       ├── RedTeam  
│       │   └── Phising  
│       │       └── Test.md  
│       └── Théorie  
│           ├── OWASP.md  
│           └── Vecteurs d'attaques.md  
├── Linux  
│   ├── Administration système  
│   │   ├── Configuration générale.md  
│   │   ├── Fichiers log ✅.md  
│   │   ├── Gestion des droits ✅.md  
│   │   ├── Gestionnaire d'installation ✅.md  
│   │   └── Utilisateurs et groupes ✅.md  
│   ├── Architecture linux  
│   │   ├── Boots et processus d'initialisation ✅.md  
│   │   ├── Différentes distributions ✅.md  
│   │   ├── Kernel (noyau) ✅.md  
│   │   ├── Linux-GNU (OS).md  
│   │   └── Shells ✅.md  
│   ├── Automatisation et supervision  
│   │   ├── Ansible.md  
│   │   ├── Bash.md  
│   │   ├── Crontab.md  
│   │   ├── Grafana.md  
│   │   ├── Icinga.md  
│   │   └── Zabbix.md  
│   ├── Configuration de services  
│   │   ├── Accès à distance  
│   │   │   ├── RDP.md  
│   │   │   ├── SSH.md  
│   │   │   ├── Telnet.md  
│   │   │   └── VNC.md  
│   │   ├── Authentification  
│   │   │   ├── FreeRADIUS.md  
│   │   │   ├── MIT Kerberos.md  
│   │   │   └── OpenLDAP.md  
│   │   ├── Base de données  
│   │   │   ├── MongoDB (NoSQL).md  
│   │   │   ├── MySQL.md  
│   │   │   ├── Oracle Database.md  
│   │   │   ├── PostgreSQL.md  
│   │   │   └── Redis.md  
│   │   ├── DNS-DHCP  
│   │   │   └── dnsmasq.md  
│   │   ├── Mails  
│   │   │   ├── Evolution.md  
│   │   │   ├── Kmail.md  
│   │   │   └── Thunderbird.md  
│   │   ├── Partage de fichiers  
│   │   │   ├── FTP-FTPS-SFTP ✅.md  
│   │   │   ├── NFS.md  
│   │   │   ├── SCP.md  
│   │   │   └── SMB-SAMBA ✅.md  
│   │   ├── Proxy  
│   │   │   ├── NGINX.md  
│   │   │   └── Squid.md  
│   │   ├── Sauvegarde et stockage  
│   │   │   └── RSYNC.md  
│   │   ├── Téléphonie  
│   │   │   └── Asterisk.md  
│   │   ├── Virtualisation  
│   │   │   ├── Docker.md  
│   │   │   ├── KVM.md  
│   │   │   └── QEMU.md  
│   │   ├── VPN  
│   │   │   ├── OpenVPN.md  
│   │   │   └── WireGuard.md  
│   │   └── Web  
│   │       ├── Apache.md  
│   │       └── Nginx.md  
│   ├── Git.md  
│   ├── Réseau et communications  
│   │   ├── Diagnostic réseau ✅.md  
│   │   ├── Firewall.md  
│   │   ├── NAT-PAT.md  
│   │   ├── Paramètres réseaux ✅.md  
│   │   └── Routage ✅.md  
│   ├── Sauvegarde et archivage  
│   │   ├── Amanda.md  
│   │   ├── Archivage.md  
│   │   ├── Bacula.md  
│   │   ├── Dump-Restore.md  
│   │   ├── Git.md  
│   │   └── Rsync.md  
│   ├── Sécurité  
│   │   ├── Firewalls.md  
│   │   ├── Gestion des ports.md  
│   │   └── Monitoring.md  
│   └── Système de fichiers  
│       ├── Gestion de l'espace disque et quotas.md  
│       ├── Gestion des périphériques.md  
│       ├── Logical Volume Manager.md  
│       └── Types de systèmes de fichiers.md  
├── Microsoft  
│   ├── Active Directory  
│   │   ├── Active Directory.md  
│   │   ├── Kerberos.md  
│   │   ├── LDAP.md  
│   │   └── NTLM.md  
│   ├── Gestion des mises à jours & déploiement  
│   │   ├── MDT.md  
│   │   ├── SCCM.md  
│   │   ├── Windows Installer.md  
│   │   └── WSUS.md  
│   ├── Gestion de stratégies  
│   │   └── Group Policy.md  
│   ├── Gestion de surveillance  
│   │   ├── Event Viewer.md  
│   │   ├── Nagios.md  
│   │   ├── Performance Monitor.md  
│   │   ├── SCCM.md  
│   │   ├── SCOM.md  
│   │   └── SolarWinds.md  
│   ├── Journalisation  
│   │   ├── Event Viewer.md  
│   │   ├── Graylog.md  
│   │   └── Splunk.md  
│   ├── Sauvegarde et reprise  
│   │   ├── Azure Backup.md  
│   │   ├── Veeam.md  
│   │   └── Windows Server Backup.md  
│   ├── Service base de données  
│   │   └── Microsoft SQL Server.md  
│   ├── Service Messagerie  
│   │   └── Exchange Server.md  
│   ├── Services de fichiers et stockage  
│   │   ├── DFS.md  
│   │   ├── Fibre Channel.md  
│   │   ├── iSCSI.md  
│   │   └── Storage Spaces.md  
│   ├── Services réseau  
│   │   ├── Gestion des accès distants  
│   │   │   ├── DirectAccess.md  
│   │   │   ├── RDP.md  
│   │   │   ├── RDS.md  
│   │   │   ├── RRAS.md  
│   │   │   └── VPN.md  
│   │   └── Gestion d'IP  
│   │       ├── DNS-DHCP.md  
│   │       └── IPAM.md  
│   ├── Service Web  
│   │   └── IIS.md  
│   └── Virtualisation  
│       ├── Hyper-V.md  
│       └── VMware.md  
├── Programmation  
│   ├── Assembleur.md  
│   ├── C++.md  
│   └── Python.md  
├── README.md  
└── Réseaux  
   ├── Automatisation & Sauvegarde  
   │   ├── Ansible.md  
   │   ├── Jenkins.md  
   │   ├── Puppet.md  
   │   ├── Salt.md  
   │   ├── SolarWinds.md  
   │   ├── Terraform.md  
   │   └── Veeam.md  
   ├── Cloud  
   │   └── Service Cloud  
   │       └── Amazon Web Service  
   │           └── AWS.md  
   ├── Conception réseau d'entreprise.md  
   ├── Fondamentaux du réseau  
   │   ├── Architecture réseau et équipement ✅.md  
   │   ├── Modèles de référence OSI ✅.md  
   │   ├── Ports ✅.md  
   │   └── Routage et commutation ✅.md  
   ├── Protocoles  
   │   ├── 1 - Physique  
   │   │   ├── Cablage fibre.md  
   │   │   ├── Câbles réseau ✅.md  
   │   │   └── DSL.md  
   │   ├── 2 - Liaison de données  
   │   │   ├── EtherChannel ✅.md  
   │   │   ├── Ethernet ✅.md  
   │   │   ├── MAC ✅.md  
   │   │   ├── PPP-HDLC ✅.md  
   │   │   ├── STP ✅.md  
   │   │   └── VLAN ✅.md  
   │   ├── 3 - Réseau  
   │   │   ├── Acheminement  
   │   │   │   ├── GRE ✅.md  
   │   │   │   └── MPLS ✅.md  
   │   │   ├── Controle  
   │   │   │   └── ICMP ✅.md  
   │   │   ├── Gestion d'adresse IP  
   │   │   │   ├── ARP ✅.md  
   │   │   │   ├── Calcul reseau.md  
   │   │   │   ├── IGMP ✅.md  
   │   │   │   ├── IPV4 ✅.md  
   │   │   │   ├── IPV6 ✅.md  
   │   │   │   ├── Localhost et Loopback ✅.md  
   │   │   │   ├── Masque réseau ✅.md  
   │   │   │   └── NAT PAT ✅.md  
   │   │   ├── MLS ✅.md  
   │   │   ├── Routage  
   │   │   │   ├── EGP  
   │   │   │   │   └── BGP ✅.md  
   │   │   │   ├── IGP  
   │   │   │   │   ├── Etat de liaison  
   │   │   │   │   │   ├── ISIS.md  
   │   │   │   │   │   └── OSPF ✅.md  
   │   │   │   │   └── Vecteurs de distance  
   │   │   │   │       ├── EIGRP ✅.md  
   │   │   │   │       └── RIP ✅.md  
   │   │   │   ├── Redistribution de routes ✅.md  
   │   │   │   ├── Routage dynamique ✅.md  
   │   │   │   └── Routage statique ✅.md  
   │   │   ├── VRF ✅.md  
   │   │   └── VXLAN.md  
   │   ├── 4 - Transport  
   │   │   ├── RTP ✅.md  
   │   │   ├── TCP ✅.md  
   │   │   └── UDP ✅.md  
   │   └── 5 - Application  
   │       ├── Connexion  
   │       │   ├── RDP ✅.md  
   │       │   ├── SSH ✅.md  
   │       │   ├── Telnet ✅.md  
   │       │   └── VNC ✅.md  
   │       ├── Gestion réseau  
   │       │   ├── NTP ✅.md  
   │       │   └── SNMP ✅.md  
   │       ├── Liaison IP  
   │       │   ├── DHCP ✅.md  
   │       │   └── DNS ✅.md  
   │       ├── Messagerie et communication  
   │       │   ├── MQTT ✅.md  
   │       │   ├── SIP ✅.md  
   │       │   ├── SMTP-IMAP-POP3 ✅.md  
   │       │   └── XMPP ✅.md  
   │       ├── Transferts de fichiers  
   │       │   ├── FTP-FTPS-SFTP.md  
   │       │   ├── FTP ✅.md  
   │       │   ├── NFS ✅.md  
   │       │   ├── NFS.md  
   │       │   ├── SFTP ✅.md  
   │       │   ├── SMB ✅.md  
   │       │   └── SMB-SAMBA.md  
   │       └── Web  
   │           ├── HTTP-HTTPS ✅.md  
   │           └── HTTP-HTTPS.md  
   ├── QoS ✅.md  
   ├── Sans fil  
   │   ├── 5G ✅.md  
   │   ├── Bluetooth ✅.md  
   │   ├── NFC ✅.md  
   │   ├── RCS ✅.md  
   │   ├── RFID ✅.md  
   │   └── WLAN ✅.md  
   ├── Sécurité réseau  
   │   ├── Authentification  
   │   │   ├── 802.1X ✅.md  
   │   │   ├── Kerberos ✅.md  
   │   │   ├── LDAP ✅.md  
   │   │   ├── RADIUS ✅.md  
   │   │   ├── SSO ✅.md  
   │   │   └── TACACS+ ✅.md  
   │   ├── Contrôle d'accès  
   │   │   ├── ACL ✅.md  
   │   │   ├── NAC ✅.md  
   │   │   ├── Port Security ✅.md  
   │   │   └── RBAC ✅.md  
   │   ├── Cryptographie  
   │   │   ├── Chiffrement et certificats ✅.md  
   │   │   ├── Cryptographie.md  
   │   │   └── PKI ✅.md  
   │   ├── Equipements  
   │   │   ├── Firewall ✅.md  
   │   │   ├── IDS IPS ✅.md  
   │   │   ├── Proxy ✅.md  
   │   │   ├── VPN ✅.md  
   │   │   ├── WAF ✅.md  
   │   │   └── ZBF.md  
   │   └── Protocoles de sécurité  
   │       ├── IKE et IPsec ✅.md  
   │       └── TLS ✅.md  
   └── VoIP ✅.md
```