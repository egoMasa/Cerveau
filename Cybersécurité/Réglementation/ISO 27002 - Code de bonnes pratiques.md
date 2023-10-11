# Guide ISO 27002 

* Définit l'ensemble des bonnes pratiques en matière de sécurité
* Répartie en plusieurs 
* Agit comme une check-list en cas d'audit
# Sécurité Physique 
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
	1. Y a-t-il des caméras de surveillance ? Où sont-elles situées ?
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
 
# Sécurité Opérationnelle 
1. **Gestion des changements** :
	1. Comment sont gérées les modifications apportées aux systèmes et aux applications ?
	2. Existe-t-il un processus formalisé de demande, d'approbation et de documentation des changements ?
	3. Comment sont testés les changements avant leur mise en production ?
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
	4. Comment est géré le chiffrement des données au repos ?
3. **Durée de conservation** :
	1. Quelle est la politique de rétention des données ? Pourquoi cette durée a-t-elle été choisie ?
	2. Comment est mise en œuvre la suppression ou l'archivage des données après cette période ?
4. **Backups** :
	1. Quelle est la politique de sauvegarde des données ?
	2. Combien de temps sont conservées ces sauvegardes ?
	3. Où sont stockées les sauvegardes (emplacement géographique, sur site/hors site) ?
	4. Comment sont protégées ces sauvegardes (chiffrement, contrôle d'accès...) ?
	5. À quelle fréquence les restaurations de sauvegarde sont-elles testées ?
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
9. **Évaluation des risques** :
	1. Comment les risques associés aux données sont-ils évalués ?
	2. Comment sont gérées les vulnérabilités ou les menaces identifiées ?
10. **Réponse aux incidents** :
	1. Comment réagissez-vous en cas de violation ou de fuite de données ?
	2. Y a-t-il un plan de réponse aux incidents spécifique pour les incidents liés aux données ?
11. **Conformité réglementaire** :
	1. Comment assurez-vous la conformité avec les réglementations relatives à la protection des données (par exemple, RGPD, CCPA...) ?
	2. Avez-vous des audits réguliers pour vous assurer de cette conformité ?

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
11. **Formation et sensibilisation** :
	1. Comment le personnel technique est-il formé aux meilleures pratiques de sécurité réseau ?
	2. Comment les utilisateurs finaux sont-ils sensibilisés aux risques liés au réseau ?
12. **Politiques et procédures** :
	1. Avez-vous des politiques et des procédures spécifiques pour la sécurité des réseaux ?
	2. Comment sont-elles régulièrement revues et mises à jour ?
13. **Évaluation et tests** :
	1. À quelle fréquence effectuez-vous des tests d'intrusion ou d'autres évaluations sur votre réseau ?
	2. Comment les résultats de ces tests sont-ils traités et intégrés dans vos processus de sécurité ?


