# Guide ISO 27002 

* Définit l'ensemble des bonnes pratiques en matière de sécurité
* Répartie en plusieurs 
* Agit comme une check-list en cas d'audit

# Sécurité Opérationnelle 
1. **Gestion des changements** :
	1. Comment sont gérées les modifications apportées aux systèmes et aux applications ?
	2. Existe-t-il un processus formalisé de demande, d'approbation et de documentation des changements ?
	3. Garder-vous un journal de bord des modifications ? 
	4. Comment sont testés les changements avant leur mise en production ?
2. **Mises à jour et patches** :
	1. Comment sont gérées les mises à jour et les patches des systèmes et des applications ?
	2. À quelle fréquence les systèmes sont-ils patchés ?
	3. Comment est assurée la compatibilité des patches avec l'environnement existant ?
3. **Sauvegardes et récupérations** :
	1. Comment sont gérées les sauvegardes des données ?
	2. Où sont stockées les sauvegardes ? Sont-elles chiffrées ?
	3. À quelle fréquence des tests de récupération sont-ils effectués ?
4. **Surveillance et détection** :
	1. Comment sont surveillés les systèmes et le réseau ?
	2. Quels outils sont utilisés pour la détection d'incidents et d'anomalies ?
	3. Comment est gérée l'alerte en cas de détection d'un incident ?
5. **Réponse aux incidents** :
	1. Existe-t-il un plan de réponse aux incidents informatiques ?
	2. Comment est géré un incident une fois détecté ?
	3. Qui est responsable de la gestion des incidents et comment sont-ils formés ?
6. **Gestion des droits d'accès** :
	1. Comment sont attribués les droits d'accès aux systèmes et aux données ?
	2. Comment est géré le principe du moindre privilège ?
	3. Comment sont révoqués les droits d'accès lorsqu'ils ne sont plus nécessaires ?
7. **Journalisation et suivi** :
	1. Quels événements sont consignés (log) dans les systèmes et les applications ?
	2. Comment sont sécurisés et stockés ces journaux ?
	3. Comment est assurée la révision régulière des journaux pour détecter d'éventuelles anomalies ?
8. **Formation et sensibilisation** :
	1. Comment le personnel est-il formé aux procédures de sécurité opérationnelle ?
	2. Existe-t-il des formations régulières pour tenir le personnel informé des dernières menaces et des meilleures pratiques ?
9. **Contrôles antimalware** :
	1. Quels outils antimalware sont en place ?
	2. Comment sont-ils mis à jour ?
10. **Évaluation et mise à jour** :
	1. À quelle fréquence les procédures opérationnelles sont-elles revues et mises à jour ?
	2. Comment sont gérées les nouvelles vulnérabilités découvertes dans l'environnement opérationnel ?

Avec ce questionnaire, vous aurez une vue d'ensemble solide des pratiques et des procédures de sécurité opérationnelle de votre organisation.
# Sécurité des flux 
La sécurité des flux concerne principalement la manière dont les données sont transférées et communiquées à travers les réseaux et entre différentes applications et services. Ceci inclut la gestion des réseaux, les contrôles d'accès, le chiffrement, la segmentation, etc.

1. **Architecture réseau** :
	1. Pouvez-vous décrire brièvement l'architecture du réseau de votre organisation ?
	2. Comment le réseau est-il segmenté ?
2. **Gestion des points d'accès** :
	1. Comment sont sécurisés les points d'accès au réseau (WAN, LAN, WLAN) ?
	2. Quels protocoles de sécurité sont en place pour les connexions sans fil ?
3. **Gestion des connexions externes** :
	1. Comment sont gérées et sécurisées les connexions VPN ou autres accès distants ?
	2. Existe-t-il des contrôles pour les appareils BYOD (Bring Your Own Device) ?
4. **Chiffrement** :
	1. Comment sont chiffrées les données en transit sur le réseau ?
	2. Utilisez-vous des solutions de réseau privé virtuel (VPN) pour protéger les données en déplacement ?
5. **Contrôles aux frontières** :
	1. Quels dispositifs de sécurité sont en place aux points d'entrée et de sortie du réseau (pare-feux, IDS, IPS) ?
	2. Comment sont gérés les règles de pare-feu ?
6. **Détection et réponse** :
	1. Comment détectez-vous les activités suspectes ou malveillantes sur le réseau ?
	2. Comment répondez-vous à ces activités une fois détectées ?
7. **Gestion du trafic** :
	1. Comment est priorisé et contrôlé le trafic sur le réseau pour garantir la disponibilité et la performance ?
	2. Existe-t-il des contrôles pour empêcher les attaques par déni de service (DoS) ?
8. **Echanges de données avec des tiers** :
	1. Comment sont gérés et sécurisés les échanges de données avec des partenaires, fournisseurs ou autres tiers ?
	2. Existe-t-il des accords ou des protocoles spécifiques pour ces échanges ?
9. **Contrôles des applications** :
	1. Comment est contrôlé le trafic des applications sur le réseau ?
	2. Comment sont gérées les mises à jour et les modifications des applications en termes de sécurité des flux ?
10. **Journalisation et suivi** :
	1. Comment sont consignés (log) les événements liés au trafic réseau ?
	2. À quelle fréquence ces journaux sont-ils revus ?
11. **Formation et sensibilisation** :
	1. Le personnel est-il formé à reconnaître et à signaler les comportements suspects ou les tentatives d'accès non autorisées liées au flux des données ?
12. **Révision et mise à jour** :
	1. À quelle fréquence l'architecture réseau et les contrôles de sécurité des flux sont-ils revus et mis à jour ?
# Sécurité des données

1. **Collecte de données** :
	1. Quels types de données sont collectés par le système (données personnelles, financières, opérationnelles...) ?
	2. Comment ces données sont-elles collectées ? Y a-t-il des contrôles pour s'assurer de leur exactitude et de leur intégrité lors de la collecte ?
2. **Stockage des données** :
	1. Quels systèmes, bases de données ou solutions de stockage sont utilisés pour stocker les données ?
	2. Qui a accès à ces données stockées ?
	3. Comment est gérée la segmentation des données (séparation des données sensibles et non sensibles) ?
	4. Comment est géré le chiffrement des données ?
3. **Durée de conservation** :
	1. Quelle est la politique de rétention des données ? Pourquoi cette durée a-t-elle été choisie ?
	2. Comment est mise en œuvre la suppression ou l'archivage des données après cette période ?
4. **Backups** :
	1. Quelle est la politique de sauvegarde des données ?
	2. Combien de temps sont conservées ces sauvegardes ?
	3. Où sont stockées les sauvegardes (emplacement géographique, sur site/hors site) ?
	4. Comment sont protégées ces sauvegardes (chiffrement, contrôle d'accès...) ?
	5. Qui à accès au backups et via quel moyen ? 
	6. À quelle fréquence les restaurations de sauvegarde sont-elles testées ?
5. **Chiffrement et hashing** :
	1. Quels algorithmes de chiffrement et de hachage sont utilisés pour protéger les données ?
	2. Comment sont gérées et protégées les clés de chiffrement ?
6. **Partage et transfert de données** :
	1. Comment sont partagées et transférées les données entre différents systèmes ou avec des tiers ?
	2. Comment est assurée la sécurité de ces transferts (chiffrement, tunnels sécurisés...) ?
7. **Accès aux données** :
	1. Comment est géré le contrôle d'accès aux données ?
	2. Existe-t-il un journal d'accès pour suivre qui a consulté ou modifié les données ?
8. **Sensibilisation et formation** :
	1. Comment le personnel est-il formé à la manipulation sécurisée des données ?
	2. Existe-t-il des rappels ou des formations continues sur la protection des données ?
9. **Réponse aux incidents** :
	1. Comment réagissez-vous en cas de violation ou de fuite de données ?
	2. Y a-t-il un plan de réponse aux incidents spécifique pour les incidents liés aux données ?

# Sécurité des Réseaux

1. **Architecture et conception** :
	1. Pouvez-vous décrire brièvement l'architecture de votre réseau ?
	2. Comment les réseaux internes et externes sont-ils segmentés ?
	3. Utilisez-vous une architecture à zones démilitarisées (DMZ) pour les services exposés à Internet ?
2. **Contrôle d'accès au réseau** :
	1. Comment sont gérées les authentifications pour accéder au réseau ?
	2. Utilisez-vous des solutions comme le 802.1X pour le contrôle d'accès réseau basé sur des portails ?
	3. Comment les périphériques non autorisés sont-ils détectés et gérés ?
3. **Protection contre les menaces** :
	1. Quels types de pare-feu utilisez-vous (pare-feu d'application, pare-feu d'entreprise) ?
	2. Comment gérez-vous la détection et la prévention des intrusions (IDS/IPS) ?
	3. Comment traitez-vous les menaces telles que les attaques DDoS ?
4. **Chiffrement du réseau** :
	1. Comment le trafic réseau est-il chiffré (par exemple, VPN, TLS) ?
	2. Comment sont gérées et protégées les clés de chiffrement ?
5. **Surveillance et détection** :
	1. Comment surveillez-vous le trafic réseau pour détecter d'éventuelles activités suspectes ?
	2. Utilisez-vous une solution SIEM (gestion des informations et des événements de sécurité) ?
	3. Comment sont traitées les alertes réseau ?
6. **Mise à jour et maintenance** :
	1. Comment assurez-vous que tous vos équipements réseau (routeurs, commutateurs, pare-feu, etc.) sont régulièrement mis à jour ?
	2. Disposez-vous d'un calendrier de maintenance régulière pour vos infrastructures réseau ?
7. **Connectivité distante** :
	1. Comment gérez-vous l'accès distant au réseau (par exemple, VPN) ?
	2. Quelles mesures de sécurité sont mises en place pour les connexions distantes ?
8. **Réseau sans fil** :
	1. Quels protocoles de sécurité sont utilisés pour vos réseaux Wi-Fi ?
	2. Comment sont gérés l'accès et l'authentification sur le réseau sans fil ?
9. **Gestion des configurations** :
	1. Avez-vous des normes pour configurer les équipements réseau de manière sécurisée ?
	2. Comment sont stockées et sécurisées les configurations ?
10. **Réponse aux incidents** :
	1. Comment réagissez-vous en cas d'incident réseau ?
	2. Disposez-vous d'un plan de réponse spécifique pour les incidents liés au réseau ?
11. **Politiques et procédures** :
	1. Avez-vous des politiques et des procédures spécifiques pour la sécurité des réseaux ?
	2. Comment sont-elles régulièrement revues et mises à jour ?
13. **Évaluation et tests** :
	1. À quelle fréquence effectuez-vous des tests d'intrusion ou d'autres évaluations sur votre réseau ?
	2. Comment les résultats de ces tests sont-ils traités et intégrés dans vos processus de sécurité ?





##########################################################################


##################################################################
# Sécurité Physique 

## 1) Points à aborder 
* Identification des zones sensibles et les obstacles d'accès
* Emplacement des équipements
* Procédures de gestions de clefs et des combinaison
* Contrôle d'accès au zone sensibles et les modalités aux personnes non habilités
* Mesures pour contrôler des équipement et s'assurer de leur bon fonctionnement
* Procédures de gestion des alarmes et détection d'intrusion
* Procédures mises en place en dehors des heures de travail
## 2) Questions à poser 
1. **Localisation des données** :
	1. Où sont situés physiquement les serveurs et autres dispositifs de stockage de données ?
2. **Contrôle d'accès aux locaux** :
	1. Les entrées des locaux sont-elles verrouillées ? 
	2. Qui peut accéder aux locaux ?
	3. Comment obtenir un droit d'accès physique ?
	4. Verrouillage biométrique/badge ou autre moyen d'accès ?
	5. Comment sont gérées les clés, badges ou autres moyens d'accès physique ?
	6. Qui est responsable de leur distribution et de leur recueil ?
	7. Certaines zones sont-elles limitées à un nombre restreint de personnes ? Qui sont ces personnes et comment sont-elles désignées ?
3. **Surveillance et détection** :
	1. Y a-t-il des caméras de surveillance ? Où sont-elles situées ? Qui a accès au enregistrement
	2. Quels dispositifs de détection d'intrusion sont mis en place ?
	3. Comment sont sécurisées les entrées et sorties des locaux ?
	4. Y a-t-il des clôtures, barrières ou autres dispositifs périphériques de sécurité ?
4. **Mesures environnementales et d'urgence** :
	1. Quels dispositifs sont mis en place pour la protection contre les incendies, inondations et autres catastrophes naturelles ?
	2. Comment assurez-vous la disponibilité des systèmes en cas de panne d'électricité ? Système de relais, moteur thermique, solaire ?
	3. En cas d'urgence, existe-t-il un protocole clair pour protéger les informations tout en garantissant la sécurité des personnes ?
5. **Gestion des visiteurs et sous-traitants** :
	1. Comment les visiteurs et sous-traitants sont-ils gérés dans les locaux ? Sont-ils libres de se déplacer ? Sont-ils surveillés ou filmés ?
6. **Plan de réponse aux incidents physiques** :
	1. Existe-t-il un plan en cas d'intrusion, d'incendie ou d'autres incidents physiques ?
	2. Ce plan est-il régulièrement mis à jour et testé ?
7. **Formation et sensibilisation du personnel** :
	1. Le personnel est-il formé pour reconnaître et signaler les comportements suspects ou tentatives d'accès non autorisées ?
8. **Transport sécurisé des données** :
	1. Comment sont sécurisées les données lorsqu'elles sont physiquement transportées, par exemple sur des disques durs externes ou des bandes ?
9. **Traitement sécurisé des équipements hors service** :
	1. Comment sont éliminés les équipements en fin de vie ?
	2. Y a-t-il des procédures pour s'assurer que toutes les données sont complètement effacées ?
10. **Évaluation et mise à jour** :
	1. À quelle fréquence les mesures de sécurité physique sont-elles évaluées et mises à jour pour s'adapter à l'évolution des menaces ?
	2. À quelle fréquence une évaluation des risques physiques est-elle réalisée pour s'assurer que toutes les vulnérabilités sont correctement identifiées et atténuées ?
 
# Sécurité des personnes 
## 1) Points à aborder 
* Liste du personnel intervenants sur le système et leurs niveau de droits (admin, user, technicien)
* Besoins d'habilitation selon le type de personnel ? 
	* Niveaux d'habilitations définis
	* Processus d'habilitation
	* Critères d'habilitation 
	* Les restrictions en fonction du niveau d'habilitation 
* Formations sur la sécurité en fonction des niveaux d'habilitation
* Procédures de gestion des personnel de maintenance et d'entretien
## 2) Questions à poser 

### 1. **Liste du personnel intervenant sur le système et leurs niveaux de droits (admin, user, technicien)**
   - Qui sont les membres du personnel autorisés à accéder au système ?
   - Quels rôles spécifiques chaque membre du personnel a-t-il dans la gestion du système ?
   - Quels niveaux de droits chaque membre du personnel détient-il (admin, utilisateur, technicien) ?
   - Comment les niveaux de droits sont-ils attribués et révisés ?
### 2. **Besoins d'habilitation selon le type de personnel**
   - Quels sont les différents niveaux d'habilitation nécessaires pour accéder au système ?
   - Comment le processus d'habilitation est-il géré ?
   - Quels sont les critères spécifiques utilisés pour déterminer le niveau d'habilitation d'un individu ?
   - Y a-t-il des restrictions spécifiques associées à chaque niveau d'habilitation ?
### 3. **Formations sur la sécurité en fonction des niveaux d'habilitation**
   - Quels types de formations en sécurité sont fournis au personnel ?
   - Comment les besoins en formation sont-ils déterminés en fonction des niveaux d'habilitation ?
   - À quelle fréquence les formations en sécurité sont-elles fournies ou mises à jour ?
   - Comment l'efficacité des formations en sécurité est-elle évaluée ?
### 4. **Procédures de gestion du personnel de maintenance et d'entretien**
   - Quelles sont les procédures standard pour gérer le personnel de maintenance et d'entretien ?
   - Comment le personnel de maintenance et d'entretien est-il habilité et formé ?
   - Quelles mesures de sécurité spécifiques sont en place pour le personnel de maintenance et d'entretien ?
   - Comment les activités de maintenance et d'entretien sont-elles documentées et revues ?
# Sécurité des documents 
## 1) Points à aborder
* Identification des documents stockés relatif au SI (journaux d'audit, les journaux d'événements, les fichiers de configuration, les politiques et procédures de sécurité)
* Documents sur les mesures de sécurité actuellement déployés 
* Documents sur le fonctionnent du système et son stockage
* Procédures d'inspections des enregistrement et les responsabilités
* Mesures de contrôle, stockage et marquage des documents
* Procédures de création des documents techniques et leur diffusion dans l'équipe
* Procédures d'accès aux documents et enregistrement 
* Procédures de suppression des anciens documents et support
## 2) Questions à poser
### 1. **Identification des documents stockés relatifs au SI**
   - Quels sont les différents types de documents stockés relatifs au SI (journaux d'audit, journaux d'événements, fichiers de configuration) ?
   - Où sont stockés ces documents ?
   - Qui a accès à ces documents ?
### 2. **Documents sur les mesures de sécurité actuellement déployés**
   - Quels documents détaillent les mesures de sécurité actuellement en place ?
   - Comment ces documents sont-ils mis à jour et à quelle fréquence ?
   - Qui est responsable de la mise à jour de ces documents ?
### 3. **Documents sur le fonctionnement du système et son stockage**
   - Quels documents expliquent le fonctionnement du système ?
   - Où sont stockés ces documents explicatifs et qui y a accès ?
   - Comment sont sécurisés les documents relatifs au fonctionnement du système ?
### 4. **Procédures d'inspections des enregistrements et les responsabilités**
   - Quelles sont les procédures d'inspection des enregistrements ?
   - Qui est responsable de ces inspections ?
   - À quelle fréquence ces inspections sont-elles effectuées ?
### 5. **Mesures de contrôle, stockage et marquage des documents**
   - Quelles sont les mesures de contrôle appliquées aux documents ?
   - Comment les documents sont-ils stockés et marqués ?
   - Quelles sont les procédures de stockage sécurisé des documents sensibles ?
### 6. **Procédures de création des documents techniques et leur diffusion dans l'équipe**
   - Comment sont créés les documents techniques ?
   - Quelles sont les procédures de diffusion de ces documents au sein de l'équipe ?
   - Qui a le droit de modifier ces documents techniques ?
### 7. **Procédures d'accès aux documents et enregistrement**
   - Qui a accès aux différents types de documents ?
   - Comment l'accès aux documents est-il enregistré et surveillé ?
   - Quelles sont les restrictions d'accès appliquées aux documents sensibles ?
### 8. **Procédures de suppression des anciens documents et supports**
   - Quelles sont les procédures de suppression ou de destruction des anciens documents ?
   - Comment est gérée la suppression sécurisée des supports d'information ?
   - À quelle fréquence les anciens documents et supports sont-ils supprimés ou détruits ?

Cette liste exhaustive de questions devrait vous permettre de couvrir tous les aspects des documents et des enregistrements relatifs à la sécurité du système d'information.
# Sécurité du SI
## 1) Points à aborder
* Description de l'environnement système (?)
* Mesures de protections du matériel contre 
	* perte
	* endommagement
	* vol
	* compromission
	* Emplacement, stockage, prise en compte et manipulation
* Procédure d'arrêt et démarrage des postes et machines
* Mesures de protection des services généraux contre les coupures
* Procédures de contrôle d'équipements et leur intégrité
* Maintenance du système
	* Préventive ou curative
	* procédures selon le type de maintenance
	* effectuer par un interne  ou un externe
	* périodicité et méthodes appliquer
* 
## 2) Questions à poser
### 1. **Description de l'environnement système**
   - Quels sont les composants principaux de l'environnement système ?
   - Comment chaque composant interagit-il avec les autres au sein du système ?
   - Y a-t-il des composants particulièrement sensibles ou critiques dans l'environnement système ?
### 2. **Mesures de protections du matériel**
   - Quelles sont les mesures en place pour protéger le matériel contre la perte, l'endommagement, le vol et la compromission ?
   - Comment le matériel est-il stocké et manipulé pour garantir sa sécurité ?
   - Quels sont les emplacements sécurisés dédiés au stockage du matériel ?
### 3. **Procédure d'arrêt et démarrage des postes et machines**
   - Quelles sont les procédures à suivre pour l'arrêt et le démarrage sécurisés des postes et machines ?
   - Qui est autorisé à exécuter ces procédures ?
   - Existe-t-il des vérifications ou des contrôles en place lors de l'arrêt et du démarrage des machines ?
### 4. **Mesures de protection des services généraux contre les coupures**
   - Quelles mesures sont en place pour protéger les services généraux (électricité, internet) contre les interruptions ?
   - Existe-t-il des systèmes de secours ou de redondance pour minimiser les temps d'arrêt ?
   - Comment les services généraux sont-ils surveillés pour détecter rapidement toute interruption ?
### 5. **Procédures de contrôle d'équipements et leur intégrité**
   - Quelles procédures de contrôle sont en place pour s'assurer de l'intégrité des équipements ?
   - À quelle fréquence ces contrôles sont-ils effectués ?
   - Qui est responsable de la réalisation de ces contrôles ?
### 6. **Maintenance du système**
   - Quels sont les types de maintenance appliqués au système (préventive, curative) ?
   - Comment les procédures de maintenance varient-elles selon le type de maintenance ?
   - La maintenance est-elle effectuée par des intervenants internes ou externes ?
   - À quelle fréquence la maintenance est-elle réalisée, et quelles méthodes sont appliquées ?
# Sécurité logiciel
## 1) Points à aborder
* Procédures de contrôle d'accès au système 
* Procédures de gestion des comptes utilisateurs
* Procédures de d'installation de nouveau logiciel 
* Procédures de masterisation des logicielles et des copies de sauvegarde
* Procédures de gestion des traces d’audit et l'utilisation du SI
	* Contrôle des accès autorisés
	* Gestion des alarmes de sécurité (antivirus) ou les défaillances (pannes)
	* Contrôle des modifications ou de tentatives de modification des paramètres ou mesures de sécurité
* Procédures de sauvegarde des fichiers qui retrace l'historique des journaux
* Procédures de mise en place contre les codes malveillants (anti-virus,sas,machine blanche)
* Précision des zones de protection à respecter (zone de couplage, zone de sécurité)
* Procédures de gestion des équipements chiffre et des clés associées.
## 2) Questions à poser
### 1. **Procédures de contrôle d'accès au système**
   - Quelles sont les étapes définies pour contrôler l'accès au système ?
   - Comment les droits d'accès sont-ils attribués aux différents utilisateurs ?
   - Comment s'assurer que seuls les utilisateurs autorisés ont accès au système ?
### 2. **Procédures de gestion des comptes utilisateurs**
   - Comment sont créés les nouveaux comptes utilisateurs ?
   - Comment sont gérées les modifications des comptes existants (réaffectation, changement de rôle, etc.) ?
   - Comment les comptes inactifs ou obsolètes sont-ils identifiés et désactivés ?
### 3. **Procédures d'installation de nouveau logiciel**
   - Quel est le processus pour installer un nouveau logiciel ?
   - Qui est autorisé à installer de nouveaux logiciels ?
   - Comment s'assurer que les nouveaux logiciels installés sont sécurisés et conformes aux politiques de sécurité de l'entreprise ?
### 4. **Procédures de masterisation des logiciels et des copies de sauvegarde**
   - Comment est effectuée la masterisation des logiciels ?
   - Quelles sont les étapes pour réaliser les copies de sauvegarde ?
   - Comment et où sont stockées les copies de sauvegarde ?
### 5. **Procédures de gestion des traces d’audit et l'utilisation du SI**
   - Comment sont collectées et stockées les traces d'audit ?
   - Quelles sont les informations essentielles à inclure dans les traces d'audit ?
   - Comment sont analysées les traces d'audit pour identifier les activités suspectes ou non conformes ?
### 6. **Contrôle des accès autorisés**
 - Comment sont contrôlés les accès au système ?
 - Comment est assurée la traçabilité des accès ?
### 7.**Gestion des alarmes de sécurité (antivirus) ou les défaillances (pannes)**
 - Comment sont configurées et gérées les alarmes de sécurité ?
 - Quelle est la procédure en cas d'alarme de sécurité ou de défaillance détectée ?
### 8.**Contrôle des modifications ou de tentatives de modification des paramètres ou mesures de sécurité**
 - Comment sont surveillées les modifications des paramètres de sécurité ?
 - Comment identifier et réagir en cas de tentatives non autorisées de modification des paramètres de sécurité ?

### 9. **Procédures de sauvegarde des fichiers qui retrace l'historique des journaux**
   - Comment sont organisées et planifiées les sauvegardes des journaux historiques ?
   - Où sont stockées les sauvegardes et comment est assurée leur sécurité ?
   - Quelle est la durée de rétention des sauvegardes et comment sont-elles archivées ou supprimées après cette période ?
### 10. **Procédures de mise en place contre les codes malveillants (antivirus, sas, machine blanche)**
   - Quels sont les outils et technologies utilisés pour protéger le système contre les codes malveillants ?
   - Comment sont configurés et mis à jour ces outils (antivirus, etc.) ?
   - Comment sont gérées et analysées les alertes générées par ces outils ?
### 11. **Précision des zones de protection à respecter (zone de couplage, zone de sécurité)**
   - Quelles sont les différentes zones de protection définies et leurs caractéristiques ?
   - Comment est contrôlé l'accès à chaque zone et comment est assuré le respect des règles de sécurité propres à chaque zone ?
   - Quels sont les risques identifiés pour chaque zone et comment sont-ils atténués ?
### 12. **Procédures de gestion des équipements de chiffrement et des clés associées**
   - Comment sont générées, distribuées, et stockées les clés de chiffrement ?
   - Comment est assuré le renouvellement sécurisé des clés et le retrait des clés compromises ou obsolètes ?
   - Quelles sont les procédures en cas de compromission suspectée d'une clé ou d'un équipement de chiffrement ?



# Sécurité de secours
## 1) Points à aborder
* Responsabilités et la périodicité des sauvegardes systèmes et utilisateurs.
* Stockage et accès des sauvegardes systèmes et utilisateurs
* Procédures de reprise après incident.
* Mesures de protection des matériels contre des coupures de courant et autres perturbations dues à une défaillance des services généraux (alimentation, énergie)
* Mesures de protection des matériels contre des perturbations dues à une défaillance de climatisation)
* Procédures de gestion des perte de moyen de télécommunication.
* Protection incendie nécessaire à l’installation et utilisation du SI.
* Mesures d’urgence à appliquer.
## 2) Questions à poser
### 1. **Responsabilités et la périodicité des sauvegardes systèmes et utilisateurs:**
   - Qui est responsable de la réalisation des sauvegardes système et utilisateur ?
   - À quelle fréquence les sauvegardes système et utilisateur sont-elles effectuées ?
   - Comment est déterminée la périodicité des sauvegardes ?
   - Existe-t-il des procédures documentées pour guider le processus de sauvegarde ?
### 2. **Stockage et accès des sauvegardes systèmes et utilisateurs:**
   - Où sont stockées les sauvegardes système et utilisateur ?
   - Qui a accès aux sauvegardes stockées ?
   - Comment l'accès aux sauvegardes est-il contrôlé et sécurisé ?
   - Les sauvegardes sont-elles cryptées ou d'une autre manière sécurisées contre les accès non autorisés ?
### 3. **Procédures de reprise après incident:**
   - Existe-t-il un plan de reprise après incident documenté ?
   - Comment sont testées les procédures de reprise après incident ?
   - À quelle fréquence les procédures de reprise après incident sont-elles révisées et mises à jour ?
### 4. **Mesures de protection des matériels contre des coupures de courant et autres perturbations:**
   - Quelles sont les mesures en place pour protéger les équipements contre les coupures de courant ?
   - Existe-t-il des systèmes d'alimentation interruptible (UPS) ou des générateurs pour garantir la continuité de l'alimentation électrique ?
### 5. **Mesures de protection des matériels contre des perturbations dues à une défaillance de climatisation:**
   - Comment le système de climatisation est-il surveillé pour garantir qu'il fonctionne correctement ?
   - Quelles actions sont entreprises en cas de défaillance du système de climatisation ?
### 6. **Procédures de gestion des pertes de moyen de télécommunication:**
   - Comment les pertes de moyens de télécommunication sont-elles gérées ?
   - Existe-t-il des solutions de rechange ou des plans de contingence en place pour maintenir la communication en cas de perte de moyens de télécommunication ?
### 7. **Protection incendie nécessaire à l’installation et utilisation du SI:**
   - Quels sont les systèmes de protection contre l'incendie en place ?
   - Comment le système de protection incendie est-il entretenu et testé ?
### 8. **Mesures d’urgence à appliquer:**
   - Quelles sont les mesures d'urgence à appliquer en cas d'incident affectant le SI ?
   - Le personnel est-il formé et conscient des procédures d'urgence à suivre ?
   - Comment sont communiquées les mesures d'urgence aux différentes parties prenantes concernées ?
