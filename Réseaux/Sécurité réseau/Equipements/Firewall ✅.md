# Guide Firewall 

# **1. C'est quoi un firewall?**
Un firewall, ou pare-feu en français, est un dispositif ou un logiciel qui surveille et contrôle le trafic réseau entrant et sortant sur la base de règles de sécurité prédéfinies. Il sert de barrière entre un réseau interne sécurisé et un autre réseau, généralement Internet, qui est considéré comme non sécurisé.

# **2. C'est quoi le but et l'intérêt d'un firewall?**
Le principal objectif d'un firewall est de protéger les ressources informatiques d'un réseau d'attaques provenant d'un autre réseau (généralement Internet). Les intérêts principaux sont :

- **Sécurité** : Il empêche l'accès non autorisé aux systèmes depuis Internet et empêche les logiciels malveillants d'accéder au réseau interne.
- **Confidentialité** : En filtrant le trafic, il protège la confidentialité des données en s'assurant que seules les informations autorisées traversent le réseau.
- **Contrôle d'accès** : Les entreprises peuvent contrôler quelles applications ou services peuvent être accessibles depuis le réseau extérieur.
- **Enregistrement et reporting** : Les firewalls peuvent généralement enregistrer le trafic, permettant ainsi aux administrateurs de surveiller les tentatives d'accès, d'analyser les tendances et de repérer d'éventuelles anomalies ou attaques.

# **3. Quels sont les cas courants d'utilisation d'un firewall?**

- **Protection du réseau d'entreprise** : Les firewalls sont couramment utilisés pour protéger les réseaux d'entreprise contre les menaces extérieures, telles que les tentatives d'intrusion, les attaques par déni de service ou les logiciels malveillants.
  
- **Protection des appareils individuels** : Des firewalls logiciels peuvent être installés sur des ordinateurs individuels ou des smartphones pour protéger contre les menaces potentielles, surtout lorsqu'ils sont connectés à des réseaux publics ou non sécurisés.
  
- **VPN & accès distant** : Les firewalls sont souvent déployés avec des solutions VPN pour permettre un accès distant sécurisé aux employés tout en gardant les ressources de l'entreprise sécurisées.
  
- **Bridage du réseau** : Dans certains contextes, un firewall peut être utilisé pour bloquer l'accès à des sites spécifiques ou des services en ligne (par exemple, bloquer l'accès aux sites de médias sociaux ou aux plateformes de streaming).
  
- **Segmentation de réseau** : Dans les grands réseaux, des firewalls peuvent être utilisés pour séparer différents segments du réseau pour améliorer les performances et la sécurité. Par exemple, un réseau d'entreprise peut avoir un segment dédié aux ressources humaines et un autre aux développeurs, chacun protégé par des règles de firewall différentes.

En résumé, un firewall agit comme un gardien ou un point de contrôle entre les réseaux, permettant ou bloquant le trafic selon des règles prédéfinies pour assurer la sécurité et la performance du réseau.

# **4. Quels sont les éléments d'un Firewall:**

- **Règles de filtrage** : Ce sont des directives configurées par l'administrateur pour déterminer quel trafic est autorisé ou bloqué. Ces règles peuvent être basées sur des adresses IP, des ports, des protocoles, entre autres.

- **Table d'état** : Utilisée principalement par les firewalls dits "stateful", cette table conserve la trace des connexions actives et permet au firewall de comprendre le contexte de chaque paquet de données, pour savoir si celui-ci fait partie d'une connexion établie ou s'il s'agit d'une nouvelle tentative de connexion.

- **Interface réseau** : Il peut y avoir plusieurs interfaces sur un firewall, généralement dédiées aux zones (interne, externe, DMZ, etc.). Elles servent de points d'entrée ou de sortie pour le trafic réseau.

- **Zones de sécurité** : Des sections du réseau définies pour appliquer des politiques spécifiques. Par exemple, la DMZ (zone démilitarisée) est une zone couramment utilisée pour héberger des services accessibles depuis Internet, mais elle est séparée du réseau interne pour des raisons de sécurité.

- **Proxy/Application Layer Gateway** : Certains firewalls peuvent agir comme des intermédiaires, inspectant et filtrant le trafic au niveau de l'application, pas seulement au niveau du réseau ou du transport.

- **Moteur d'inspection profonde des paquets (DPI)** : Cette capacité permet à un firewall d'examiner en détail le contenu des paquets réseau pour identifier et bloquer des menaces potentielles.

- **Journal (Logs)** : Un élément essentiel pour la surveillance et l'audit, les logs enregistrent toutes les actions prises par le firewall, y compris le trafic autorisé, bloqué, et toute autre activité suspecte.

- **ALG (Application Level Gateway)** : Permet la personnalisation du traitement du trafic pour des applications spécifiques.

- **NAT (Network Address Translation)** : Fonctionnalité permettant de modifier les adresses IP source ou de destination des paquets qui traversent le firewall, couramment utilisé pour masquer des adresses IP internes.

En résumé, on peut imaginer le firewall comme un douanier à la frontière d'un pays. Les règles de filtrage sont les critères pour laisser passer ou non une personne (ou un paquet de données). La table d'état est le registre des personnes ayant déjà été contrôlées et autorisées. Les interfaces réseau sont les différents points de passage, et le journal est le registre des entrées et sorties.

# **5. Quels sont les versions et les caractéristiques d'un Firewall :**

1. **Firewall à la couche réseau (stateless)** :
   - **Comparaison** : Comme un videur à l'entrée d'un club qui vérifie uniquement si vous avez un billet, sans se soucier de qui vous êtes ou de ce que vous avez fait précédemment.
   - **Caractéristiques** : Il prend des décisions basées sur l'adresse source, l'adresse de destination, le port, et le protocole. N'a pas de mémoire du trafic précédent.

2. **Firewall à la couche réseau (stateful)** :
   - **Comparaison** : Comme un videur qui non seulement vérifie votre billet, mais se souvient aussi de vous d'une visite précédente.
   - **Caractéristiques** : Garde une trace des connexions actives et peut prendre des décisions basées sur le contexte de la session.

3. **Firewall d'application ou proxy** :
   - **Comparaison** : C'est comme un serveur dans un restaurant qui prend votre commande et la transmet en cuisine, s'assurant que vous obtenez exactement ce que vous avez commandé sans rien d'inattendu.
   - **Caractéristiques** : Inspecte le trafic au niveau de l'application, capable de comprendre des protocoles tels que HTTP, SMTP, etc., et peut prendre des décisions basées sur des critères spécifiques à ces protocoles.

4. **Firewall Next Generation (NGFW)** :
   - **Comparaison** : C'est comme un centre de sécurité avancé dans un aéroport qui non seulement scanne vos bagages, mais utilise également la technologie la plus récente pour détecter des menaces spécifiques et évaluer les intentions des passagers.
   - **Caractéristiques** : Intègre des fonctionnalités traditionnelles de firewall avec d'autres fonctionnalités comme l'inspection profonde de paquets (DPI), l'identification des applications, l'intégration IPS et parfois même un système de prévention des menaces avancées.

5. **Firewalls basés sur le cloud** :
   - **Comparaison** : Pensez-y comme à un service de sécurité à domicile que vous souscrivez, où le fournisseur surveille votre maison depuis un centre distant.
   - **Caractéristiques** : Ces firewalls sont hébergés dans le cloud et offrent des services de filtrage et de sécurité à l'échelle, souvent utilisés pour protéger des applications basées sur le cloud ou pour offrir des services à plusieurs sites.

En conclusion, si les firewalls étaient des gardiens, leurs versions et caractéristiques détermineraient comment ils vérifient et régulent le trafic, allant d'une simple vérification des billets à une évaluation approfondie et détaillée des intentions et du comportement.

# 6. **Comment fonctionne techniquement un firewall stateful**:

La façon dont un firewall (FW) fonctionne et établit une communication dépend de son type et de sa complexité. Pour simplifier, nous prendrons l'exemple d'un firewall stateful, qui est le type le plus couramment utilisé dans les entreprises aujourd'hui.

Un firewall stateful inspecte les paquets entrants et sortants et prend des décisions basées sur un ensemble de règles définies, ainsi que sur le contexte du trafic.

**Étapes de la communication utilisant un FW stateful** :

1. **Initialisation**:
    - Un client interne initie une demande de connexion vers un serveur externe (par exemple, une demande HTTP vers un site web).
    - Cette demande est un paquet SYN, marquant le début d'une connexion TCP.

2. **Inspection du paquet par le FW**:
    - Le FW inspecte le paquet SYN.
    - Il vérifie l'adresse IP source, l'adresse IP de destination, le port source, et le port de destination par rapport à sa table de règles.
    
3. **Comparaison avec les règles du FW**:
    - Si une règle autorise le trafic de l'IP source vers l'IP de destination sur le port spécifique, le FW laisse passer le paquet.
    - Sinon, le paquet est bloqué.

4. **Mise à jour de la table d'état**:
    - Si le paquet est autorisé, le FW ajoute cette connexion à sa table d'état. Cette table garde une trace de toutes les connexions actives.

5. **Réponse du serveur**:
    - Le serveur externe reçoit le paquet SYN, y répond par un paquet SYN-ACK, et le renvoie au client.

6. **Inspection de la réponse par le FW**:
    - Le FW inspecte le paquet SYN-ACK en vérifiant sa table d'état.
    - S'il voit que le client a initialement demandé cette connexion, il laisse passer le paquet SYN-ACK.

7. **Établissement complet de la connexion**:
    - Le client reçoit le paquet SYN-ACK et répond par un paquet ACK, finalisant ainsi l'établissement de la connexion TCP.

8. **Fin de la communication**:
    - Lorsque la session est terminée, que ce soit par le client ou le serveur, une fin de session est signalée, et le FW retire cette connexion de sa table d'état.

**Comparaison**: Imaginez une série d'échanges de lettres entre deux personnes via une poste centrale. Si la première personne (le client) envoie une lettre (le paquet SYN) demandant à établir une correspondance, la poste (le FW) vérifie si cette personne est autorisée à envoyer une lettre à la deuxième personne (le serveur). Si c'est le cas, la lettre est envoyée, sinon elle est retournée à l'expéditeur. Une fois que la deuxième personne répond (SYN-ACK), la poste vérifie à nouveau avant de livrer la lettre. Cette correspondance continue jusqu'à ce que l'une des deux personnes décide de mettre fin à l'échange.

# 8. Quels sont les failles de sécurité utilisable par un attaquant pour bypass un Firewall
Un IDS (Système de Détection d'Intrusion) et un IPS (Système de Prévention d'Intrusion) sont conçus pour identifier et, dans le cas de l'IPS, bloquer les activités malveillantes dans un réseau. Cependant, comme tous les systèmes, ils ont leurs faiblesses. Voici certaines méthodes qu'un attaquant pourrait utiliser pour les contourner :

1. **Fragmentation des paquets** : 
    - Les attaquants peuvent diviser des paquets malveillants en petits fragments. Si l'IDS/IPS ne reconstitue pas correctement ces fragments, il peut ne pas reconnaître l'attaque. 
    - **Comparaison**: C'est comme essayer de comprendre une phrase quand on n'entend qu'un mot à la fois, hors de contexte.

2. **Évasion à l'aide de l'encodage**:
    - L'utilisation d'encodage différent ou de techniques d'obfuscation peut cacher la véritable nature d'un paquet malveillant.
    - **Comparaison**: C'est comme écrire un message en code; si vous ne savez pas comment déchiffrer le code, le message semble inoffensif.

3. **Utilisation de protocoles non standard**:
    - Si un IDS/IPS est configuré pour surveiller uniquement certains protocoles, l'utilisation d'un protocole moins courant ou d'une application qui utilise des ports non standards peut permettre d'éviter la détection.
    - **Comparaison**: C'est comme avoir un garde qui ne parle que certaines langues; si vous parlez dans une langue qu'il ne comprend pas, il pourrait vous laisser passer.

4. **Attaques par inondation**:
    - En inondant un réseau de trafic, un attaquant peut tenter de submerger l'IDS/IPS, le rendant incapable d'analyser correctement tout le trafic.
    - **Comparaison**: C'est comme crier dans une pièce bondée; il est difficile de se concentrer sur une seule voix.

5. **Faibles configurations**:
    - Si un IDS/IPS est mal configuré, il peut ne pas détecter certaines attaques. Les attaquants peuvent exploiter ces lacunes.
    - **Comparaison**: Si une alarme est mal réglée, elle ne sonnera pas même si une porte ou une fenêtre est ouverte.

6. **Attaques "zero-day"**:
    - Ces attaques exploitent des vulnérabilités non connues ou non corrigées. Puisqu'elles sont inconnues, la plupart des IDS/IPS n'ont pas de signatures pour les détecter.
    - **Comparaison**: C'est comme essayer de préparer une défense contre une maladie dont on n'a jamais entendu parler.

7. **Insertion et évasion**:
    - Les attaquants peuvent insérer des paquets supplémentaires ou des séquences dans le trafic, espérant que le système cible traitera la séquence de manière différente de l'IDS/IPS.
    - **Comparaison**: C'est comme glisser un message secret dans une lettre plus longue, espérant que seul le destinataire le lira et comprendra.

Il est crucial pour les responsables de la sécurité de se tenir informés des nouvelles techniques d'évasion et de s'assurer que leurs systèmes IDS/IPS sont régulièrement mis à jour et correctement configurés.

# 9. Comment un attaquant peut-il détecter et savoir qu'il y a un Firewall sur le réseau ?
Un attaquant qui cherche à identifier la présence d'un pare-feu (Firewall) peut utiliser une variété de méthodes et de techniques. Voici certaines d'entre elles:

1. **Scans de ports**:
    - En balayant une plage de ports sur une cible, un attaquant peut déterminer quels ports sont ouverts, fermés ou filtrés. Si une grande majorité de ports répondent comme "filtrés", cela peut indiquer la présence d'un pare-feu qui bloque activement les tentatives de scan.
    - **Comparaison**: C'est comme vérifier chaque porte et fenêtre d'une maison pour voir lesquelles sont verrouillées.

2. **Ping (ICMP Echo)**:
    - Un attaquant peut envoyer une demande de ping à une cible. Si la cible ne répond pas, mais que d'autres signes montrent qu'elle est active, cela peut signifier qu'un pare-feu bloque les requêtes ICMP.
    - **Comparaison**: C'est comme crier le nom de quelqu'un à l'extérieur de sa maison et attendre de voir s'il répond.

3. **Tests d'évasion**:
    - En essayant différentes techniques d'évasion connues contre une cible, si certaines tentatives sont bloquées et d'autres réussissent, cela peut indiquer la présence d'un pare-feu qui utilise des signatures pour bloquer le trafic suspect.
    - **Comparaison**: C'est comme essayer de passer un garde en utilisant différents déguisements.

4. **Paquets mal formés**:
    - L'envoi de paquets mal formés ou non standard et l'observation des réponses peuvent aider à identifier la présence et parfois le type de pare-feu. Certains pare-feu répondent de manière unique à des paquets non conformes.
    - **Comparaison**: C'est comme envoyer une lettre avec une adresse étrange pour voir comment le destinataire réagit.

5. **Détection par l'effet secondaire**:
    - Certains pare-feu ont des effets secondaires lorsqu'ils traitent le trafic, tels que des délais ou des modifications de paquets. En observant ces effets, un attaquant peut déduire la présence d'un pare-feu.
    - **Comparaison**: C'est comme noter que quelqu'un regarde toujours par le judas avant d'ouvrir la porte.

6. **Recherche d'informations publiques**:
    - Les attaquants peuvent rechercher des informations sur la cible, comme des avis de sécurité ou des articles de blogs. Les mentions d'un pare-feu ou des spécificités de sa configuration peuvent être découvertes.
    - **Comparaison**: C'est comme lire un avis sur un magasin avant de le visiter pour savoir s'il y a un garde à l'entrée.

En déduisant la présence d'un pare-feu, les attaquants peuvent alors adapter leurs méthodes et techniques pour contourner ou éviter cette défense. D'où l'importance pour les administrateurs réseaux d'avoir une approche en couches de la sécurité, plutôt que de s'appuyer uniquement sur un pare-feu.