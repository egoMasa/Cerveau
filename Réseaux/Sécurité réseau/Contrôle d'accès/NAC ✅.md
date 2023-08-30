## Contrôle d'accès réseau (NAC - Network Access Control)

### 1. C'est quoi le protocole?
**NAC** n'est pas un protocole en soi, mais plutôt une approche ou une solution utilisée pour gérer l'accès au réseau. Il s'agit d'un ensemble de politiques de sécurité permettant de déterminer et d'appliquer qui (ou quel dispositif) est autorisé à accéder et à utiliser le réseau.

### 2. C'est quoi le but et l'intérêt du protocole?
**But:**  
Le but principal du NAC est de prévenir l'accès non autorisé et de garantir que les dispositifs se conformant à une politique de sécurité spécifique ont accès au réseau.

**Intérêt:**  
- **Sécurité renforcée:** Les solutions NAC garantissent que seuls les dispositifs conformes aux politiques de sécurité puissent accéder au réseau, réduisant ainsi les risques d'attaques ou de compromissions.
  
- **Visibilité:** Le NAC offre une visibilité sur les dispositifs qui tentent d'accéder au réseau, permettant ainsi une meilleure gestion et une surveillance accrue.
  
- **Conformité:** Pour les entreprises soumises à des réglementations strictes, le NAC peut aider à garantir que seuls les dispositifs conformes puissent accéder aux ressources sensibles.
  
- **Gestion des invités:** Le NAC permet de contrôler l'accès des invités en leur fournissant un accès limité ou segmenté au réseau.

### 3. Quels sont les cas courants d'utilisation du protocole?

- **Gestion de l'accès des invités:** Par exemple, dans un hôtel ou une conférence, où vous souhaitez fournir un accès Internet aux invités sans compromettre la sécurité du réseau principal.

- **BYOD (Bring Your Own Device):** De nombreuses entreprises permettent à leurs employés d'apporter leurs propres dispositifs (téléphones, tablettes, ordinateurs portables) au travail. Le NAC garantit que ces dispositifs sont sécurisés et conformes avant d'accorder l'accès au réseau.

- **Mise en quarantaine:** Les dispositifs qui ne sont pas à jour avec les derniers correctifs de sécurité ou qui sont infectés par des malwares peuvent être placés en quarantaine jusqu'à ce qu'ils soient conformes aux politiques.

- **Intégration avec d'autres systèmes de sécurité:** Le NAC peut être intégré à d'autres systèmes comme les IDS/IPS, les pare-feu et les systèmes de gestion des événements et des informations de sécurité (SIEM) pour fournir une sécurité multicouche.

- **Conformité réglementaire:** Pour les industries telles que la finance ou la santé, le NAC peut être utilisé pour garantir que seuls les dispositifs conformes aux réglementations ont accès aux informations sensibles.

En conclusion, le NAC est un élément essentiel de la stratégie de sécurité réseau d'une organisation. Il offre une approche proactive pour garantir que seuls les dispositifs conformes et autorisés ont accès aux ressources du réseau, tout en offrant une visibilité et un contrôle accrus aux administrateurs réseau.

### 4. Quels sont les éléments du NAC?

Le NAC, en tant que solution de sécurité, est composé de plusieurs éléments essentiels qui travaillent ensemble pour fournir un accès sécurisé au réseau. Voici les principaux éléments:

- **Serveur d'authentification:** C'est généralement un serveur RADIUS ou TACACS+ qui gère l'authentification, l'autorisation et la comptabilité (AAA) des utilisateurs et des dispositifs.
    
- **Agent NAC:** Il s'agit généralement d'un logiciel installé sur les dispositifs clients pour collecter les informations sur leur état de conformité. Il peut s'agir d'agents persistants (installés de manière permanente) ou d'agents dissolvants (temporaires).
    
- **Contrôleur NAC:** Un dispositif ou une solution logicielle qui prend des décisions sur l'accès au réseau en fonction des informations fournies par l'agent NAC et du serveur d'authentification. Il peut autoriser, refuser ou limiter l'accès au réseau en fonction des politiques définies.
    
- **Base de données des politiques:** Où sont stockées toutes les politiques de conformité et d'accès. Elle détermine ce qui est considéré comme "conforme" et comment les dispositifs non conformes doivent être traités.
    
- **Switches & Points d'accès:** Ces équipements de réseau jouent un rôle crucial dans l'application des politiques NAC en fournissant ou en refusant l'accès physique au réseau.

### 5. Comment fonctionne techniquement le NAC et comment on le déploie?

Le NAC fonctionne en évaluant les dispositifs qui tentent de se connecter à un réseau pour s'assurer qu'ils respectent les politiques de sécurité définies par l'organisation. Voici comment le NAC fonctionne techniquement et comment on le déploie:

#### Fonctionnement Technique du NAC:

1. **Demande d'accès:** Lorsqu'un dispositif essaie de se connecter au réseau, le NAC intervient pour évaluer le dispositif.
    
2. **Évaluation de la posture:** À l'aide d'un agent (logiciel installé sur le dispositif), le NAC vérifie si le dispositif respecte les politiques définies. Cela peut inclure des vérifications pour les mises à jour du système d'exploitation, les logiciels de sécurité à jour, l'absence de malwares, etc.
    
3. **Décision d'accès:** En fonction de l'évaluation, le contrôleur NAC décide d'accorder un accès total, un accès limité ou de refuser l'accès. Par exemple, un dispositif sans les derniers correctifs de sécurité pourrait être placé dans un VLAN séparé où il peut seulement accéder à Internet pour télécharger des mises à jour.
    
4. **Application de la politique:** Les switches, routeurs ou points d'accès appliquent la politique décidée par le contrôleur NAC, limitant ou permettant l'accès au réseau.
    
5. **Surveillance continue:** Une fois connecté, le dispositif peut continuer à être surveillé pour assurer qu'il reste conforme.
    

#### Déploiement du NAC:

1. **Évaluation des besoins:** Avant de déployer le NAC, il est crucial de comprendre les besoins spécifiques de l'organisation. Cela inclut la compréhension des types de dispositifs qui se connectent, des politiques nécessaires, et des intégrations avec d'autres systèmes.
    
2. **Choix de la solution:** Il existe de nombreuses solutions NAC sur le marché, allant des options matérielles dédiées aux solutions basées sur le cloud. Il faut choisir celle qui convient le mieux à la taille de l'organisation, à son budget et à ses besoins.
    
3. **Définition des politiques:** Avant la mise en place, définissez clairement vos politiques de conformité. Qu'est-ce qu'un dispositif doit avoir pour être considéré comme "conforme"?
    
4. **Installation des contrôleurs NAC:** Installez le matériel ou le logiciel qui prendra les décisions d'accès. Ils devraient être placés de manière à pouvoir contrôler l'accès à l'ensemble du réseau.
    
5. **Déploiement des agents:** Sur les dispositifs qui seront régulièrement connectés au réseau, installez les agents NAC qui rapporteront leur statut au contrôleur.
    
6. **Configuration des équipements réseau:** Configurez vos switches, routeurs et points d'accès pour qu'ils puissent appliquer les décisions du NAC.
    
7. **Intégration avec d'autres systèmes:** Si nécessaire, intégrez le NAC avec d'autres systèmes tels que les SIEM, les systèmes de gestion des vulnérabilités, etc.
    
8. **Tests:** Avant de déployer complètement, testez le système dans un environnement contrôlé pour vous assurer qu'il fonctionne comme prévu.

### 9. Quels sont les failles de sécurité du NAC?

Comme tout système ou protocole, le NAC n'est pas exempt de failles potentielles. Bien que le NAC soit conçu pour améliorer la sécurité du réseau, certaines failles peuvent émerger, notamment :

1. **Contournement des agents:** Si un attaquant peut désactiver ou contourner l'agent NAC sur un dispositif, il peut éviter l'évaluation de la posture.
  
2. **Fausse déclaration de posture:** Un dispositif compromis pourrait faussement signaler qu'il est conforme aux politiques de l'organisation, trompant ainsi le système NAC.
  
3. **Attaques man-in-the-middle (MitM):** Si les communications entre le dispositif et le contrôleur NAC ne sont pas correctement sécurisées, un attaquant pourrait intercepter et altérer les communications.
  
4. **Failles dans le logiciel NAC lui-même:** Comme tout logiciel, le NAC peut avoir ses propres vulnérabilités qui pourraient être exploitées par des attaquants.
  
5. **Échec de mise à jour des politiques:** Si les politiques ne sont pas régulièrement mises à jour pour refléter le paysage des menaces en constante évolution, des dispositifs non sécurisés pourraient être autorisés à se connecter.

### 10. Comment sécuriser le protocole NAC?

Pour renforcer le NAC et le rendre plus robuste contre les menaces, voici quelques meilleures pratiques :

1. **Crypter les communications:** Assurez-vous que toutes les communications entre le dispositif, l'agent et le contrôleur NAC sont cryptées pour éviter les attaques MitM.
  
2. **Mises à jour régulières:** Gardez votre solution NAC à jour pour vous assurer que toutes les failles de sécurité connues sont corrigées.
  
3. **Politiques strictes:** Soyez strict dans la définition de vos politiques. Lorsque vous êtes en doute, adoptez une approche de moindre privilège et n'accordez l'accès qu'aux dispositifs dont vous êtes sûr de la conformité.
  
4. **Utiliser une authentification multifactorielle (MFA):** Pour les dispositifs et utilisateurs se connectant au réseau, l'utilisation d'une MFA peut renforcer la sécurité.
  
5. **Surveillance continue:** Ne vous fiez pas uniquement à l'évaluation initiale de la posture. Surveillez continuellement les dispositifs connectés pour détecter tout changement qui pourrait indiquer une compromission.
  
6. **Séparation des réseaux:** Utilisez des VLANs ou d'autres technologies pour séparer les dispositifs non conformes ou invités du réseau principal.
  
7. **Éducation des utilisateurs:** Formez régulièrement vos utilisateurs sur l'importance de la conformité et les dangers potentiels si leurs dispositifs ne respectent pas les politiques.
  
8. **Journalisation et surveillance:** Conservez des journaux détaillés de toutes les décisions NAC et des tentatives de connexion. Ceci est crucial pour détecter des activités suspectes et pour les audits.

En suivant ces meilleures pratiques, vous pouvez maximiser les avantages de sécurité que le NAC offre tout en minimisant les risques associés à son déploiement.

## Configuration Cisco