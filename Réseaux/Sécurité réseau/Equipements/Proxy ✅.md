# Guide Proxy 

**Thème : Proxy**

# **1. C'est quoi un Proxy ?**

Un proxy, souvent appelé serveur proxy, agit comme un intermédiaire pour les demandes d'un client cherchant des ressources auprès d'autres serveurs. Le client se connecte au proxy, lequel transmet sa demande au serveur cible, reçoit la réponse du serveur, puis envoie cette réponse au client. Durant ce processus, le serveur cible ne communique jamais directement avec le client initial.

*Comparaison simple :* Pensez au proxy comme à un interprète entre deux personnes parlant des langues différentes. Plutôt que de parler directement, chaque personne communique avec l'interprète, qui traduit et transmet les messages entre elles.

# **2. C'est quoi le but et l'intérêt d'un Proxy ?**

Le proxy peut servir plusieurs objectifs :

- **Contrôle :** Les entreprises peuvent utiliser un proxy pour contrôler et surveiller l'accès à Internet des employés. Ils peuvent bloquer l'accès à des sites spécifiques ou à des types de contenu.

- **Performance :** Les proxies peuvent mettre en cache (stocker localement) les pages web populaires et fournir ces pages aux utilisateurs, réduisant le besoin d'aller chercher la page sur Internet chaque fois, ce qui améliore les temps de réponse.

- **Filtrage de contenu :** Un proxy peut être utilisé pour filtrer certains types de contenu, comme les publicités ou les scripts malveillants.

- **Confidentialité :** En masquant l'adresse IP réelle de l'utilisateur, un proxy peut offrir une certaine forme d'anonymat lors de la navigation sur le web.

- **Sécurité :** Un proxy peut être utilisé pour fournir une couche de sécurité supplémentaire en bloquant l'accès à des sites malveillants.

- **Transcodage :** Certains proxies sont utilisés pour adapter le contenu web pour un type de dispositif spécifique, comme un téléphone mobile.

- **Bypass de restrictions géographiques :** Un proxy situé dans une autre région ou pays peut être utilisé pour accéder à des contenus qui sont géo-restreints.

*Comparaison simple :* Imaginez un portier à l'entrée d'un club. Il décide qui peut entrer, note les allées et venues, peut donner des informations sur ce qui se passe à l'intérieur sans que vous ayez à entrer, et peut même vous dire de repasser plus tard si l'endroit est trop occupé.

# **3. Quels sont les cas courants d'utilisation d'un Proxy ?**

- **Proxy de filtrage web :** Utilisé par les écoles et les entreprises pour bloquer et filtrer l'accès à certains sites ou contenus.

- **Proxy inverse (reverse proxy) :** Positionné devant les serveurs web, il dirige les demandes des clients vers le serveur approprié, améliore la performance et la sécurité.

- **Proxy de cache :** Stocke localement les contenus fréquemment demandés pour améliorer les temps de réponse et réduire la bande passante.

- **Proxy anonymiseur :** Utilisé pour masquer l'adresse IP de l'utilisateur et ainsi naviguer anonymement.

- **Proxy de traduction :** Modifie le contenu pour s'adapter à des besoins spécifiques, comme traduire un site web.

- **Proxy de passage (tunneling) :** Transmet des communications sans les altérer, souvent utilisé pour le VPN.

- **Proxy de contournement :** Utilisé pour accéder à des contenus bloqués dans une région géographique spécifique.

*Comparaison simple :* Imaginez un ensemble d'outils. Chaque outil a une fonction spécifique, comme un marteau pour enfoncer des clous ou une scie pour couper du bois. De la même manière, chaque type de proxy a une utilisation et une fonction spécifiques selon les besoins.

# **4. Quels sont les éléments d'un Proxy ?**

- **Client :** L'entité (généralement un navigateur ou une application) qui initie la demande vers un serveur et qui se connecte au proxy.

- **Adresse du serveur cible :** L'URL ou l'IP du serveur que le client souhaite atteindre.

- **Règles de filtrage :** Un ensemble de critères que le proxy utilise pour déterminer comment traiter les demandes, par exemple, bloquer certains sites ou autoriser l'accès à d'autres.

- **Cache :** Une mémoire temporaire où le proxy stocke des copies des réponses des serveurs, afin de fournir une réponse plus rapide aux demandes ultérieures pour le même contenu.

- **Journal (logs) :** Un enregistrement des activités du proxy, y compris les adresses IP des clients, les URLs demandées, les horodatages, etc.

- **Liste noire et blanche :** Listes d'URLs ou de domaines que le proxy est configuré pour bloquer ou autoriser.

- **Moteur de traitement :** Le composant qui traite les demandes et les réponses, applique les règles de filtrage, gère le cache, etc.

*Comparaison simple :* Imaginez un proxy comme une poste centrale. Les clients sont les personnes envoyant du courrier, l'adresse du serveur cible est l'adresse de destination, le cache est comme une étagère de courriers fréquemment demandés, les règles de filtrage sont les directives de livraison, et les journaux sont les registres de toutes les lettres traitées.

# **5. Quels sont les versions et les caractéristiques ?**

Il n'y a pas de "versions" standardisées d'un proxy comme il pourrait y en avoir pour certains logiciels. Cependant, les proxies peuvent être classés en différents types basés sur leur fonctionnalité et leurs caractéristiques :

- **Proxy transparent :** Ne modifie pas les demandes ou les réponses et est principalement utilisé pour le cache. Il ne masque pas l'adresse IP du client.

- **Proxy anonyme :** Masque l'adresse IP du client mais peut informer les sites web qu'il s'agit d'une demande via un proxy.

- **Proxy distorsion :** Transmet une fausse adresse IP à la place de celle du client.

- **Proxy haute anonymat :** Masque l'adresse IP du client et ne révèle pas qu'une demande provient d'un proxy.

- **Proxy inverse (reverse proxy) :** Sert de point d'intermédiation entre les clients et un ou plusieurs serveurs, améliorant la sécurité, la charge, et la performance.

- **Proxy SOCKS :** Ne se limite pas au trafic web, mais peut traiter n'importe quel type de trafic réseau.

- **Proxy résidentiel :** Utilise des adresses IP réelles provenant d'appareils des particuliers, offrant un haut degré d'anonymat.

*Comparaison simple :* Pensez aux différents types de chaussures. Chacune a une fonction spécifique (baskets pour le sport, bottes pour la randonnée, chaussures de ville pour les occasions formelles, etc.). De même, chaque type de proxy a une utilité et des caractéristiques spécifiques selon les besoins.

# **6. Comment fonctionne techniquement un Proxy ?**

Un proxy fonctionne en se positionnant entre le client (comme un ordinateur utilisateur) et le serveur cible (comme un site web). Plutôt que de permettre une communication directe entre ces deux entités, le proxy reçoit les demandes du client, les traite selon sa configuration, et les transmet ensuite au serveur cible.

**Étapes de communication avec un proxy :**

1. **Initiation :** Le client, souhaitant accéder à un certain service ou site web, envoie sa demande au proxy. Cette demande contient l'URL ou l'adresse IP du serveur cible, ainsi que d'autres détails tels que le type de méthode HTTP (GET, POST, etc.) et d'éventuels en-têtes.

2. **Traitement de la demande :** À la réception de la demande, le proxy vérifie ses règles de filtrage. Par exemple, il détermine si le client a la permission d'accéder au site web demandé ou si ce site est bloqué.

3. **Transmission au serveur cible :** Si la demande est autorisée, le proxy la transmet au serveur cible. Dans certains cas, le proxy peut altérer la demande (par exemple, pour masquer l'adresse IP du client).

4. **Réception de la réponse :** Une fois que le serveur cible a traité la demande, il renvoie une réponse. Cette réponse est d'abord reçue par le proxy.

5. **Traitement de la réponse :** Le proxy peut alors mettre en cache cette réponse pour une utilisation future, appliquer des transformations supplémentaires si nécessaire, ou simplement la transmettre telle quelle au client.

6. **Transmission au client :** Le proxy envoie la réponse du serveur au client. Si le contenu a été mis en cache et qu'un autre client demande le même contenu, le proxy peut fournir la réponse directement depuis son cache, évitant ainsi une nouvelle requête au serveur cible.

*Comparaison simple :* Imaginez commander un article dans un restaurant via un serveur. Au lieu de vous rendre à la cuisine pour prendre votre commande, le serveur (agissant comme un proxy) prend votre commande, la transmet à la cuisine, attend qu'elle soit prête, et vous l'apporte. Si quelqu'un d'autre commande le même plat peu de temps après, et qu'il est déjà prêt en raison de votre commande précédente, le serveur peut le fournir plus rapidement.

# **7. Quels sont les failles de sécurité utilisables pour un attaquant ?**

Un proxy, bien que souvent utilisé pour améliorer la sécurité, peut aussi présenter des vulnérabilités :

1. **Déchiffrage SSL/TLS :** Certains proxies déchiffrent le trafic SSL/TLS pour l'inspection. Si cela n'est pas correctement implémenté, cela peut introduire des vulnérabilités.

2. **Attaques Man-in-the-Middle (MitM) :** Si le proxy n'est pas correctement sécurisé, un attaquant peut s'interposer entre le client et le proxy ou entre le proxy et le serveur cible.

3. **Empoisonnement du cache :** Un attaquant pourrait tromper le proxy pour qu'il cache du contenu malveillant, qui serait ensuite servi aux clients.

4. **Divulgation d'informations :** Si le proxy conserve des journaux détaillés, un attaquant qui y accède pourrait obtenir des informations sensibles sur les activités des utilisateurs.

5. **Configuration faible :** Comme avec tout équipement réseau, une mauvaise configuration peut exposer le proxy à diverses attaques.

6. **Déni de service (DoS) :** Attaquer le proxy directement pour le surcharger et le rendre inopérant pour les utilisateurs légitimes.

# **8. Comment sécuriser techniquement le proxy ?**

1. **Utiliser une connexion chiffrée :** Assurez-vous que le trafic entre le client et le proxy et entre le proxy et le serveur cible est chiffré.

2. **Mise à jour régulière :** Tout comme d'autres logiciels, il est essentiel de garder le logiciel proxy à jour pour corriger les vulnérabilités connues.

3. **Sécurisation du cache :** Configurez correctement le cache pour éviter l'empoisonnement et assurez-vous que le contenu sensible n'est pas mis en cache.

4. **Contrôle d'accès strict :** Limitez l'accès au proxy aux seuls clients nécessaires et utilisez des méthodes d'authentification solides.

5. **Limitation des logs :** Bien que les journaux soient essentiels pour le débogage et la surveillance, évitez de conserver des informations sensibles. Chiffrez et protégez l'accès aux journaux.

6. **Révision régulière de la configuration :** Vérifiez régulièrement la configuration du proxy pour éviter les erreurs ou les oublis qui pourraient introduire des vulnérabilités.

7. **Utiliser des solutions de détection et de prévention des intrusions :** Ces solutions peuvent aider à détecter et bloquer les activités suspectes à destination ou en provenance du proxy.

8. **Réseau isolé :** Si possible, placez le proxy dans un réseau isolé (DMZ) pour le séparer des autres systèmes critiques.

*Comparaison simple :* Imaginez un proxy comme une porte d'entrée dans une maison. Si cette porte n'est pas correctement sécurisée (verrous solides, caméra de surveillance, etc.), un cambrioleur pourrait facilement entrer. De même, un proxy mal sécurisé est vulnérable à diverses attaques. Assurez-vous donc qu'il est "bien verrouillé" avec les meilleures pratiques de sécurité.