# Guide NTP

La synchronisation du temps est un élément essentiel des systèmes informatiques. Le protocole NTP est au cœur de cette synchronisation. Il garantit que l'ensemble des équipements d'un réseau maintiennent une horloge commune. Ceci est essentiel pour la sécurité, mais également pour le bon fonctionnement de nombreuses applications et protocoles.

### **Importance du NTP dans la cybersécurité**

- **Authentification** : Des protocoles comme Kerberos dépendent d'une horloge précise pour l'authentification. Les différences de temps peuvent provoquer des échecs d'authentification.
    
- **Journalisation et audit** : Pour retracer et comprendre les incidents de sécurité, les horodatages précis sont essentiels. Une horloge décalée peut compliquer la détection des activités malveillantes.
    
- **Signatures numériques** : Les signatures numériques utilisent souvent un horodatage pour indiquer quand un document a été signé. Une synchronisation exacte est essentielle pour garantir l'intégrité des signatures.
    

### **Fonctions principales du NTP**

- **Synchronisation d'horloge** : NTP coordonne les horloges de tous les appareils d'un réseau, les synchronisant avec une source de temps de référence.
    
- **Hiérarchie Stratum** : NTP utilise un système hiérarchique pour maintenir la précision. Les serveurs d'un niveau supérieur fournissent le temps aux serveurs d'un niveau inférieur, qui à leur tour synchronisent les horloges des clients.
    
- **Interrogation** : Les clients NTP interrogent régulièrement leurs serveurs NTP pour ajuster leurs horloges en fonction de l'information reçue.
    

### **Risques de sécurité et meilleures pratiques avec NTP**

- **Attaques de réflexion/amplification NTP** : Ces attaques DDoS exploitent les serveurs NTP mal configurés. Pour limiter ce risque, assurez-vous que votre serveur NTP est correctement configuré.
    
- **Falsification du temps** : Les attaquants peuvent manipuler le trafic NTP pour modifier l'heure sur les appareils clients. L'utilisation de clés d'authentification avec NTP garantit l'intégrité des mises à jour temporelles.
    
- **Serveurs non fiables** : Il est essentiel d'obtenir le temps d'une source fiable. Configurez toujours les clients pour utiliser des serveurs NTP de confiance.
    
## Configuration Cisco 

- Activer NTP
```
ntp server @ip_serveur
```

- Vérifier la liaison
```
sh ntp status
sh clock detail
```
### **Conclusion**

L'utilisation de NTP est cruciale pour garantir la sécurité et l'efficacité d'un réseau. Comprendre son fonctionnement et ses implications en matière de sécurité permet de renforcer la posture de sécurité globale de votre réseau.