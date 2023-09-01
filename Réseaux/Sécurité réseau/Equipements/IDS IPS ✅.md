# Guide IDS/IPS

# **1. C'est quoi un IDS/IPS :**

- **IDS** : L'IDS, ou Système de Détection d'Intrusion (Intrusion Detection System en anglais), est un dispositif ou un logiciel qui surveille le trafic réseau à la recherche d'activités suspectes ou malveillantes. Lorsqu'il détecte une telle activité, il génère des alertes pour informer les administrateurs.

- **IPS** : L'IPS, ou Système de Prévention d'Intrusion (Intrusion Prevention System en anglais), est similaire à l'IDS, mais va plus loin : il est capable non seulement de détecter des activités malveillantes, mais aussi de les bloquer en temps réel pour empêcher une intrusion ou une attaque.

# **2. C'est quoi le but et l'intérêt d'un IDS/IPS :**

- **Détecter et alerter** : L'IDS est principalement utilisé pour surveiller le trafic, détecter des activités anormales ou malveillantes et alerter les responsables. Sa mission est de "voir" et "informer".

- **Bloquer les menaces en temps réel** : L'IPS est conçu pour non seulement détecter, mais aussi prendre des mesures proactives pour stopper les menaces avant qu'elles ne puissent causer des dommages.

- **Amélioration de la sécurité** : Les IDS/IPS offrent une couche supplémentaire de sécurité, protégeant contre les menaces connues et inconnues.

- **Conformité** : Pour certaines industries ou normes, avoir un IDS/IPS en place est une exigence pour la conformité réglementaire.

# **3. Quels sont les cas courants d'utilisation d'un IDS/IPS :**

- **Protection des ressources critiques** : Les IDS/IPS sont souvent déployés devant des serveurs ou des bases de données critiques pour garantir qu'aucune activité malveillante n'y parvient.

- **Surveillance du trafic en bordure de réseau** : Pour protéger un réseau d'entreprise, les IDS/IPS peuvent être placés à la périphérie, juste derrière les pare-feux, pour surveiller tout le trafic entrant et sortant.

- **Détection des comportements anormaux** : Les IDS/IPS peuvent identifier les comportements réseau qui sortent de l'ordinaire, comme une grande quantité de trafic en provenance d'une seule source ou des motifs d'attaque connus.

- **Mise en conformité** : Pour les entreprises qui doivent se conformer à des normes spécifiques comme le PCI DSS, le déploiement d'un IDS/IPS peut être une exigence.

- **Environnements cloud** : Avec la montée des infrastructures cloud, les IDS/IPS sont également utilisés pour surveiller et protéger le trafic dans ces environnements.

*Comparaison simple* : Pensez à l'IDS comme une caméra de sécurité dans une banque qui surveille en permanence et déclenche une alarme si un voleur est repéré. L'IPS, quant à lui, serait comme une porte de sécurité qui se ferme automatiquement lorsque quelqu'un essaie d'entrer sans autorisation.


# **4. Quels sont les éléments d'un IDS/IPS :**

- **Capteurs/Agents** : Ils sont déployés à des points stratégiques du réseau pour collecter les données de trafic. Ils analysent ces données en temps réel pour détecter des signes d'activité malveillante.

- **Console de gestion** : Interface centrale à partir de laquelle les administrateurs peuvent configurer les capteurs, mettre à jour les signatures, visualiser les alertes et générer des rapports.

- **Base de données** : Elle stocke des informations telles que les configurations, les signatures des attaques, les alertes et les journaux d'événements.

- **Moteur d'analyse** : Ce composant est chargé d'analyser les données du trafic réseau en utilisant des signatures d'attaque prédéfinies, des algorithmes d'apprentissage automatique ou une analyse heuristique pour détecter des activités suspectes.

- **Signature d'attaque** : Il s'agit d'un ensemble de règles qui définissent les caractéristiques spécifiques d'une attaque connue. Les IDS/IPS utilisent ces signatures pour identifier et (dans le cas de l'IPS) bloquer les activités malveillantes.

# **5. Quels sont les versions et les caractéristiques :**

- **IDS basé sur les signatures** : Il utilise une base de données de signatures pour reconnaître les menaces connues. La base de données doit être régulièrement mise à jour pour détecter de nouvelles menaces.

- **IDS basé sur les anomalies** : Au lieu de rechercher des signatures spécifiques, il surveille le trafic réseau pour détecter tout comportement qui s'écarte d'un "profil normal" établi.

- **IPS basé sur les signatures** : Tout comme l'IDS basé sur les signatures, mais avec la capacité supplémentaire de bloquer activement les menaces détectées en temps réel.

- **IDS/IPS basé sur le réseau (NIDS/NIPS)** : Surveille le trafic réseau global pour détecter et/ou bloquer les activités malveillantes.

- **IDS/IPS basé sur l'hôte (HIDS/HIPS)** : Installé sur un hôte ou un serveur spécifique pour surveiller les activités au niveau de cet hôte.

**Caractéristiques clés :**

- **Taux élevé de détection avec un minimum de faux positifs** : Un bon IDS/IPS doit être capable de détecter avec précision les menaces tout en minimisant les alertes inutiles.

- **Mises à jour régulières** : Les menaces évoluent constamment, il est donc essentiel que le système puisse se mettre à jour régulièrement avec de nouvelles signatures et des informations sur les menaces.

- **Intégration avec d'autres systèmes de sécurité** : Capacité à s'intégrer avec d'autres solutions comme les SIEM, les pare-feux, etc., pour une réponse plus coordonnée aux menaces.

- **Rapport détaillé et alerte en temps réel** : Fournit une analyse détaillée des incidents détectés et génère des alertes en temps réel pour une intervention rapide.

- **Adaptabilité** : Capacité à s'adapter à des environnements changeants et à apprendre des nouveaux comportements pour améliorer la détection.

*Comparaison simple* : Un IDS/IPS fonctionne un peu comme un système d'alarme sophistiqué dans un musée. Certains détecteurs (IDS basé sur les signatures) sonneront si quelqu'un essaye de briser une vitre en utilisant une méthode connue, tandis que d'autres détecteurs (IDS basé sur les anomalies) sonneront si quelqu'un se comporte simplement de manière suspecte dans le musée.

La fonctionnalité d'un IDS/IPS repose sur une analyse minutieuse du trafic réseau pour détecter et éventuellement bloquer des activités malveillantes. Voici un aperçu de leur fonctionnement et de la manière dont une communication se déroule lorsqu'un IDS/IPS est en place :

# **6. Fonctionnement technique d'un IDS/IPS :**

1. **Collecte de données** : Le capteur ou l'agent de l'IDS/IPS surveille le trafic réseau à un point stratégique, souvent à la frontière du réseau.

2. **Prétraitement** : Les paquets réseau capturés sont d'abord prétraités pour extraire les informations pertinentes nécessaires à l'analyse.

3. **Analyse du trafic** : Le moteur d'analyse compare ensuite le trafic à des signatures d'attaque prédéfinies ou à des profils d'activité normale. Deux principales méthodes d'analyse sont utilisées:
   - **Détection basée sur les signatures** : Comparaison du trafic avec une base de données de signatures pour identifier des menaces connues.
   - **Détection basée sur les anomalies** : Comparaison du trafic actuel avec un profil basé sur un comportement réseau "normal" préalablement établi.

4. **Déclenchement d'alertes** :
   - Si l'IDS détecte une menace potentielle, il génère une alerte pour informer les administrateurs.
   - Si c'est un IPS (et qu'il est configuré pour le faire), il peut également prendre des mesures pour bloquer le trafic malveillant ou suspect en temps réel.

5. **Rapports et analyses** : Les événements et les alertes sont enregistrés pour une analyse ultérieure. Les administrateurs peuvent examiner ces rapports pour identifier des tendances, effectuer des investigations approfondies ou améliorer la configuration de l'IDS/IPS.

# **7. Communication utilisant un IDS/IPS :**

1. Un utilisateur (ou un système) initie une communication réseau.

2. Le trafic passe par le capteur/agent de l'IDS/IPS.

3. L'IDS/IPS analyse le trafic en temps réel, cherchant des correspondances avec des signatures d'attaque ou des comportements anormaux.

4. Si aucune activité malveillante n'est détectée, le trafic continue normalement.

5. Si une menace est détectée :
   - L'IDS générera une alerte, permettant à l'administrateur d'enquêter sur l'incident.
   - Si c'est un IPS, il peut bloquer le paquet suspect ou la session de communication en fonction de sa configuration.

6. Les informations sur l'incident sont enregistrées pour référence et analyse ultérieure.

**Comparaison simple** : Pensez à un IDS/IPS comme à un portier à l'entrée d'une boîte de nuit. Ce portier regarde chaque personne (paquet) qui essaie d'entrer. S'il reconnaît quelqu'un (signature) sur la liste des personnes indésirables, ou si quelqu'un se comporte étrangement (anomalie), il alertera la sécurité ou refusera l'entrée à cette personne.
# 8. Quels sont les failles de sécurité utilisable par un attaquant pour bypass un IDS/IPS

Les systèmes IDS/IPS, malgré leur rôle essentiel dans la défense du réseau, ne sont pas infaillibles. Voici quelques méthodes que les attaquants peuvent utiliser pour les contourner :

1. **Évasion par fragmentation** : En fragmentant des paquets malveillants en segments plus petits, les attaquants espèrent que l'IDS/IPS ne reconstituera pas ou n'analysera pas correctement les paquets pour détecter l'attaque. Cela peut notamment être efficace contre les IDS basés sur les signatures.

2. **Polymorphisme et métamorphisme** : Les attaquants peuvent changer continuellement la signature de leurs malwares pour éviter la détection. C'est comme porter un déguisement différent chaque fois qu'on essaie de passer un garde.

3. **Tunnelling** : Encapsuler le trafic malveillant dans des protocoles couramment autorisés, comme ICMP ou DNS, pour le faire passer sans être détecté.

4. **Attaques basées sur l'heure** : Introduire un délai entre les paquets ou les attaques pour tenter de déjouer les IDS/IPS qui s'appuient sur la détection d'une certaine séquence d'événements en un temps donné.

5. **Utilisation du chiffrement** : Les IDS/IPS peuvent avoir du mal à inspecter le contenu chiffré, donc si le trafic malveillant est chiffré, il pourrait passer sans être détecté.

6. **Insertion et évasion** : En exploitant les différences entre la manière dont les hôtes TCP traitent les paquets et la manière dont l'IDS traite les paquets, les attaquants peuvent insérer des commandes dans une session TCP que l'IDS ne verra pas, mais la cible traitera.

7. **Attaques de saturation** : Inonder le système IDS/IPS avec un volume élevé de trafic pour le submerger, dans l'espoir qu'il ne pourra pas traiter tout le trafic ou qu'il manquera des attaques pendant la période d'encombrement.

8. **Fausses alertes** : Inonder l'IDS/IPS avec de fausses alertes pour distraire les responsables de la sécurité et potentiellement faire passer une vraie attaque inaperçue.

9. **Exploiter les vulnérabilités des IDS/IPS** : Comme tout autre logiciel, les IDS/IPS peuvent avoir des failles. Les attaquants peuvent les exploiter pour désactiver ou contourner le système.

Il est important de comprendre que bien que ces méthodes puissent permettre de contourner un IDS/IPS, elles ne garantissent pas nécessairement le succès d'une attaque. De plus, de nombreux fournisseurs d'IDS/IPS travaillent continuellement pour améliorer leurs produits et contrer ces techniques d'évasion.

# 9. Comment un attaquant peut-il détecter et savoir qu'il y a un IDS/IPS sur le réseau ?
Un attaquant peut utiliser plusieurs méthodes pour détecter la présence d'un IDS/IPS sur un réseau. Bien que ces méthodes ne garantissent pas toujours une détection précise, elles peuvent fournir des indices sur la présence d'un tel système de sécurité. Voici quelques méthodes couramment utilisées par les attaquants pour détecter la présence d'IDS/IPS :

1. **Scanning et observation du comportement** : En envoyant des paquets spécialement conçus sur le réseau et en observant les réponses, un attaquant peut identifier le comportement d'un IDS/IPS. Par exemple, si un paquet mal formé entraîne le blocage de l'adresse IP source, cela peut indiquer la présence d'un IPS.

2. **Analyse des temps de réponse** : Les systèmes IDS/IPS peuvent introduire des retards minimes lors de l'analyse du trafic. En mesurant le temps de réponse pour un certain nombre de paquets, un attaquant peut parfois détecter ces retards.

3. **Tests avec des signatures connues** : Un attaquant peut envoyer du trafic qui contient des signatures d'attaques connues mais inoffensives. Si le trafic est bloqué ou s'il y a une alerte, cela pourrait indiquer la présence d'un IDS/IPS.

4. **Recherche d'adresses IP suspectes** : Certains IDS/IPS utilisent des adresses IP pour envoyer des paquets de "reset" afin de terminer les connexions suspectes. En identifiant ces paquets, un attaquant peut suspecter la présence d'un IDS/IPS.

5. **Injection de TTL (Time to Live)** : En envoyant des paquets avec une valeur TTL faible qui s'incrémente progressivement, un attaquant peut observer à quel moment les paquets sont bloqués ou modifiés. Cela peut aider à localiser la position d'un IDS/IPS sur le chemin du réseau.

6. **Observation des refus de connexion** : Si un attaquant essaie de se connecter à un grand nombre de ports et qu'il observe un nombre anormalement élevé de refus ou de réinitialisations, cela peut indiquer la présence d'un IPS qui bloque les scans de ports.

7. **Écoute passive** : En écoutant passivement le trafic sur un réseau, un attaquant peut parfois détecter des motifs ou des anomalies qui indiquent des opérations d'IDS/IPS, comme des paquets de requête ou des mises à jour de signatures.

8. **Analyse des en-têtes** : Certains IDS/IPS peuvent modifier ou insérer des en-têtes spécifiques dans les paquets qu'ils inspectent. En examinant ces en-têtes, un attaquant peut parfois identifier la présence d'un système de sécurité.

Il est important de noter que la détection d'un IDS/IPS dépend de sa configuration, de son mode de fonctionnement (par exemple, en mode transparent ou en mode en ligne) et des autres dispositifs de sécurité en place. De nombreux administrateurs réseau utilisent également des "pot de miel" (honeypots) ou des "réseaux leurre" (honeynets) pour tromper et détecter les attaquants, rendant ainsi la détection et la distinction entre les vrais systèmes de sécurité et les leurres encore plus difficile pour l'attaquant.