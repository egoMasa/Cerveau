# Guide SNMP

SNMP est un protocole centralisé conçu pour gérer et surveiller les dispositifs de réseau tels que les routeurs, les commutateurs et les serveurs. SNMP est largement utilisé dans les réseaux pour collecter des informations et configurer à distance des dispositifs. La compréhension du SNMP est essentielle pour tout administrateur réseau ou ingénieur.

### **Introduction au SNMP**

- **Définition** : SNMP, ou Simple Network Management Protocol, est un protocole standardisé utilisé pour surveiller et administrer des dispositifs de réseau et pour collecter des informations sur ces dispositifs à travers un réseau IP.
    
- **Versions** : SNMP a plusieurs versions, notamment SNMPv1, SNMPv2c et SNMPv3. SNMPv3 est actuellement la version la plus sécurisée, offrant des fonctionnalités d'authentification et de chiffrement.
    

### **Composants clés du SNMP**

1. **Agent SNMP** : Il s'agit d'un programme qui s'exécute sur les dispositifs de réseau. Il collecte et stocke des informations concernant le dispositif sur lequel il s'exécute.
    
2. **Gestionnaire SNMP (ou SNMP Manager)** : Il s'agit du système centralisé utilisé pour surveiller ou administrer des dispositifs SNMP. Il envoie des requêtes à l'agent et attend des réponses.
    
3. **MIB (Management Information Base)** : Une base de données hiérarchisée qui décrit les informations disponibles sur le dispositif. Elle est organisée en objets, chacun ayant un identifiant unique (par exemple, 1.3.6.1.4.1.9.2.1.58.0). Les MIB sont constituées de groupes standards, y compris IP, TCP, UDP, ICMP, AT, ISO, entre autres.
    
4. **Traps** : Les traps sont des notifications ou des alertes envoyées par un agent au gestionnaire en cas d'événement spécifique.
    

### **Fonctionnement du SNMP**

- Le gestionnaire envoie une requête SNMP à un dispositif.
- L'agent du dispositif reçoit la requête, récupère les informations nécessaires depuis la MIB, et renvoie une réponse au gestionnaire.
- **Protocole** : SNMP est une application non orientée connexion, ce qui signifie qu'elle n'établit pas de session permanente entre le client et le serveur. Il utilise UDP (User Datagram Protocol) pour ses communications.
- **Ports** : SNMP utilise principalement les ports 161 (pour les requêtes) et 162 (pour les traps).
- **Messages** :
	- **GET** : Utilisé pour récupérer la valeur des objets MIB à partir de l'agent.
	- **SET** : Utilisé pour définir ou modifier la valeur des objets MIB au niveau de l'agent.
	- **TRAP** : Utilisé par l'agent pour notifier le gestionnaire d'événements significatifs.
### **Versions du SNMP**

- **SNMPv1** : Première version avec une sécurité minimale basée sur des "community strings".
- **SNMPv2c** : Améliorations fonctionnelles par rapport à SNMPv1 avec des capacités de sécurité similaires.
- **SNMPv3** : Version la plus récente et la plus sécurisée, offrant des fonctionnalités d'authentification et de chiffrement.
    
### **Sécurité et Meilleures Pratiques**

1. **Utiliser SNMPv3** : En raison de ses mécanismes de sécurité renforcés.
2. **Modifier les community strings par défaut** : Évitez d'utiliser les "community strings" par défaut comme "public" ou "private".
3. **Restriction d'accès** : Utilisez des listes de contrôle d'accès pour limiter l'accès aux dispositifs SNMP.
4. **Surveillance** : Surveillez régulièrement les journaux SNMP pour toute activité suspecte.

## Configuration Cisco
### Agent 
La mise en place d'un agent SNMP nécessite de paramétrer correctement les équipements réseau afin qu'ils puissent communiquer avec le gestionnaire SNMP. Voici un résumé simplifié et corrigé des étapes à suivre :

1. **Configuration de Base** :
   - Chaque équipement réseau doit être configuré pour qu'il puisse répondre aux requêtes du gestionnaire SNMP.

2. **Spécification de l'identifiant de communauté** :
   - Pour la lecture seule (Agent) :
     ```
     snmp-server community [NOM_COMMUNAUTE] ro
     ```
   - Pour la lecture et écriture (Agent) :
     ```
     snmp-server community [NOM_COMMUNAUTE] rw
     ```

3. **Spécification de l'emplacement et du contact principal** :
   - Pour définir l'emplacement de l'équipement géré :
     ```
     snmp-server location [EMPLACEMENT]
     ```
   - Pour définir le contact principal de l'équipement :
     ```
     snmp-server contact [CONTACT]
     ```

4. **Configuration des syslogs** :
   - Activer la journalisation :
     ```
     logging on
     ```
   - Spécifier l'hôte ou l'IP pour l'envoi des journaux :
     ```
     logging [NOM_HOTE ou ADRESSE_IP]
     ```
   - Définir le service de journalisation :
     ```
     logging facility local7
     ```
   - Configurer le niveau de gravité des messages à capturer :
     ```
     logging trap informational
     ```
   - Spécifier l'interface à utiliser pour envoyer des messages syslog :
     ```
     logging source-interface loopback0
     ```
   - Activer les horodatages sur les messages de journal :
     ```
     logging timestamps log datetime
     ```
### Serveur 
Le gestionnaire SNMP est le composant central du système SNMP qui communique avec les agents SNMP pour surveiller ou gérer les équipements réseau.
- Obtenir valeur à partir de la MIB
```
snmp get {v1|v2c|v3} @ip_agent @communaute oid @oid_value
```
### **Conclusion**

SNMP est un outil précieux pour la gestion des réseaux. Toutefois, comme pour tout protocole ou outil, une compréhension approfondie, associée à une mise en œuvre sécurisée, est essentielle pour maximiser son efficacité tout en minimisant les risques potentiels.