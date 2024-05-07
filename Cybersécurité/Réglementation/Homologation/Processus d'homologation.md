
# Partie 1 : Stratégie d'homologation
## Etape 1 : Définir le système à homologuer 
* Objectif : Préciser le référentiel réglementaire applicable et délimiter le périmètre du système à homologuer.
- [ ] Préciser la raison et le référentiel réglementaire de l'homologation : 
	- [ ] l’instruction générale interministérielle no 1300 (IGI 1300), pour les systèmes traitant d’informations classifiées de défense ; 
	- [ ] Référentiel général de sécurité (RGS), pour les systèmes permettant des échanges entre une autorité administrative et les usagers ou entre autorités administratives ; 
	- [ ] Politique de sécurité des systèmes d’information de l’État (PSSIE), pour les systèmes des administrations de l’État
- [ ] Délimiter le périmètre du système à homologuer: 
	- [ ] Eléments fonctionnels et d’organisation : 
		- [ ] fonctionnalités du système, 
		- [ ] type d’utilisateurs, 
		- [ ] contexte et règles d’emploi, 
		- [ ] procédures formalisées, 
		- [ ] conditions d’emploi des produits de sécurité, 
		- [ ] gestion des droits, dispositifs de détection et de gestion des incidents ; 
	- [ ] Eléments techniques : 
		- [ ] architecture du système (en précisant notamment les interconnexions avec d’autres systèmes), 
		- [ ] possibilité d’utilisation de supports amovibles, 
		- [ ] d’accès à distance ou de cloisonnement, 
		- [ ] mécanismes de maintenance, d’exploitation ou de télégestion du système, notamment lorsque ces opérations sont effectuées par des prestataires externes ; 
	- [ ] Périmètre géographique et physique : localisations géographiques et caractéristiques des locaux
## Etape 2 : Stratégie et démarche d'homologation
* Objectif : Définir le niveau de profondeur de la démarche d’homologation
- [ ] Autodiagnostiquer les besoins de sécurité du système et le niveau de maturité SSI de l’organisme
	- [ ] ***1 - Document à remplir*** : [Evaluation-de-la-demarche-dhomologation](https://cyber.gouv.fr/sites/default/files/2014/06/evaluation-de-la-demarche-dhomologation-2017_v2.xls)
- [ ] En déduire la démarche appropriée

| Niveau | Description |
|--------|-------------|
| **Pianissimo** | Démarche autonome a minima, que l’autorité d’homologation peut mener sans recours à une assistance conseil externe, par l’application des outils et des indications donnés dans le présent guide. |
| **Mezzo Piano** | Démarche autonome approfondie, que l’autorité d’homologation peut mener sans recours à une assistance conseil externe, par l’application des outils et des indications donnés dans le présent guide et ses ressources internes. |
| **Mezzo Forte** | Démarche assistée approfondie, que l’autorité d’homologation mène avec l’aide d’une assistance conseil externe, en plus des outils et des indications données dans le présent guide. |
| **Forte** | Le niveau de maturité de l’organisme en matière de sécurité des systèmes d’information dispense l’autorité d’homologation de la lecture du présent guide qui apporte des outils qu’elle maîtrise déjà. Cette démarche n’est donc pas traitée dans ce guide. |

## Etape 3 : Définir les contributeurs de l'homologation
* Objectif : Identifier l’ensemble des acteurs de l’homologation et bien définir leur rôle
- [ ] Définir l'ensemble des rôles suivants : 
	- [ ] L’autorité d’homologation (AH)
	- [ ] La commission d’homologation
	- [ ] Les acteurs de l’homologation : 
		- [ ] Le RSSI
		- [ ] Le responsable d’exploitation du système
		- [ ] Les prestataires
		- [ ] Les systèmes interconnectés
## Etape 4 : Recueillir et présenter les informations
* Objectif : Inventorier le contenu du dossier d’homologation/documentations et définir le planning de la démarche
- [ ] Rassembler à partir de la méthode choisie l'ensemble des documents obligatoires pour le dossier d'homologation
- [ ] Définir un planning pour l'avancement des étapes 
	1. Lancement de la procédure d’homologation (par exemple date de formalisation de la stratégie d’homologation) ; 
	2. début et de fin de l’analyse des risques (dates des entretiens avec l’autorité) 
	3. remise des différents documents du dossier d’homologation (cf. section suivante) 
	4. engagements liés à d’éventuels contrats avec des prestataires impliqués dans le système (hébergeurs, fournisseurs de sous-systèmes, d’applications…) 
	5. réunions de la commission d’homologation ; 
	6. audits éventuels sur les composants du système (techniques ou organisationnels), logiciels plates-formes matérielles, interfaces réseaux 
	7. homologation du système 
	8. mise en service du système.
- [ ] Créer référentiel documentaire nécessaire détaillé en fonction du service : ***Référentiel documentaire.xls***
- [ ] Envoyer la liste des documentations nécessaires aux équipes responsables du service
- [ ] Faire des retours sur les documentations manquantes en fonction de leur importance
* ***2 - Document final à remplir*** : [Stratégie homologation](https://cyber.gouv.fr/sites/default/files/document/Strat%C3%A9gie-Homologation-propostion.doc)

# Partie 2 : Maitrise des risques 
## Etape 5 : Analyse de risques
* Objectif : Identifier et ordonner les risques qui pèsent sur le système
- [ ] Partir de la liste des menaces courantes et écarter celles qui ne sont pas pertinentes dans le contexte du système d’information étudié ; 
- [ ] Pour chaque menace conservée, déterminez un ou plusieurs biens essentiels qui pourraient être affectés. (informations traitées au sein du système, ainsi que leurs processus de traitement)
	- [ ] Liste menaces courantes :
	- [ ] Liste bien essentiels : 
- [ ] Pour chaque lien identifié entre une menace et un bien essentiel, décrivez l’impact négatif sur la disponibilité, l’intégrité ou la confidentialité de ce bien essentiel. Vous obtenez un scénario de risque. 
- [ ] Hiérarchisez les scénarios de risque obtenus, en identifiant les plus probables et ceux dont l’impact est le plus pénalisant. 
- [ ] Si un scénario de risque plausible aboutit à un impact très fort, cela signifie que le besoin de sécurité évalué lors de la deuxième étape a été sous-évalué. Envisagez alors une démarche plus complète, de type Mezzo Piano ou Mezzo Forte
- [ ] Identifier les mesures de sécurité
	- [ ] Guide des 40 règles d’hygiène informatique
	- [ ] ISO 270XX
	- [ ] Autres référentiels de sécurité qui proposent des catalogues de mesures
* ***3 - Document final à remplir*** : [Analyse de risques EBIOS](https://cyber.gouv.fr/sites/default/files/2014/06/EBIOS-Canevas-Etude-proposition.doc)
* ***4 - Document à produire*** :  [Plan de sécurité (PDS)]
* ***5 - Document final à remplir*** :[ Procédures-exploitation-sécurité (PES)](https://cyber.gouv.fr/sites/default/files/document/Proc%C3%A9dures-exploitation-s%C3%A9curit%C3%A9-proposition.doc)

## Etape 6 : Vérification et audit de sécurité
* Objectif : Mesurer l’écart entre les objectifs et la réalité.
- [ ] Définition du périmètre du contrôle 
	- [ ] Audit formalisé sur un système dont le périmètre doit être soigneusement délimité par l’autorité d’homologation. 
	- [ ] Les éléments à contrôler peuvent être de différente nature (code source, configuration des équipements, architecture du système, organisation mise en place, etc.).
- [ ] Rapport d'audit contenant  : 
	- [ ] L'évolution des menaces sur le système ; 
	- [ ] La découverte éventuelle de nouvelles vulnérabilités ; 
	- [ ] La préconisation de mesures correctrices, le cas échéant. 

* ***5 - Document à produire*** : [Rapport-audits]

## Etape 7 : Plan d’action pour réduire le risques
* Objectif : Définir un plan d’action pour amener le risque identifié à un niveau acceptable
- [ ] Demander à l'autorité d'homologation leur avis sur les possibilités pour chaque scénario de risque
	- [ ] L’éviter : changer le contexte de telle sorte qu’on n’y soit plus exposé ; 
	- [ ] Le réduire : prendre des mesures de sécurité pour diminuer l’impact et/ou la vraisemblance ; 
	- [ ] L’assumer : en supporter les conséquences éventuelles sans prendre de mesure de sécurité supplémentaire ; 
	- [ ] Le transférer : partager les pertes occasionnées par un sinistre ou faire assumer la responsabilité à un tiers.
- [ ] Définir les mesures à appliquer pour chaque scénarios de risques et définir le risques résiduels après l'application de la mesures
	- [ ] ***Document à remplir*** : [Plan d'action](https://cyber.gouv.fr/sites/default/files/2014/06/Plan-action-proposition.xls)
	- [ ] ***Document à remplir***: [Risques résiduels](https://cyber.gouv.fr/sites/default/files/document/Suivi-risques-r%C3%A9siduels-proposition.xls)
- [ ] Faire valider le nouveau niveau de risques auprès de la commission 
	- [ ] ***Document à remplir*** : [Avis-homologation](https://cyber.gouv.fr/sites/default/files/2014/06/Avis-commission-homologation-proposition.doc)
# Partie 3 : Décision et suivi d'homologation
## Etape 8 : Réaliser la décision d’homologation
* Objectif : Concrétiser la décision d’homologation par une attestation formelle autorisant, du point de vue de la sécurité, l’exploitation du système
- [ ] ***Document à remplir*** : [Décision-homologation](https://cyber.gouv.fr/sites/default/files/document/D%C3%A9cision-homologation-proposition.doc)


# Résume des documents obligatoire
- [ ] ***0 - Stratégie d'homologation***
- [ ] ***1 - Référentiel de sécurité***
- [ ] ***2 - Analyse de risques***
- [ ] ***4 - Objectifs et plan de sécurité (PDS)*** =  Ce qu'on aimerait mettre en place comme standards, objectifs de sécurité 
- [ ] ***5 - Procédures-exploitation-sécurité (PES)*** = Les mesures et contrôles actuellement déployés sur le système
- [ ] ***8 - Résultat d'audit***
- [ ] ***7 - Plan d'action*** = Actions et mesures spécifique pour mieux répondre au PDS et réduire les risques
- [ ] ***6 - Tableau risques résiduels*** = Comparatif des risques avec l'application du plan d'action
# Résume du processus
1. Définir stratégie d'homologation
2. Liste des référentiel de sécurité
3. Récolte d'informations/documentation du SI
4. Analyse de risques et déduction des scénarios triés par vraisemblance/gravité
5. Rassemble l'état actuelle du SI dans le PES avec les mesures de sécurité actuellement déployés sur le système
6. Audité le SI pour vérifier le bon déploiement du PES (optionnel)
7. Demander à la commission la validation des scénarios de risques
8. Si risque rejeté, définir plan d'action qui viens réduire les scénarios à risques via des mesures spécifique
9. Produire tableau de risques résiduels à représenter à la commission pour leur validation
10. Décision de l'homologation du système
