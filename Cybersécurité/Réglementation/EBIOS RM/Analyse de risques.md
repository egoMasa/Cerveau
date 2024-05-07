# EBIOS RM 

# 0) Présentation méthode EBIOS RM
* Il s'agit d'une méthode de gestion des risques en sécurité de l'information
* Permet d’identifier, d’analyser et de traiter les risques liés à la sécurité de l’information au sein d’une organisation
* La méthode EBIOS RM est composé de 5 étapes différentes 
	1. Cadrage/socle de sécurité
		1. Identifie l'objet de l'étude
		2. Identifie les participants 
		3. Recenser les missions, valeurs métiers et bien supports
		4. Identifier les événements redoutés et l'impact des dégâts
		5. Définir le socle de sécurité et les écarts avec la réalité 
	2. Sources de risque
	3. Scénarios stratégiques
	4. Scénarios opérationnels
	5. Traitement du risque
		1. Synthétiser les scénarios à risque
		2. Définir stratégie de traitement du risques et les mesures déployer
		3. Evaluer et documenter les risques résiduels
		4. Mettre en place un cadre et suivi des risques
# 1) Cadrage et socle de sécurité
## Objectifs
1. Identifie l'objet de l'étude
2. Identifie les participants 
3. Recenser les missions, valeurs métiers et bien supports
4. Identifier les événements redoutés et leur niveau de gravité
5. Définir le socle de sécurité et les écarts avec la réalité 
## Terminologie 
* **Participants** : Personnes impliqués dans l'étude (employé, responsable)
* **Missions** : Objectifs et fonctions du système étudié
- **Valeurs métiers** : Informations et processus essentiels qui définissent le cœur de l'activité d'une entreprise et qu'il est impératif de protéger. En gros tout ce qui a de la valeur pour un organisme
	- **Exemple** : Service spécifique, type de données, résultats de travaux, stratégie de développement ... 
- **Biens supports** : Actifs qui soutiennent et permettent la réalisation des missions et la protection des valeurs métier de l'entreprise
* **Socle de sécurité et écarts** : Ecart entre les mesures de sécurité nécessaires (ou souhaitées) et la réalité du SI actuel.
## Eléments à produire 
1. Cadrage de l'étude
	* Participants avec matrice RACI
	* Périmètre métier : Les métiers et personnes qui dépendent de ce SI
	* Périmètre technique : L'architecture, technologies, flux
2. Evènements redoutés et leur niveau de gravité
3. Socle de sécurité : 
	* Mesures de sécurité applicables pour limiter les risques
	* Etat du SI
	* Identification des écarts
## Etape 1 : Cadrage de l'étude 

### Périmètre métier et technique 
| MISSIONS                                        | MISSION 1         |
|-------------------------------------------------|-------------------|
| DÉNOMINATION DE LA VALEUR MÉTIER                | DEPARTEMENT,SI,Objectifs   |            |
| NATURE DE LA VALEUR MÉTIER  |              PROCESSES/INFORMATION
| DESCRIPTION                                     |OBJECTIFS VALEUR METIER (listing)                   |                 |                  |
| ENTITÉ OU PERSONNE RESPONSABLE (INTERNE / EXTERNE)  | RESPONSABLE MISSION             |                 |                  |
| DÉNOMINATION DU / DES BIEN(S) SUPPORT(S) ASSOCIÉ(S) | SERVEUR/SYSTEME |
| DESCRIPTION                                     | UTILITE DU BIEN SUPPORT DANS MISSION                  |                 |                  |
| ENTITÉ OU PERSONNE RESPONSABLE (INTERNE / EXTERNE)  | RESPONSABLE BIEN SUPPORT              |                 |                  |

### Questions à poser 
1. A quoi sert l'objet de l'étude dans l'organisme
2. Quels sont les processus et informations permettant à l'objet d'étude de fonctionner
3. Quels sont les services/applications/réseaux/structures/personnes qui permettent de mener à bien le processus de l'objet d'étude
## Etape 2 : Evènements redoutés et leur niveau de gravité

### Echelles de gravité 

| Niveau de Gravité | Capacité opérationnelle | Performances de l'activité | Sécurité des personnes et des biens | Facilité de surmontabilité | Dégradation du fonctionnement |
|-------------------|-------------------------|----------------------------|------------------------------------|-----------------------------|-------------------------------|
| CRITIQUE (4)      | Incapacité              | Impacts majeurs           | Impacts majeurs                    | Difficilement surmontable   | Forte dégradation             |
| GRAVE (3)         | Assurée avec impacts    | Forte dégradation         | Éventuels impacts                  | Surmontable                 | Dégradation                   |
| SIGNIFICATIVE (2) | Assurée                | Dégradation               | Aucun impact                       | Quelques difficultés        | Fonctionnement dégradé        |
| MINEURE (1)       | Assurée                | Aucun impact              | Aucun impact                       | Sans grandes difficultés    | Aucune dégradation            |

1. **Capacité opérationnelle de la société** : Capacité de la société à continuer à fonctionner normalement ou à assurer son activité.
2. **Performances de l'activité** : Niveau de performance ou d'efficacité de l'activité de l'entreprise.
3. **Sécurité des personnes et des biens** : Sécurité physique des individus et des propriétés matérielles.
4. **Facilité de surmontabilité** : Facilité avec laquelle la société peut surmonter la situation ou les défis présentés.
5. **Dégradation du fonctionnement** : Façon dont le fonctionnement normal de la société est affecté, que ce soit légèrement ou gravement.

### Catégories d'impact 

| Catégorie d'impact                                       | Conséquences types                                                                                                                                      | Exemples |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|----------|
| Impacts sur les missions et services de l'organismes | Conséquences sur la réalisation des missions et services.      | Incapacité à fournir un service, dégradation de performances opérationnelles, retards, etc. |
| Impacts sur la capacité de développement ou de décision | Conséquences sur la liberté de décider.                         | Perte de souveraineté, limitation de l'indépendance de jugement, etc. |
| Impacts sur le lien social interne                   | Conséquences sur la qualité des liens sociaux.                          | Perte de confiance des employés, exacerbation de tensions, etc. |
| Impacts sur le patrimoine intellectuel ou culturel   | Conséquences sur les connaissances non-explicites.                  | Perte de mémoire de l'entreprise, perte de savoir-faire, etc. |
| Impacts sur la sécurité ou sur la santé des personnes | Conséquences sur l'intégrité physique de personnes.                                        | Accident du travail, maladie professionnelle, etc. |
| Impacts matériels                                    | Dégâts matériels ou destruction de biens supports.                        | Destruction de locaux, endommagement de moyens de production, etc. |
| Impacts sur l'environnement                          | Conséquences écologiques.                                        | Contamination radiologique, rejet de polluants, etc. |
| Impacts financiers                                   | Conséquences pécuniaires.                                                                 | Perte de chiffre d'affaire, dépenses imprévues, etc. |
| Impacts juridiques                                   | Conséquences suite à une non-conformité.                                                     | Procès, amende, condamnation d'un dirigeant, etc. |
| Impacts sur l'image et la confiance                  | Conséquences sur l'image de l’organisation.                                        | Publication d’articles négatifs, perte de crédibilité, etc. |


### Evénements redoutés 
| Valeurs Métier          | Événements Redoutés                | Catégorie d'impacts       | Gravité  |
|-------------------------|------------------------------------|----------------------------|----------|
| Base de données clients | Altération des informations                | Sécurité ou la santé des personnes            | 1   |
| Site Web                | Fuite d'informations                       | Image et confiance              | 2  |
| Processus de facturation| Perte/Destruction d'informations | Financier               | 3   |
| R&D                     | Interruption des services    | Missions et services de l'organismes            | 4 |
| Système de paiement     | Fraude                             | Coûts de developpement                  | 4 |
| Système de paiement     | Fraude                             | Juridiques                  | 4 |

### Tableau final 
| VALEUR MÉTIER | ÉVÉNEMENT REDOUTÉ | CATÉGORIES D'IMPACT | GRAVITÉ |
|---------------|-------------------|---------------------|---------|
| **Département**      | Description de l'événement 1 | - Impact type 1<br>- Impact type 2<br>- Impact type 3 | X |
| **Système cible**      | Description de l'événement 2 | - Impact type 4<br>- Impact type 5 | X |
| **Type d'informations**      | Description de l'événement 3 | - Impact type 6<br>- Impact type 7 | X |
| **Objectifs**      | Description de l'événement 4 | - Impact type 6<br>- Impact type 5 | X |

## Etape 3 : Déterminer socle de sécurité 

### Pyramide du risque numérique 
1. Lister les principes de base et hygiène
	* [Recommandation ANSSI](https://www.ssi.gouv.fr/administration/bonnes-pratiques/)
	* Règles sécurité interne à l'organisation
1. Lister les mesures réglementaire et normatif
	* Normes ISO 27000
	* [NIS2](https://www.ssi.gouv.fr/directive-nis-2/)
	* [RGPD](https://www.ssi.gouv.fr/administration/reglementation/rgpd-renforcer-la-securite-des-donnees-a-caractere-personnel/)
1. Lister les mesures de sécurité à mettre en place spécifiques à l'objet de l'étude et aux scénarios redoutés
### Tableau socle de sécurité 
| TYPE DE RÉFÉRENTIEL | NOM DU RÉFÉRENTIEL | ÉTAT D'APPLICATION | ÉCARTS | JUSTIFICATION DES ÉCARTS |
|--------------------|-------------------|-------------------|-------|-------------------------|
| Règles d'hygiène informatique et bonnes pratiques | Guide d'hygiène informatique de l'ANSSI | Appliqué avec restrictions | - Règle 8 : Identifier nommément chaque personne accédant au système et distinguer les rôles<br>- Règle 37 : définir et appliquer une politique de sauvegarde des composants critiques | - Existence d'un compte admin non nommément pour l'administration de l'ERP (solution propriétaire ne permettant pas l'administration par un autre compte)<br>- Politique de sauvegarde en cours de rédaction par un groupe de travail |

# 5) Traitement du risque 
## Objectifs
1. Synthétiser les scénarios à risques et les décisions de traitement avec les mesures
2. Evaluer et documenter les risques résiduels
3. Mettre en place un cadre et suivi des risques
## Etape 1 : Synthétiser les scénarios à risques et les décisions de traitement avec les mesures

### Niveaux de risques et les actions relier 

| NIVEAU DE RISQUE | ACCEPTABILITÉ DU RISQUE       | INTITULÉ DES DÉCISIONS ET DES ACTIONS                                                                 |
|------------------|-------------------------------|-------------------------------------------------------------------------------------------------------|
| Faible           | Acceptable en l'état          | Aucune action n'est à entreprendre                                                                     |
| Moyen            | Tolérable sous contrôle      | Un suivi en termes de gestion du risque est à mener et des actions sont à mettre en place dans le cadre d'une amélioration continue sur le moyen et long terme |
| Élevé            | Inacceptable                  | Des mesures de réduction du risque doivent impérativement être prises à court terme. Dans le cas contraire, tout ou partie de l'activité sera refusé          |

### Scénarios de risques 
* Représenter sur un graphique différents scénarios en fonction de 2 échelles : gravité et vraisemblance
* Ajouter le niveau de risques par couleurs (vert, orange, rouge) au tableau de synthèse des scénarios de risque

| GRAVITÉ \ VRAISEMBLANCE | 1 | 2 | 3 | 4 |
|-------------------------|---|---|---|---|
| 4                       |   |   | R4| R5|
| 3                       | R2| R1| R3|   |
| 2                       |   |   |   |   |
| 1                       |   |   |   |   |
* **R1** : Description d'un scénario 
* **R2** : Description d'un scénario 
* **R3** : Description d'un scénario 
* **R4** : Description d'un scénario 
* **R5** : Description d'un scénario 
### Plan d’amélioration continue de la sécurité (PACS)

* Produire 3 tableau différents 
	* Mesures de sécurité concernant la gouvernance
	* Mesures de sécurité concernant la protection
	* Mesures de sécurité concernant la défense
	* Mesures de sécurité concernant la résilience

| MESURE DE SÉCURITÉ                                                                                   | SCÉNARIOS DE RISQUES ASSOCIÉS | RESPONSABLE       | FREINS ET DIFFICULTÉS DE MISE EN ŒUVRE                                   | COÛT / COMPLEXITÉ | ÉCHEANCE | STATUT    |
|------------------------------------------------------------------------------------------------------|-------------------------------|--------------------|------------------------------------------------------------------------|------------------|----------|-----------|
| Mesure 1                            | R1                           | RSSI              | FREINS POSSIBLES                                        | + - +++             | 6 mois   | {En cours| Terminé |A lancer}  |


## Etape 2 : Evaluer et documenter les risques résiduels

### Résumé du risque résiduel:

| Catégories                                                    | Éléments                                                                                         |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| **Description et analyse du risque résiduel**                 | - **Description sommaire (dont impacts à craindre)**<br>- **Vulnérabilités résiduelles susceptibles d'être exploitées par la source de risque**<br>- **Autres causes ou facteurs aggravants (négligence, erreur, concours de circonstance, etc.)** |
| **Événements redoutés concernés**                             | - Événement redouté 1<br>- Événement redouté 2                                                    |
| **Mesures de traitement du risque existantes et complémentaires** | - Mesure 1<br>- Mesure 2                                                                           |
| **Gestion du risque résiduel**                                | - Mesures particulières de suivi et de contrôle du risque résiduel.                                |

### Évaluation du risque résiduel:

|                          | Initiale | Résiduelle |
|--------------------------|:--------:|:----------:|
| **Gravité**              |          |            |
| **Vraisemblance**        |          |            |
| **Niveau de risque**     |          |            |

# Résume des informations à collecter 

| Étape | Informations à Collecter |
|-------|--------------------------|
| 1. Définir les Responsables et Acteurs du Service | - Noms et fonctions des responsables (fonctionnel, technique).<br>- Contacts des acteurs clés (DSI, administrateurs de sécurité, utilisateurs principaux).<br>- Rôles et responsabilités spécifiques dans le projet. |
| 2. Définir le Périmètre d'Analyse | - Nom et description des applications et systèmes impliqués.<br>- Nombre et nature des interconnexions avec d'autres systèmes.<br>- Thèmes et domaines fonctionnels couverts.<br>- Limites claires de l'analyse. |
| 3. Collecter les Documentations du Système | - Plans architecturaux du système (logiques et physiques).<br>- Diagrammes des flux de données.<br>- Architecture réseau et topologie.<br>- Détails sur les applications déployées sur les serveurs.<br>- Logique de fonctionnement et séquence des processus. |
| 4. Définir pour Chaque Système les Serveurs, Logiciels, Type de Données, Type d'Utilisateur | - Liste des serveurs (physiques et virtuels) utilisés.<br>- Détails des logiciels et applications (versions, configurations).<br>- Types de données traitées.<br>- Catégories d'utilisateurs. |
| 5. Identifier les Menaces Potentielles et les Vulnérabilités Type du Système | - Inventaire des menaces potentielles.<br>- Liste des vulnérabilités connues ou suspectées.<br>- Historique des incidents de sécurité antérieurs. |
| 6. Identifier les Types d'Attaques Susceptibles d'Affecter le Système | - Types d'attaques courantes dans des environnements similaires.<br>- Méthodes d'exploitation des vulnérabilités spécifiques.<br>- Rapports d'analyses de sécurité ou d'incidents précédents. |
| 7. Classer par Ordre de Gravité les Événements Redoutés et les Probabilités | - Liste des événements redoutés avec estimation de leur gravité et probabilité.<br>- Critères d'évaluation pour la gravité et la probabilité. |
| 8. Lister et Examiner les Mesures de Sécurité Actuelles | - Inventaire des mesures de sécurité en place.<br>- Politiques de sécurité et procédures opérationnelles.<br>- Résultats des derniers audits de sécurité. |
| 9. Proposer des Mesures en Fonction des Vulnérabilités Non Couvertes par les Mesures Actuelles | - Analyse des lacunes dans les mesures existantes.<br>- Suggestions de mesures de sécurité complémentaires.<br>- Évaluation des coûts et de la faisabilité pour chaque mesure. |
| 10. Définir un Responsable d'Application pour Intégrer les Mesures de Façon Progressive | - Nomination d'un responsable de projet.<br>- Planification détaillée pour l'intégration des mesures.<br>- Mécanismes de reporting et de suivi pour le responsable. |
| 11. Définir l'Ensemble des Mesures de Sécurité Manquantes et à Déployer | - Liste complète des mesures de sécurité à mettre en place.<br>- Calendrier de déploiement.<br>- Plan de formation et de sensibilisation pour les utilisateurs. |
| 12. Analyser la Réduction de la Probabilité des Risques avec les Nouvelles Mesures | - Méthodologie pour évaluer l'efficacité des mesures.<br>- Critères pour mesurer la réduction des risques.<br>- Plan pour le suivi continu et l'évaluation des risques résiduels. |

