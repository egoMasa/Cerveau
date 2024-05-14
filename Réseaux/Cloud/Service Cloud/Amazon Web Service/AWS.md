# Sommaire [AWS Academy Introduction to Cloud: Semester 1](https://awsacademy.instructure.com/courses/78245)
0. Structure et fonctions du cloud
	1. Présentation du cloud computing
	2. Solutions IaaS, PaaS et SaaS
1. Stockage et partage de contenu dans le cloud
	1. Console AWS
		1. Services AWS
		2. Amazon Virtual Private Cloud
	2. Serveurs virtuels
		3. Amazon EC2
		4. Amazon S3
	3. Diffusion de contenu
		1. CloudFront pour les compartiments S3
		2. AWS Direct Connect
		3. Amazon CloudFront
	4. Stockage virtuel
		1. Amazon EBS
		2. Attacher un volume EBS à une instance EC2
		3. Catégories de types de volume EBS
2. Sécurisation et surveillance dans le cloud
	1. Sécurité I
		1. Sécurité dans le cloud AWS
		2. Rôles IAM
		3. Groupes de sécurité
		4. Groupes d’utilisateurs IAM
		5. Utilisateur racine d’un compte AWS
		6. Types d’autorisations de sécurité
		7. AWS Identity and Access Management (IAM)
	2. Sécurité II
		1. Amazon Inspector
		2. Amazon Shield
		3. Types courants d’attaques DDos
		4. AWS WAF
		5. AWS Artifact
	3. Surveillance du cloud
		1. AWS Config
		2. AWS CloudTrail
		3. Amazon CloudWatch
		4. Amazon Simple Notification
3. Gestion des données
	1. Base de données
		1. Amazon Relational Database Service
		2. Amazon Redshift
		3. Amazon Aurora
		4. Base de données clé-valeur
		5. Entrepôts de données
		6. Types d’instances RDS
		7. Amazon DynamoDB
	2. Équilibreurs de charge et mise en cache
		1. Elastic Load Balancing
		2. Avantages liés à la mise en cache
		3. Amazon ElastiCache
	3. Elastic Beanstalk et CloudFormation
		1. AWS CloudFormation
		2. AWS Elastic Beanstalk
4. Gestion et optimisation des fonctions du cloud
	1. Nouvelles technologies dans le cloud
		1. AWS DeepRacer
		2. Amazon SageMaker
		3. AWS DeepLens
	2. Facturation et support
		1. Concepts clés d’AWS Organizations
		2. AWS Organizations
		3. Comparatif des programmes de support AWS
		4. AWS Enterprise Support
	3. Autres fonctions du cloud
		1. Amazon Athena
		2. Amazon Macie
		3. Amazon Blockchain
	4. Optimiser le cloud avec AWS CDK
		1. Constructs
		2. AWS CDK


# Sommaire [AWS Academy Cloud Foundations](https://awsacademy.instructure.com/courses/78117)
1. Concepts du cloud
	1. Introduction au cloud computing
	2. Avantages du cloud computing
	3. Introduction à Amazon Web Services (AWS)
	4. Framework d’adoption d’AWS Cloud (AWS CAF)
2. Couts et facturation du Cloud
	1. Bases de la tarification
	2. Coût total de possession
	3. AWS Organizations
	4. Facturation et gestion des coûts AWS
	5. Support technique
	6. Calculateur de prix AWS
3. Infrastructure mondiale AWS
	1. Infrastructure mondiale AWS
	2. Services et catégories de services AWS
	3. Console de gestion AWS
4. Sécurité du cloud AWS
	1. Modèle de responsabilité partagée AWS 
	2. AWS Identity and Access Management (IAM)
	3. Sécurisation d’un nouveau compte AWS
	4. Sécurisation des comptes
	5. Sécurisation des données sur AWS
	6. Efforts pour assurer la conformité
	7. Services et ressources de sécurité supplémentaires
5. Mise en réseau et diffusion de contenu
	1. Bases de la mise en réseau
	2. Amazon Virtual Private Cloud (Amazon VPC)
	3. Mise en réseau de VPC
	4. Sécurité de VPC
	5. Amazon Route 53
	6. Amazon CloudFront
6. Calcul
	1. Présentation des services de calcul
	2. Amazon EC2
	3. Optimisation des coûts Amazon EC2
	4. Services de conteneurs
	5. Introduction à AWS Lambda
	6. Introduction à AWS Elastic Beanstalk
7. Stockage
	1. Amazon Elastic Block Store (Amazon EBS)
	2. Amazon Simple Storage Service (AmazonS3)
	3. Amazon Elastic File System (Amazon EFS)
	4. Amazon Simple Storage Service Glacier
8. Bases de données
	1. Amazon Relational Database Service (Amazon RDS)
	2. Amazon Dynamo DB
	3. Amazon Redshift
	4. Amazon Aurora
9. Architecture cloud
	1. Cadre AWS Well-Architected
	2. Fiabilité et haute disponibilité
	3. AWS Trusted Advisor
10. Auto Scalling et surveillance
	1. Elastic Load Balancing
	2. Amazon Cloud Watch
	3. Amazon EC2 Auto Scaling

# 1. Concepts du cloud
## 1.0 Objectifs
À la fin de ce module, vous devriez être en mesure d’effectuer les tâches suivantes
* Définir les différents types de cloud computing
* Décrire six avantages du cloud computing
* Identifier les principales catégories de services AWS et les services de base
* Examiner le framework d’adoption d’AWS Cloud (AWS CAF)

## 1.1 Introduction au Cloud Computing

### Définition du Cloud Computing
Le cloud computing consiste à déployer à la demande des ressources informatiques comme la puissance de calcul, le stockage, les bases de données et des applications via Internet, avec une tarification basée sur l'utilisation. Ces ressources, hébergées dans des centres de données à travers le monde, sont gérées par des fournisseurs de services cloud tels qu'AWS. Elles permettent de construire des solutions flexibles pour atteindre des objectifs métier spécifiques.

### Comparaison avec l'informatique traditionnelle
- **Informatique traditionnelle** : Considérée comme du matériel, nécessitant espace, personnel, sécurité physique et planification. Les coûts initiaux sont élevés, et l'acquisition, la mise en service, et la maintenance sont longues et coûteuses. La capacité doit être prévue pour les pics théoriques, entraînant des coûts pour des ressources souvent inutilisées.
- **Cloud computing** : Permet de considérer et d'utiliser l'infrastructure comme un logiciel. Ce modèle est flexible, permettant une sélection, une mise en service et une résiliation des ressources à la demande, et une facturation uniquement pour les ressources utilisées.

### Modèles de Service Cloud
1. **Infrastructure en tant que Service (IaaS)** : Offre le plus haut niveau de flexibilité et de contrôle, avec accès à des fonctionnalités de mise en réseau, des ordinateurs et du stockage.
2. **Plateforme en tant que Service (PaaS)** : Permet de se concentrer sur le déploiement et la gestion des applications, sans gérer l'infrastructure sous-jacente.
3. **Logiciel en tant que Service (SaaS)** : Fournit un produit complet géré par le fournisseur, typiquement des applications destinées aux utilisateurs finaux, comme une messagerie web.

### Modèles de déploiement du Cloud Computing
1. **Cloud** : Les applications sont entièrement déployées et gérées dans le cloud, optimisant les avantages de cette technologie.
2. **Hybride** : Combine ressources cloud et infrastructures existantes pour étendre et accroître les capacités informatiques.
3. **Sur site (ou Cloud privé)** : Utilise la virtualisation et des outils de gestion d'applications pour simuler le cloud computing sur des infrastructures propriétaires.

### Similitudes entre AWS et l'informatique traditionnelle
- **Sécurité et gestion** : Les groupes de sécurité AWS, les ACL réseau et AWS IAM sont similaires aux pare-feu, ACL, et administrateurs traditionnels.
- **Réseautage** : Elastic Load Balancing et Amazon VPC sont comparables aux routeurs et commutateurs.
- **Stockage et traitement** : Les AMI et les instances Amazon EC2 agissent comme des serveurs traditionnels, tandis que Amazon EBS, EFS, S3 et RDS sont similaires aux solutions de stockage et bases de données traditionnelles.

AWS offre ainsi une flexibilité et des capacités qui reflètent mais surpassent celles des centres de données traditionnels.

### Points cléfs
Voici quelques points clés à retenir de cette section du module:•Le cloud computing est la diffusion de ressources informatiques à la demande via Internet, avec une tarification en fonction de l’utilisation.•Le cloud computing vous permet de considérer (et d’utiliser) votre infrastructure en tant que logiciel.•Les trois modèles de services cloud sont IaaS, PaaS et SaaS.•Il existe trois modèles de déploiement cloud: cloud, hybride et sur site ou privé.•Les services AWS analogues à l’espace informatique traditionnel sur site sont nombreux
## 1.2 Avantages du Cloud Computing

### Transformer des dépenses d’investissement en coûts variables
- **Rationalisation des coûts**: Le passage de dépenses en capital (CAPEX) pour des actifs physiques à des coûts variables aligne vos dépenses avec la consommation réelle de ressources.
- **Flexibilité et économie**: Évite les investissements massifs en infrastructures avant de déterminer leur utilité. Vous payez seulement pour ce que vous utilisez, économisant ainsi sur les coûts technologiques et réduisant les délais de mise en œuvre des nouvelles applications.

### Importantes économies d’échelle
- **Réduction des coûts**: Grâce à l'utilisation mutualisée des ressources par des milliers de clients, AWS et d'autres fournisseurs de cloud peuvent atteindre des économies d'échelle, réduisant ainsi les tarifs.

### Plus besoin de deviner la capacité nécessaire
- **Adaptabilité**: Élimine la nécessité de prévoir précisément les besoins en infrastructures, permettant une adaptation flexible aux besoins réels. Vous pouvez augmenter ou réduire les ressources rapidement et efficacement.

### Gain en vitesse et en agilité
- **Accès rapide aux ressources**: Les nouvelles ressources informatiques sont à quelques clics de distance, ce qui réduit significativement les délais de mise à disposition pour les développeurs et augmente l'agilité organisationnelle.

### Finies les dépenses dédiées au fonctionnement et à la maintenance des centres de données
- **Concentration sur l'innovation**: Le cloud computing vous décharge des tâches de gestion de l'infrastructure, vous permettant de vous concentrer sur des initiatives stratégiques pour différencier votre entreprise.

### Déploiement à l’international en quelques minutes
- **Expansion globale simplifiée**: Permet un déploiement rapide de vos applications dans diverses régions AWS autour du monde, améliorant les temps de latence et l'expérience client à faible coût.


### Points cléfs
Les points clés à retenir de cette section du module sont les six avantages du cloud computing:•Transformer les dépenses d’investissement en coûts variables•Économies d’échelle importantes•Plus besoin de deviner la capacité nécessaire•Augmenter la vitesse et l’agilité•Finies les dépenses dédiées au fonctionnement et à la maintenance des centres de données•Déploiement international en quelques minutesAWS Training and CertificationModule 1 : Présentation des concepts du cloud© 2022 Amazon Web Services, Inc. or its affiliates. All rights reserved.26

## 1.3 Introduction à Amazon Web Services (AWS)

### Définition d'un service web
Un service web est un logiciel accessible via Internet ou des réseaux privés, utilisant des formats standardisés comme XML ou JSON pour l'échange de données. Il fonctionne indépendamment du système d'exploitation ou du langage de programmation et se décrit via un fichier de définition d'interface.

### Qu'est-ce que AWS?
Amazon Web Services (AWS) est une plateforme cloud qui offre un large éventail de produits basés sur le cloud. Ces services, qui incluent le calcul, le stockage, et la mise en réseau, sont accessibles à la demande et peuvent être facilement configurés pour s'adapter à l'évolution des besoins, optimisant ainsi les dépenses opérationnelles.

### Exemple de solution simple avec AWS
En utilisant AWS, vous pouvez par exemple développer une application de base de données. Les données sont envoyées à des instances Amazon EC2, agrégées et stockées dans Amazon S3. Amazon DynamoDB peut ensuite être utilisé pour indexer ces données, facilitant leur recherche sur une période donnée. Cette infrastructure peut être gérée via Amazon Virtual Private Cloud (Amazon VPC).

### Choix d'un service AWS selon vos besoins
AWS propose une variété de services de calcul adaptés à différents besoins :
- **Amazon EC2** : pour un contrôle complet sur les ressources.
- **AWS Lambda** : pour exécuter du code sans gérer de serveurs.
- **AWS Elastic Beanstalk** : pour le déploiement automatique d'applications web.
- **Amazon Lightsail** : pour des applications web simples.
- **AWS Batch** : pour des charges de travail par lots massives.
- **AWS Outposts** : pour exécuter l'infrastructure AWS localement.
- **Amazon ECS, EKS, ou AWS Fargate** : pour l'implémentation de conteneurs ou microservices.
- **VMware Cloud on AWS** : pour migrer une infrastructure de virtualisation vers AWS.
### Interaction avec AWS
Pour accéder et gérer les services AWS, vous pouvez utiliser :
- **AWS Management Console** : Une interface graphique pour la plupart des services AWS.
- **AWS CLI** : Une interface de ligne de commande pour automatiser les opérations via des scripts.
- **SDKs** : Des kits de développement logiciel disponibles dans divers langages pour intégrer et gérer les services AWS dans vos applications.

### Catégories de services AWS
Les services AWS sont répartis dans différentes catégories, chaque catégorie contenant un ou plusieurs services. Vous pouvez sélectionner les services souhaités dans ces différentes catégories pour créer vos solutions

|Catégorie|Services|
|---|---|
|**Analytics**|Analytique|
|**Integration**|Application Integration|
|**Augmented and Virtual Reality**|AR et VR|
|**Blockchain**|Blockchain|
|**Enterprise Applications**|Entreprise Applications|
|**Computing**|Calcul, Calcul utilisateur final|
|**Cost Management**|Coût Gestion|
|**Customer Engagement**|Engagement client|
|**Database**|Base de données|
|**Developer Tools**|Outils pour développeurs|
|**End User Computing**|Calcul utilisateur final|
|**Game Tech**|Game Tech|
|**IoT**|Internet des objets|
|**Machine Learning**|Machine Learning|
|**Management & Governance**|Gestion et gouvernance|
|**Media Services**|Services multimédias|
|**Migration & Transfer**|Migration et transfert|
|**Mobile**|Mobile|
|**Networking & Content Delivery**|Réseau et diffusion de contenu|
|**Robotics**|Robotique|
|**Satellite**|Satellite|
|**Security, Identity, & Compliance**|Sécurité, identité et conformité|
|**Storage**|Stockage|

### Services communs 
Basé sur la seconde image que vous avez téléchargée, je vais créer des tableaux en markdown pour chaque famille de services AWS affichée dans l'image. Voici le résumé pour chaque catégorie :

#### Services de calcul:
| Services AWS       |
|--------------------|
| Amazon EC2         |
| AWS Lambda         |
| AWS Elastic Beanstalk |
| Amazon EC2 Auto Scaling |
| Amazon ECS         |
| Amazon EKS         |
| Amazon ECR         |
| AWS Fargate        |

#### Services de stockage:
| Services AWS       |
|--------------------|
| Amazon S3          |
| Amazon S3 Glacier  |
| Amazon EFS         |
| Amazon EBS         |

#### Services de base de données:
| Services AWS       |
|--------------------|
| Amazon RDS         |
| Amazon DynamoDB    |
| Amazon Redshift    |
| Amazon Aurora      |

#### Services de mise en réseau et de diffusion de contenu:
| Services AWS       |
|--------------------|
| Amazon VPC         |
| Amazon Route 53    |
| Amazon CloudFront  |
| Elastic Load Balancing |

#### Services de sécurité, identité et conformité:
| Services AWS       |
|--------------------|
| AWS IAM            |
| Amazon Cognito     |
| AWS Shield         |
| AWS Artifact       |
| AWS KMS            |

#### Services de gouvernance:
| Services AWS       |
|--------------------|
| AWS Trusted Advisor |
| AWS CloudWatch     |
| AWS CloudTrail     |
| AWS Well-Architected Tool |
| AWS Auto Scaling   |
| Interface de ligne de commande AWS |
| AWS Config         |
| AWS Management Console |
| AWS Organizations  |

#### Services de gestion des coûts AWS:
| Services AWS       |
|--------------------|
| Rapport d'utilisation et de coût AWS |
| AWS Budgets        |
| AWS Cost Explorer  |

### Points cléfs
Voici les points clés à retenir de cette section du module:•AWS est une plateforme cloud sécurisée qui propose un large éventail de produits globaux basés sur le cloud, également appelés services, conçus pour interagir les uns avec les autres.•De nombreuses catégories de service AWS sont disponibles, chaque catégorie proposant une vaste sélection de services.•Choisissez un service en fonction des objectifs de votre entreprise et de vos besoins technologiques.•Il existe trois manières d’interagir avec les services AWS
## 1.4 Framework d’Adoption d’AWS Cloud (AWS CAF)

Le Cloud Computing offre de nombreux avantages, mais l'adoption du cloud ne se fait pas instantanément et implique l'alignement des personnes, des processus et de la technologie. Le framework AWS CAF a été créé pour aider les organisations à optimiser leur parcours d’adoption du cloud.

### Importance de l'Alignement
L'adoption du cloud nécessite que les entreprises envisagent des changements fondamentaux à travers toute l'organisation et obtiennent le soutien des parties prenantes internes et externes. AWS CAF aide à identifier les compétences et les lacunes en matière de processus et propose des approches pour intégrer le cloud computing dans les opérations de l'entreprise.

### Les Six Perspectives du AWS CAF
AWS CAF est organisé autour de six domaines d'intérêt, appelés perspectives, qui couvrent les aspects commerciaux et techniques de l'adoption du cloud.

#### Perspective d'Entreprise
- **Stakeholders**: Chefs d'entreprise, responsables financiers, stratégiques.
- **Objectif**: Créer un argumentaire solide pour l'adoption du cloud et hiérarchiser les initiatives.

#### Perspective de Personnes
- **Stakeholders**: Ressources humaines, gestion du personnel.
- **Objectif**: Évaluer les structures organisationnelles, les compétences requises, et identifier les lacunes pour prioriser la formation et les changements organisationnels.

#### Perspective de Gouvernance
- **Stakeholders**: DSI, architectes d'entreprise, gestionnaires de portefeuille.
- **Objectif**: Aligner les stratégies et objectifs informatiques avec ceux de l'entreprise pour maximiser la valeur et minimiser les risques.

#### Perspective de Plateforme
- **Stakeholders**: CTO, responsables informatiques, architectes de solutions.
- **Objectif**: Comprendre et décrire l'architecture des systèmes, incluant la migration vers le cloud et la mise en œuvre de nouvelles solutions.

#### Perspective de Sécurité
- **Stakeholders**: RSSI, responsables de la sécurité informatique.
- **Objectif**: Assurer que l'organisation atteint ses objectifs de sécurité avec une structure appropriée pour la sélection et la mise en œuvre des contrôles de sécurité.

#### Perspective d'Opérations
- **Stakeholders**: Responsables des opérations informatiques.
- **Objectif**: Définir les procédures opérationnelles, identifier les changements de processus et la formation nécessaire pour une adoption réussie du cloud.

### Conclusion
AWS CAF fournit des conseils structurés pour aider les organisations à naviguer dans la complexité de l'adoption du cloud, en assurant que toutes les parties de l'entreprise sont préparées et alignées pour cette transformation.



| Entreprise                        | Personnes                             | Gouvernance                                 | Plateforme                             | Sécurité                           | Opérations                                      |
| --------------------------------- | ------------------------------------- | ------------------------------------------- | -------------------------------------- | ---------------------------------- | ----------------------------------------------- |
| Financement informatique          | Gestion des ressources                | Gestion du portefeuille                     | Allocation du calcul                   | Gestion des identités et des accès | Surveillance des services                       |
| Stratégie informatique            | Gestion des intéressements            | Gestion de programme et de projet           | Allocation du réseau                   | Contrôle de détection              | Surveillance des performances des applications  |
| Réalisation des bénéfices         | Gestion de carrière                   | Evaluation des performances de l'entreprise | Allocation du stockage                 | Sécurité de l'infrastructure       | Gestion de l'inventaire des ressources          |
| Gestion des risques opérationnels | Gestion des informations              | Gestion des licences                        | Allocation des bases de données        | Protection des données             | Gestions des versions/gestion des modifications |
|                                   | Gestion du changement organisationnel |                                             | Architecture des systèmes et solutions | Réactions aux incidents            | Rapports et analyses                            |
|                                   |                                       |                                             | Développement d'applications           |                                    | Continuité de l'activité/Reprise après sinistre |
|                                   |                                       |                                             |                                        |                                    | Catalogue des services informatiques            |

### Points cléfs
•Pour la plupart des organisations, l’adoption du cloud n’est pas instantanée. Elle implique une stratégie et un alignement réfléchis et délibérés dans l’ensemble de l’organisation.•Le framework AWS CAF a été créé pour aider les organisations à développer des plans efficients et efficaces pour leur parcours d’adoption du cloud.•AWSCAF classe les conseils dans six domaines d’intérêt, appelés perspectives.•Les perspectives consistent en des ensembles decapacitéscommercialesoutechnologiquesqui relèventde la responsabilitédes principalesparties prenantes.

# 2. Coûts et facturation du Cloud

## 2.0 Objectifs
À la fin de ce module, vous serez en mesure d'effectuer les tâches suivantes:•Expliquer la politique de tarification d'AWS•Identifier les caractéristiques fondamentales de la tarification•Citer les éléments du coût total de possession•Discuter des résultats du Calculateur de prix AWS•Identifier comment configurer une structure organisationnelle qui simplifie la facturation et la visibilité des comptes pour examiner les données de coût•Identifier la fonctionnalité dans le tableau de bord de facturation AWS•Décrire comment utiliser les factures AWS, AWS Cost Explorer, AWS Budgets et le Rapport d'utilisation et de coût AWS•Identifier les différents plans et fonctions du support technique AWS
## 2.1 Bases de la tarification

### Modèle de tarification AWS
AWS facture principalement trois aspects : le calcul, le stockage, et le transfert de données sortantes. Bien que le transfert de données entrantes et entre services AWS dans la même région soit généralement gratuit, il est important de vérifier les taux spécifiques pour chaque service avant utilisation.

### Modes de paiement AWS
AWS suit une philosophie de tarification flexible où vous payez uniquement pour ce que vous utilisez, sans contrats à long terme ni dépenses initiales importantes. Les services sont disponibles à la demande, avec plusieurs options pour optimiser les coûts :

- **Paiement à l'utilisation** : Payez uniquement pour les services utilisés sans frais initiaux, ce qui permet une adaptation rapide aux besoins changeants et une concentration sur l'innovation.

- **Payez moins lorsque vous réservez** : Pour des services comme Amazon EC2 et Amazon RDS, réservez de la capacité pour économiser jusqu'à 75% par rapport aux tarifs à la demande. Options disponibles :
  - Instances réservées avec paiement total anticipé (AURI)
  - Instances réservées avec paiement partiel anticipé (PURI)
  - Instances réservées sans paiement à l'avance (NURI)

- **Payez moins en utilisant plus** : Bénéficiez de tarifs dégressifs pour des services comme Amazon S3, Amazon EBS, ou Amazon EFS où plus vous utilisez de ressources, moins le tarif par Go est élevé. 

- **Payez encore moins au fur et à mesure qu'AWS évolue** : Pour les grands projets avec des besoins uniques, une tarification personnalisée peut être négociée.

### Services sans frais
AWS propose plusieurs services sans frais supplémentaires, y compris :

- **Amazon Virtual Private Cloud (Amazon VPC)** : Lancez des ressources AWS dans un réseau virtuel que vous définissez.
- **Gestion des identités et des accès AWS (AWS IAM)** : Contrôlez l'accès aux services et ressources AWS.
- **Facturation consolidée** : Simplifiez le paiement pour plusieurs comptes AWS avec une seule facture et des opportunités de réduction des coûts.
- **AWS Elastic Beanstalk** : Déployez et gérez vos applications sur AWS plus facilement et rapidement.
- **AWS CloudFormation** : Créez et gérez des collections de ressources AWS liées de manière prévisible.
- **La mise à l'échelle automatique** : Ajoutez ou supprimez des ressources automatiquement selon les conditions définies pour maintenir les performances et réduire les coûts.
- **AWS OpsWorks** : Facilite le déploiement et la gestion d'applications de toutes tailles.

Bien que ces services soient offerts sans frais, les ressources associées, comme les instances EC2 supplémentaires créées par la mise à l'échelle automatique, peuvent entraîner des coûts.


### Points cléfs
Il n'y a aucun frais (avec quelques exceptions) pour:•Le transfert de données entrantes.•Le transfert de données entre des services au sein d'une même régionAWS.•Paiement à l'utilisation.•Démarrage et arrêt à tout moment.•Aucun contrat à long terme n'est requis.•Certains services sont gratuits, mais d'autres services AWS utilisés qu'ils fournissent peuvent ne pas l'être.En résumé, bien que le nombre et les types des services proposés par AWS aient significativement augmenté, notre philosophie de tarification reste inchangée. À la fin de chaque mois, vous ne payez que pour ce que vous utilisez et vous pouvez commencer ou arrêter d'utiliser un produit à n'importe quel moment. Aucun contrat à long terme n'est requis. Le meilleur moyen pour estimer les coûts est d'examiner les caractéristiques fondamentales de chaque service AWS, d'estimer votre utilisation pour chaque caractéristique et d'ensuite faire correspondre cette utilisation aux prix publiés sur le site web d'AWS. Notre stratégie de tarification pour chaque service vous offre une flexibilité de choix dans les services dont vous avez besoin pour chaque projet et vous ne payez que ce que vous utilisez.Parmi les services AWS gratuits, vous trouverez: •AmazonVPC•ElasticBeanstalk•AWS CloudFormation•IAM•Services de mise à l'échelle automatique•AWS OpsWorks•Facturation consolidée Les services en eux-mêmes sont gratuits, mais les ressources allouées ne le sont pas toujours. Dans la plupart des cas, aucuns frais ne s'appliquent au transfert de données entrantes ou au transfert de données entre d'autres services AWS au sein de la même région AWS. Il y a quelques exceptions. Veillez donc à vérifier les taux de transfert de données avant de commencer à utiliser le service AWS.Les coûts de transfert de données sortantes sont progressifs

## 2.2 Coût Total de Possession (TCO)

### Comparaison: Sur site vs. Cloud AWS

#### Infrastructure sur site
- **Coûts initiaux** : Investissements importants en matériel, logiciels, installations, et personnel.
- **Évolutivité** : La montée en charge peut être coûteuse et lente; réduire la capacité ne diminue pas les coûts fixes.
#### Infrastructure cloud (AWS)
- **Aucune dépense initiale** : Le modèle de paiement à l'utilisation supprime les coûts d'investissement initiaux.
- **Évolutivité flexible** : Facilité d'ajustement des ressources en fonction des besoins, avec des coûts directement liés à l'utilisation.
### Qu'est-ce que le TCO?

Le TCO est une estimation financière visant à identifier les coûts directs et indirects associés à l'achat et à l'utilisation d'un système sur sa durée de vie. Il est crucial pour comparer les coûts d'une infrastructure sur site avec ceux du cloud, aidant les entreprises à prendre des décisions éclairées concernant la migration vers le cloud.

### Considérations liées au TCO
- **Coûts sur site** : Comprend le matériel, les logiciels, le réseau, les installations, et la main-d'œuvre nécessaire pour la gestion.
- **Coûts cloud** : Principalement des coûts opérationnels basés sur la consommation; plus prévisibles et souvent moins élevés grâce à la tarification transparente par unité de temps et d'utilisation.

### Économies potentielles
Migration vers AWS peut entraîner jusqu'à 96% d'économies sur trois ans par rapport à une infrastructure sur site, principalement due à la flexibilité d'AWS à ajuster les ressources en fonction des besoins réels et à réduire ainsi les frais généraux.

### Calculateur de prix AWS
- **Fonctionnalités** : Permet d'estimer les coûts mensuels, d'identifier les opportunités de réduction des coûts, et de modéliser des solutions avant leur mise en œuvre.
- **Utilité** : Aide à planifier et simuler les coûts des services AWS, à optimiser les dépenses et à prendre des décisions de déploiement informées.

### Interprétation d'une estimation AWS
- **Total des 12 premiers mois** : Combine les coûts initiaux et mensuels pour la première année.
- **Total initial** : Coûts à payer à l'avance lors de la configuration.
- **Total mensuel** : Coûts récurrents pour l'exploitation des services AWS.

### Avantages du cloud AWS

#### Avantages tangibles
- Réduction des dépenses de calcul, de stockage, de mise en réseau et de sécurité.
- Diminution des achats de matériel et de logiciels, et des coûts d'exploitation, de sauvegarde et de reprise après sinistre.
- Moins de personnel nécessaire pour les opérations.

#### Avantages intangibles
- Réutilisation des services pour redéfinir les solutions cloud.
- Amélioration de la productivité des développeurs et satisfaction client accrue.
- Agilité des processus métier pour répondre efficacement aux opportunités.

L'analyse du TCO est essentielle pour comprendre le coût réel des infrastructures sur site par rapport à celles du cloud, incluant non seulement les économies directes mais aussi les bénéfices à long terme de la flexibilité, de l'évolutivité et des innovations continues offertes par AWS.

## 2.3 AWS Organizations

### Présentation d'AWS Organizations
AWS Organizations est un service gratuit permettant de gérer plusieurs comptes AWS de manière centralisée. Il offre des fonctionnalités telles que la gestion des politiques d'accès, le contrôle des services AWS, l'automatisation de la création et la gestion des comptes, ainsi que la facturation consolidée.

### Terminologie Clé
- **Organisation** : L'entité principale, représentant la collection de tous les comptes.
- **Unité Organisationnelle (OU)** : Un conteneur pour regrouper des comptes, pouvant contenir d'autres OUs. Permet de structurer les comptes en une hiérarchie.
- **Compte** : Un compte AWS standard contenant des ressources AWS.
- **Politiques de Contrôle des Services (SCP)** : Des règles appliquées à des niveaux de l'organisation pour gérer les permissions à travers les comptes.

### Fonctionnalités Principales
- **Gestion centralisée des politiques d'accès** : Contrôle uniforme des accès aux services AWS sur plusieurs comptes.
- **Facturation Consolidée** : Un seul moyen de paiement pour tous les comptes, avec une vue d'ensemble des coûts et l'opportunité de bénéficier de tarifs préférentiels sur l'usage groupé.
- **Automatisation** : API pour simplifier et automatiser la création et gestion des comptes AWS.

### Sécurité dans AWS Organizations
- **Gestion des identités et des accès (IAM)** : Contrôle qui peut faire quoi au sein des services AWS.
- **SCP vs IAM** : Les SCP permettent de définir des permissions à l'échelle de l'organisation ou des OUs, tandis que IAM est utilisé pour des contrôles plus granulaires au niveau des comptes, utilisateurs, groupes et rôles.

### Configuration des Organisations
1. **Création d'une Organisation** : Utilisation de votre compte AWS principal pour établir et inviter d'autres comptes.
2. **Création des Unités Organisationnelles** : Structuration de votre organisation en différentes OUs.
3. **Application des Politiques de Contrôle des Services** : Définition de règles de gouvernance applicables à des groupes de comptes.
4. **Test des Restrictions** : Validation des politiques appliquées pour s'assurer qu'elles fonctionnent comme prévu.

### Limites d'AWS Organizations
- Restrictions sur les noms, nombre de comptes, OUs, et politiques.
- Limites spécifiques sur la taille des politiques et le niveau de hiérarchie des OUs.

### Accès à AWS Organizations
- **Console de Gestion AWS** : Interface utilisateur graphique pour gérer les comptes et les ressources.
- **AWS CLI** : Interface en ligne de commande pour une gestion plus scriptée et automatisée.
- **SDK AWS** et **API de Requête HTTPS** : Kits de développement et interfaces de programmation pour intégrer la gestion d'AWS Organizations dans vos applications.

AWS Organizations offre une structure puissante pour la gestion à grande échelle des ressources AWS, améliorant la gouvernance, la conformité, et l'efficacité opérationnelle au sein des entreprises utilisant AWS.

## 2.4 Facturation et Gestion des Coûts AWS

### Présentation de la Gestion de Facturation et Coûts AWS
Le service de Facturation et Gestion des Coûts AWS offre une plateforme pour surveiller, gérer et optimiser les dépenses AWS. Il inclut des fonctionnalités de prédiction des coûts et de budgétisation pour une planification financière plus précise.

### Tableau de Bord de Facturation AWS
Le tableau de bord de facturation AWS affiche:
- **Récapitulatif des dépenses** : Dépenses du mois dernier, estimations pour le mois en cours, et prévisions pour les mois futurs.
- **Dépenses mensuelles par service** : Visualisation des principaux services utilisés et leurs coûts associés.

### Outils de Gestion des Coûts
- **AWS Budgets** : Planifiez et contrôlez les dépenses AWS avec des alertes de dépassement de budget.
- **Rapport d'Utilisation et de Coût** : Détails des tendances de consommation et opportunités d'optimisation.
- **AWS Cost Explorer** : Visualisez, gérez et prévoyez vos dépenses AWS.

### Fonctionnalités des Outils
- **Factures mensuelles** : Liste détaillée des coûts par service AWS et par région.
- **Cost Explorer** : Analyse approfondie des coûts, tendances des dépenses et prévisions sur trois mois.
- **Réduction et suivi des coûts** : Surveillance des budgets avec notifications pour la gestion proactive des coûts.

### Rapport de Coût et d'Utilisation
Cet outil fournit une vue détaillée des coûts et de l'utilisation par catégorie de service, mise à jour quotidiennement et stockée dans un compartiment S3.

### Support Technique d'AWS
- **AWS Support** : Offre une combinaison d'outils et d'expertise pour tous les niveaux d'utilisation, de l'expérimentation à l'exploitation stratégique d'AWS.
- **Plans de support** :
  - **Support Basique** : Accès aux ressources, Service Health Dashboard, et vérifications de base de Trusted Advisor.
  - **Support Développeur** : Pour les clients en phase de développement ou de test.
  - **Support Business** : Pour les clients avec des charges de travail en production.
  - **Support Enterprise** : Pour les clients avec des charges de travail métiers et stratégiques, incluant l'accès à un Technical Account Manager.

AWS offre des services dédiés à la gestion des coûts et à la facturation pour aider les utilisateurs à comprendre, gérer et optimiser leurs dépenses tout en bénéficiant d'un support technique adapté à leurs besoins.
# 3. Infrastructure mondiale AWS

## 3.0 Objectifs
* Identifier la différence entre les régions AWS, les zones de disponibilité et les emplacements périphériques
* Identifier les services et les catégories de services AWS
## 3.1 Infrastructure mondiale AWS

### Présentation des Régions AWS
AWS est structuré en 22 régions à travers le monde. Chaque région AWS représente un lieu géographique physique contenant une ou plusieurs zones de disponibilité. Ces zones de disponibilité comprennent un ou plusieurs centres de données.

### Isolation et Réplication
- **Isolation des Régions** : Chaque région est isolée des autres, ce qui renforce la tolérance aux pannes et la stabilité.
- **Réplication des Données** : Les données stockées dans une région ne sont pas automatiquement répliquées dans d'autres régions. La réplication inter-régions doit être configurée manuellement selon les besoins.

### Activation des Régions
- **Régions par Défaut** : Les régions introduites avant le 20 mars 2019 sont activées par défaut.
- **Régions Postérieures** : Régions ajoutées après cette date, telles que l'Asie-Pacifique (Hong Kong) et le Moyen-Orient (Bahreïn), nécessitent une activation manuelle via la Console de gestion AWS.

### Accès Restreint et Régions Spécifiques
- **Régions AWS en Chine** : Accès exclusif via un compte Amazon AWS (Chine).
- **AWS GovCloud (USA)** : Région isolée destinée aux administrations américaines, répondant à des exigences réglementaires strictes.

### Sélection d'une Région
- **Considérations Légales** : Les lois locales peuvent restreindre la géolocalisation des données (ex. RGPD en Europe).
- **Latence et Proximité** : Choisir une région proche des utilisateurs finaux pour minimiser la latence.
- **Disponibilité des Services** : Tous les services AWS ne sont pas disponibles dans toutes les régions.
- **Coût des Services** : Les prix peuvent varier d'une région à l'autre.

### Zones de Disponibilité
- **Définition** : Partitions isolées de l'infrastructure AWS, chaque zone peut comporter plusieurs centres de données.
- **Conception** : Conçues pour être hautement disponibles et tolérantes aux pannes, les zones de disponibilité sont interconnectées par des réseaux à haute bande passante et à faible latence.

### Centres de Données AWS
- **Opérations** : Les clients ne choisissent pas spécifiquement un centre de données; ils sélectionnent des zones de disponibilité.
- **Sécurité et Redondance** : Conception sécurisée et redondante pour garantir la continuité des services malgré les défaillances.

### Points de Présence
- **Amazon CloudFront et Route 53** : Utilisent un réseau mondial de points de présence pour réduire la latence et améliorer l'accès aux contenus.
- **Caches Périphériques Régionaux** : Gèrent le contenu peu fréquemment accédé pour optimiser les performances de distribution.

### Caractéristiques de l'Infrastructure AWS
- **Élasticité** : Adaptation dynamique de la capacité pour répondre aux besoins changeants.
- **Tolérance aux Pannes** : Redondance des composants pour maintenir les opérations malgré les pannes.
- **Haute Disponibilité** : Conçu pour minimiser les temps d'arrêt et assurer des performances opérationnelles élevées avec peu d'intervention humaine.

L'infrastructure AWS est conçue pour offrir élasticité, tolérance aux pannes, haute disponibilité, et une gestion efficace de la latence à travers un réseau mondial de régions et de zones de disponibilité.

### Points cléfs
L'infrastructure mondiale AWSse compose de régions et de zones de disponibilité.•Le choix d'une région s'effectue généralement en fonction des exigences de conformitéou dans un but visant à réduire la latence.•Chaque zone de disponibilitéest physiquement séparée des autres zones de disponibilité et dispose d'une alimentation, d'une mise en réseau et d’une connectivité redondantes.•Les emplacements périphériqueset lescaches périphériques régionaux améliorent les performances en mettant en cachele contenu à proximité des utilisateurs

## 3.2 Services et Catégories de Services AWS

### Services de base AWS
AWS s'appuie sur une infrastructure mondiale comprenant des régions, des zones de disponibilité, et des points de présence. Celle-ci supporte une vaste gamme de services cloud qui incluent le calcul, le stockage, et les réseaux, tous accessibles à la demande.

### Catégories de Services AWS

#### Services de Stockage
- **Amazon S3** : Stockage d'objets scalable pour diverses utilisations.
- **Amazon EBS** : Stockage par blocs pour instances EC2.
- **Amazon EFS** : Système de fichiers réseau scalable.
- **Amazon S3 Glacier** : Stockage à long terme économique.

#### Services de Calcul
- **Amazon EC2** : Capacité de calcul redimensionnable.
- **AWS Lambda** : Exécution de code sans serveur.
- **Amazon ECS** et **EKS** : Orchestration de conteneurs.
- **AWS Fargate** : Exécution de conteneurs sans gestion de serveurs.

#### Services de Bases de Données
- **Amazon RDS** : Base de données relationnelle gérée.
- **Amazon DynamoDB** : Base de données de clés-valeurs et documents.
- **Amazon Redshift** : Entrepôt de données de grande échelle.
- **Amazon Aurora** : Base de données relationnelle performante.

#### Services de Mise en Réseau et de Contenu
- **Amazon VPC** : Réseaux isolés dans le cloud.
- **Amazon CloudFront** : CDN pour la distribution de contenu.
- **AWS Transit Gateway** : Interconnexion de réseaux VPC.
- **AWS Direct Connect** : Connexion réseau privée à AWS.

#### Services de Sécurité, Identité et Conformité
- **AWS IAM** : Gestion sécurisée de l'accès aux ressources AWS.
- **AWS Shield** et **AWS WAF** : Protection contre les attaques DDoS et gestion des règles de filtrage web.
- **Amazon Cognito** : Gestion des identités et des accès utilisateurs pour applications.
- **AWS KMS** : Gestion des clés de chiffrement.

#### Services de Gestion des Coûts
- **AWS Cost Explorer** : Outil d'analyse des coûts AWS.
- **AWS Budgets** : Outil pour définir et gérer les budgets.
- **Rapport d'utilisation et de coût AWS** : Détails exhaustifs sur l'utilisation et les coûts AWS.

#### Services de Gestion et Gouvernance
- **AWS Management Console** : Interface pour gérer les services AWS.
- **AWS Config** : Suivi des ressources AWS et de leurs changements.
- **Amazon CloudWatch** : Surveillance des ressources et applications.
- **AWS Auto Scaling** : Automatisation du dimensionnement des ressources.

Chaque catégorie de service est conçue pour répondre à des besoins spécifiques en entreprise, offrant flexibilité, performance et sécurité.

## 3.3 Console de gestion AWS

# 4. Sécurité du cloud AWS
## 4.0 Objectifs
* Identifier le modèle de responsabilité partagée
* Identifier la responsabilité du client et celle d’AWS
* Identifier les utilisateurs, les groupes et les rôles IAM
* Décrire différents types d’identifiants de sécurité dans IAM
* Identifier la procédure de sécurisation d’un nouveau compte AWS
* Explorer les utilisateurs et les groupes IAM
* Identifier la manière de sécuriser les données AWS
* Identifier les programmes de conformité AWS

## 4.1 Modèle de Responsabilité Partagée AWS

### Introduction
AWS et ses clients partagent la responsabilité de maintenir la sécurité et la conformité des services cloud. AWS gère l'infrastructure cloud, tandis que le client gère la sécurité des ce qu'il y déploie.

### Responsabilités d'AWS
AWS est responsable de la sécurité *du* cloud, incluant:
- La sécurité physique des data centers.
- L'infrastructure matérielle et logicielle qui supporte les services cloud.
- Les composants réseau essentiels pour le fonctionnement des services AWS.

### Responsabilité du Client
Les clients sont responsables de la sécurité *dans* le cloud, ce qui comprend :
- Le chiffrement des données au repos et en transit.
- La configuration sécurisée du réseau et des instances de calcul.
- La gestion des accès et des identifiants.

### Types de Services et Responsabilités

#### IaaS (Infrastructure as a Service)
Exemples : Amazon EC2
- **Responsabilité AWS** : Infrastructure physique, stockage, réseautage.
- **Responsabilité Client** : Système d'exploitation, applications, et données.

#### PaaS (Platform as a Service)
Exemples : AWS Lambda, Amazon RDS
- **Responsabilité AWS** : Gestion de l'infrastructure, du système d'exploitation, et des plateformes.
- **Responsabilité Client** : Données et classifications des ressources.

#### SaaS (Software as a Service)
Exemples : Amazon Chime, AWS Shield
- **Responsabilité AWS** : Gestion complète de l'application, y compris la maintenance, les mises à jour de sécurité et la disponibilité.
- **Responsabilité Client** : Utilisation sécurisée du logiciel et gestion des données utilisateur.



### Points cléfs 
Les responsabilités quant à la sécurité sont réparties entre AWS et le client: •AWS est responsable de la sécurité ducloud.•Le client est responsable de la sécurité dansle cloud.•AWS est responsable de la protection de l’infrastructure(y compris le matériel, les logiciels, la mise en réseau et les installations) qui exécutent les services AWS Cloud.•Pour les services classés dans la catégorie Infrastructure en tant que service (IaaS), le client est responsable de l’exécution des tâches de configuration et de gestion de la sécurité nécessaires.•Par exemple, les mises à jour du système d’exploitation invité et les correctifs de sécurité, les pare-feu, les configurations des groupes de sécurité
## 4.2 AWS Identity and Access Management (IAM)
* IAM = Gérér l'accès aux ressources AWS
	* Ressource = Entité d'un compte AWS (ex : EC2)
* Exemple : Controler qui peut résilier les instances Amazon EC2
* Définir des droits d'accès précis
	* Qui peut accéder à la ressource
	* Quelles ressources sont accessibles et que peut faire l'utilisateur avec ces ressources
	* Comment les ressources sont accessibles
* IAM est une fonctionnalité AWS gratuite

### Composantes essentiels de IAM
* Utilisateur IAM
	* Personne ou application qui peut s'authentifier 
* Groupe IAM
	* Ensemble d'utilisateurs IAM qui reçoivent une autorisation identique
* Stratégie IAM
	* Document qui définit les ressources accessibles et le niveau d'accès à chaque ressource
* Rôle IAM
	* Mécanisme utile pour accorder un ensemble d'autorisations afin d'effectuer des demandes de service AWS

### Authentification en tant que utilisateur IAM pour obtenir l'accès
* Définition d'un utilisateur IAM = Selection des types d'accès que l'utilisateur est autorisé à utiliser
* Types d'accès 
	* Accès par programmation
		* Authentifier-vous avec les outils : ID cléf d'accès et Clef d'accès secrète
		* Fournit un accès à AWS CLI et kit SDK AWS
	* Accès à AWS Management Console
		* Authentifier-vous avec les outils : 
			* ID de compte à 12 chiffre ou alias
			* Nom d'utilisateur IAM
			* Mot de passe IAM
		* Si elle est activé, MFA demande code de vérification
		* 
Par défaut, les utilisateurs IAM ne sont pas autorisés à accéder aux ressources ni aux données d’un compte AWS. Au lieu de cela, vous devez explicitement accorder des autorisations à un utilisateur, groupe ou rôle en créant unestratégie,qui est un document au format JavaScript Object Notation (JSON). Une stratégie répertorie les autorisations qui acceptentou refusent l’accès aux ressources du compte AWS

### Autorisation IAM
- Attribue des autorisations via la création d'une stratégie IAM.
- Les autorisations déterminent les ressources et opérations qui peuvent être utilisées :
	- Par défaut, toutes les autorisations sont implicitement refusées.
	- En cas de refus explicite, aucune autorisation ne peut être accordée.
- Bonne pratique : suivez le principe du moindre privilège.
![[Pasted image 20240514205436.png]]
### Stratégie IAM
- Une stratégie IAM est un document qui définit les autorisations
	- Contrôle précis des accès
- Deux types de stratégies : basées sur l'identité et basées sur les ressources
- Stratégies basées sur l'identité
	- Stratégie attachée à une entité IAM
		- Utilisateur IAM, groupe IAM ou rôle IAM
	- Les stratégies spécifient les éléments suivants :
		- Actions pouvant être effectuées par l'entité
		- Actions ne pouvant pas être effectuées par l'entité
	- Une même stratégie peut être associée à plusieurs entités.
	- Une même entité peut être associée à plusieurs stratégies.
- Stratégies basées sur les ressources
	  - Attachées à une ressource (compartiment S3, par exemple)

### Stratégie basées sur les ressources
- Les stratégies basées sur l'identité sont jointes à un utilisateur, un groupe ou un rôle IAM.
- Les stratégies basées sur les ressources sont jointes à une ressource (pas à un utilisateur, un groupe ou un rôle).
- Caractéristiques des stratégies basées sur les ressources
	- Spécifie qui a accès à la ressource et quelles actions sont autorisées.
	- Les stratégies sont intégrées uniquement, non pas gérées.
- Les stratégies basées sur les ressources ne sont prises en charge que par certains services AWS.

### Groupes IAM
- Un groupe IAM est un ensemble d'utilisateurs IAM.
- Un groupe est utilisé pour accorder les mêmes autorisations à plusieurs utilisateurs.
	- Autorisations accordées en attachant une ou plusieurs stratégies IAM au groupe.
- Un utilisateur peut appartenir à plusieurs groupes.
- Il n’y a aucun groupe par défaut.
- Les groupes ne peuvent pas être imbriqués.

### Rôles IAM
- Un rôle IAM est une identité IAM avec des autorisations spécifiques
	- Semblable à un utilisateur IAM
		- Des stratégies d'autorisation y sont attachées
- Différent d'un utilisateur IAM
	- Pas uniquement associé à une seule personne
	- Conçu pour être assumé par une personne, une application ou un service
- Le rôle fournit des autorisations de sécurité temporaires
- Exemples d'utilisation des rôles IAM pour déléguer l'accès
	- Utilisés par un utilisateur IAM dans le même compte AWS que le rôle
	- Utilisés par un service AWS, tel qu'Amazon EC2, dans le même compte que le rôle
	- Utilisés par un utilisateur IAM dans un autre compte AWS que le rôle

### Points cléfs
- Les stratégies IAM sont construites avec JavaScript Object Notation (JSON) et définissent les autorisations.
	- Les stratégies IAM peuvent être attachées à n'importe quelle entité IAM.
	- Les entités sont des utilisateurs IAM, des groupes IAM et des rôles IAM.
- Un utilisateur IAM permet à une personne, une application ou un service de s'authentifier auprès d'AWS.
- Un groupe IAM est un moyen simple d'attacher les mêmes stratégies à plusieurs utilisateurs.
- Un rôle IAM peut être associé à des stratégies d'autorisation et peut être utilisé pour déléguer un accès temporaire à des utilisateurs ou à des applications.

## 4.3 Sécurisation d’un nouveau compte AWS
### Accès de l'utilisateur racine du compte AWS et accès IAM
- Bonne pratique : n’utilisez pas l’utilisateur racine du compte AWS, sauf si nécessaire.
	- L’accès à l’utilisateur racine du compte nécessite une connexion avec l’adresse e-mail (et le mot de passe) que vous avez utilisé pour créer le compte.
- Exemples d’actions qui ne peuvent être effectuées qu’avec l’utilisateur racine du compte :
	- Mettre à jour le mot de passe de l’utilisateur racine du compte
	- Modifier le programme de support AWS
	- Restaurer les autorisations d’un utilisateur IAM
	- Modifier les paramètres du compte (par exemple, les coordonnées ou les régions autorisées)

### Sécurisation d'un nouveau compte AWS
Voici le texte de l'image formaté en Markdown :

- Étape 1 : arrêtez d’utiliser l’utilisateur racine du compte dès que possible.
	- L’utilisateur racine du compte a un accès illimité à toutes vos ressources.
- Pour arrêter d’utiliser l’utilisateur racine du compte :
  1. Connectez-vous en tant qu’utilisateur racine du compte, puis créez un utilisateur IAM pour vous-même. Enregistrez les clés d’accès si nécessaire.
  2. Créez un groupe IAM, accordez-lui l’intégralité des privilèges administrateur et ajoutez l’utilisateur IAM à ce groupe.
  3. Désactivez et supprimez les clés d’accès de l’utilisateur racine de votre compte, si elles existent.
  4. Activez une stratégie de mot de passe pour les utilisateurs.
  5. Connectez-vous avec vos nouvelles informations d'identification d'utilisateur IAM.
  6. Stockez les autorisations de l’utilisateur racine de votre compte dans un endroit sécurisé.

- Étape 2 : activez l’authentification multifacteur (MFA).
	- Exigez l’authentification MFA pour l’utilisateur racine de votre compte et tous les utilisateurs IAM.
	- Vous pouvez également utiliser l'authentification MFA pour contrôler les accès aux API des services AWS.
- Options de récupération du jeton d’authentification MFA :
	- Applications virtuelles compatibles MFA :
		- Google Authenticator
		- Authy Authenticator (application Windows pour smartphone)
	- Dispositifs de clé de sécurité U2F :
		- YubiKey, par exemple
	- Options MFA matérielles :
		- Outil de génération automatique de clés ou carte d'affichage offerts par Gemalto.

- Étape 3 : utilisez AWS CloudTrail.
	- CloudTrail suit l'activité des utilisateurs sur votre compte.
		- Journales toutes les demandes d'API envoyées aux ressources dans tous les services pris en charge de votre compte.
		- L'historique des événements AWS CloudTrail de base est activé par défaut et est gratuit.
		- Il contient toutes les données d'événement de gestion sur les 90 derniers jours d'activité du compte.
- Pour accéder à CloudTrail :
  1. Connectez-vous à AWS Management Console, puis choisissez le service CloudTrail.
  2. Cliquez sur Event history (Historique des événements) pour afficher, filtrer et rechercher les événements des 90 derniers jours.
- Pour activer les journaux au-delà de 90 jours et activer les alertes d'événements spécifiés, créez un journal d'activité.
  1. Sur la page des journaux d'activité de la console CloudTrail, cliquez sur Create trail (Créer un journal de suivi).
  2. Donnez-lui un nom, appliquez-le à toutes les régions et créez un compartiment Amazon S3 pour le stockage des journaux.
  3. Configurez les restrictions d'accès au niveau du compartiment S3 (par exemple, seuls les utilisateurs disposant de droits d'administration doivent y avoir accès).

- Étape 4 : activez un rapport de facturation, tel que le rapport d'utilisation et de coût AWS.
	- Les rapports de facturation fournissent des informations relatives à votre utilisation des ressources AWS et aux coûts estimés pour cette utilisation.
	- AWS transmet les rapports à un compartiment Amazon S3 que vous spécifiez.
		- Le rapport est mis à jour au moins une fois par jour.
	- AWS Cost and Usage Report suit votre utilisation d'AWS et indique les frais estimés associés à votre compte AWS, par heure ou par jour.

### Points cléfs
- Meilleures pratiques pour sécuriser un compte AWS :
	- Sécurisez les connexions avec l'authentification multifactor (MFA).
	- Supprimez les clés d'accès utilisateur racine du compte.
	- Créez des utilisateurs IAM individuels et accordez des autorisations selon le principe du moindre privilège.
	- Utilisez des groupes pour attribuer des autorisations à des utilisateurs IAM.
	- Configurez une stratégie stricte en matière de mots de passe.
	- Déléguez en utilisant les rôles plutôt qu'en partageant les informations d'identification.
	- Surveillez l'activité du compte à l'aide d'AWS CloudTrail.
## 4.4 Sécurisation des comptes

### AWS Organisation
- AWS Organizations vous permet de consolider plusieurs comptes AWS afin de les gérer de manière centralisée.
- Fonctionnalités de sécurité d'AWS Organizations :
	- Regroupement des comptes AWS en unités d'organisation (UO) et association de différentes stratégies d'accès avec chacune d'elles.
	- Intégration et prise en charge d'IAM :
	    - Les autorisations accordées à un utilisateur sont à la croisée des autorisations accordées par AWS Organizations et des autorisations accordées par IAM dans ce compte.
	- Utilisation de stratégies de contrôle des services pour définir le contrôle des services AWS et des actions d'API auxquelles chaque compte AWS peut accéder.

### Stratégies de contrôle des services
- Les stratégies de contrôle des services (SCP) offrent un contrôle centralisé sur les comptes.
	- Limitez les autorisations disponibles dans un compte faisant partie d'une organisation.
- Assurent que les comptes sont conformes aux directives de contrôle d'accès.
- Les SCP sont similaires aux stratégies d'autorisations IAM :
	- Elles utilisent une syntaxe similaire.
	- Cependant, une SCP n'accorde jamais d'autorisations.
	- Au lieu de cela, les SCP spécifient le nombre maximum d'autorisations pour une organisation.
### AWS Key Management Service (AWS KMS)
- Fonctionnalités d'AWS Key Management Service (AWS KMS) :
	- Vous permet de créer et gérer des clés de chiffrement.
	- Vous permet de contrôler l'utilisation du chiffrement dans les services AWS et dans vos applications.
	- S'intègre à AWS CloudTrail pour journaliser l'utilisation de toutes les clés.
	- Utilise des modules de sécurité matériels (HSM) validés par la norme FIPS 140-2 pour la protection des clés.
### Amazon Cognito
- Fonctionnalités d'Amazon Cognito :
	- Ajoute l'inscription des utilisateurs, la connexion et le contrôle d'accès à vos applications web et mobiles.
	- S'adapte à des millions d'utilisateurs.
	- Prend en charge la connexion avec les fournisseurs d'identité sur les réseaux sociaux, tels que Facebook, Google et Amazon, et avec les fournisseurs d'identité d'entreprise, tels que Microsoft Active Directory via Security Assertion Markup Language (SAML) 2.0.

### AWS Shield
- Fonctionnalités d'AWS Shield :
	- Offre un service de protection contre le déni de service distribué (DDoS) géré.
	- Protège les applications exécutées sur AWS.
	- Assure une détection permanente et intègre l'atténuation automatique des risques.
	- AWS Shield Standard activé sans frais supplémentaires. AWS Shield Advanced est un service payant optionnel.
- Utilisez-le pour minimiser les temps d'arrêt et la latence des applications.
## 4.5 Sécurisation des données sur AWS

### Chiffrement des données au repos
- Le chiffrement encode les données avec une clé secrète, ce qui les rend illisibles.
	- Seuls ceux qui disposent de cette clé secrète peuvent décoder les données.
	- AWS KMS permet de gérer vos clés secrètes.
- AWS prend en charge le chiffrement des données au repos.
	- Données au repos = Données stockées physiquement (sur disque ou sur bande).
	- Vous pouvez chiffrer les données stockées dans n'importe quel service pris en charge par AWS KMS, notamment :
		- Amazon S3
		- Amazon EBS
		- Amazon Elastic File System (Amazon EFS)
		- Bases de données gérées Amazon RDS
### Chiffrement des données en transit
- Chiffrement des données en transit (données qui se déplacent sur un réseau) :
	- Transport Layer Security (TLS) (auparavant appelé SSL) est un protocole standard ouvert.
	- AWS Certificate Manager fournit un moyen de gérer, déployer et renouveler les certificats TLS ou SSL.
- Le protocole HTTP sécurisé (HTTPS) crée un tunnel sécurisé.
	- Utilise TLS ou SSL pour l'échange bidirectionnel des données.
- Les services AWS prennent en charge le chiffrement des données en transit.

### Sécurisation des compartiments et objets AmazonS3
- Les compartiments et objets S3 nouvellement créés sont privés et protégés par défaut.
- Lorsque les cas d'utilisation nécessitent le partage d'objets de données sur Amazon S3 :
	- Il est essentiel de gérer et de contrôler l'accès aux données.
	- Suivez les autorisations qui respectent le principe du moindre privilège et envisagez d'utiliser le chiffrement Amazon S3.
- Les outils et options de contrôle d'accès aux données S3 incluent :
	- Fonctionnalité Amazon S3 Block Public Access : facile à utiliser.
	- Stratégies IAM : option appropriée lorsque l'utilisateur peut s'authentifier à l'aide d'IAM.
	- Listes de contrôle d'accès (ACL) : ancien mécanisme de contrôle d'accès.
	- Vérification des autorisations de compartiment AWS Trusted Advisor : fonctionnalité gratuite.

## 4.6 Efforts pour assurer la conformité

### Programmes de conformité AWS
- Les clients sont soumis à de nombreuses réglementations et exigences différentes en matière de sécurité et de conformité.
- AWS fait appel à des organismes de certification et à des auditeurs indépendants pour fournir aux clients des informations détaillées relatives aux stratégies, aux processus et aux contrôles établis et gérés par AWS.
- Les programmes de conformité peuvent être classés dans les catégories suivantes :
	- **Certifications et attestations**
		- Évaluées par un auditeur tiers indépendant.
		- Exemples : ISO 27001, 27017, 27018 et ISO/IEC 9001
	- **Lois, réglementation et confidentialité**
		- AWS fournit des fonctionnalités de sécurité et des accords juridiques pour assurer la conformité.
		- Exemples : Règlement général sur la protection des données (RGPD) en Europe, HIPAA aux États-Unis
	- **Alignements et frameworks**
		- Exigences de sécurité ou de conformité spécifiques à un secteur d'activité ou à une fonction
		- Exemples : Center for Internet Security (CIS), certifié Bouclier de protection des données UE-États-Unis
### AWS Config
- Évaluez, auditez et évaluez les configurations des ressources AWS.
	- À utiliser pour la surveillance continue des configurations.
	- Évaluez automatiquement les configurations enregistrées par rapport aux configurations souhaitées.
	- Passez en revue les modifications de configuration.
	- Consultez les historiques de configuration détaillés.
	- Simplifiez les audits de conformité et les analyses de sécurité.

### AWS Artifact
- Ressource centrale proposant des informations relatives à la conformité.
    - Fournissez un accès aux rapports de sécurité et de conformité et sélectionnez des accords en ligne.
    - Permet d’accéder à des exemples de chargement :
        - Certifications ISO d’AWS
        - Rapports Payment Card Industry (PCI) et Service Organization Control (SOC)
- Accédez à AWS Artifact directement depuis AWS Management Console.
    - Sous Security, Identify & Compliance (Sécurité, identité et conformité), cliquez sur Artifact.

### Points cléfs
- Les programmes de conformité de sécurité AWS fournissent des informations sur les stratégies, les processus et les contrôles qui sont établis et gérés par AWS.
- AWS Config est utilisé pour analyser, auditer et évaluer les configurations des ressources AWS.
- AWS Artifact donne accès aux rapports de sécurité et de conformité.

## 4.7 Services et ressources de sécurité supplémentaires

# 5. Mise en réseau et diffusion de contenu

## 5.0 Objectifs
* Comprendre les notions de base de la mise en réseau
* Décrire la mise en réseau virtuelle dans le cloud avec Amazon VPC
* Ajouter des légendes à un schéma du réseau
* Concevoir une architecture de VPC élémentaire
* Préciser les étapes de création d'un VPC
* Identifier les groupes de sécurité
* Créer votre propre VPC et lui ajouter des composants supplémentaires pour obtenir un réseau personnalisé
* Identifier les bases d'Amazon Route 53
* Mesurer les avantages d'Amazon CloudFront
## 5.2 Amazon Virtual Private Cloud (Amazon VPC)

### Amazon VPC
- Vous permet de mettre en service une section logiquement isolée du Cloud AWS où vous pouvez lancer des ressources AWS dans un réseau virtuel que vous définissez.
- Vous permet de contrôler vos ressources de mise en réseau virtuel, notamment :
	- La sélection d'une plage d'adresses IP
	- La création de sous-réseaux
	- La configuration de tables de routage et de passerelles réseau
- Vous permet de personnaliser la configuration réseau de votre VPC.
- Vous permet d'utiliser plusieurs couches de sécurité.

### VPC et sous réseaux
- **VPC** :
	- Logiquement isolé des autres VPC
	- Dédiés à votre compte AWS
	- Appartient à une seule région AWS et peuvent s'étendre sur plusieurs zones de disponibilité
- **Sous-réseaux** :
	- Plage d'adresses IP qui divisent un VPC
	- Appartiennent à une seule zone de disponibilité
	- Classés comme publics ou privés
![[Pasted image 20240514213502.png]]

### Types d'adresses IP publiques
- **Adresse IPv4 publique** :
    - Attribuée manuellement via une adresse IP élastique
    - Attribuée automatiquement via les paramètres d'attribution automatique d'adresse IP publique au niveau du sous-réseau
- **Adresse IP élastique** :
    - Associée à un compte AWS
    - Peut être allouée et remappée à tout moment
    - Des frais supplémentaires peuvent s'appliquer
### Interface réseau élastique
* Une interface réseau élastique est une interface réseau virtuelle que vous pouvez :
	* Attacher à une instance
	* Détacher de l'instance et attacher à une autre instance pour rediriger le trafic réseau
* Ses attributs sont conservés lorsqu'elle est rattachée à une nouvelle instance.
* Chaque instance de votre VPC possède une interface réseau par défaut à laquelle est attribuée une adresse IPv4 privée à partir de la plage d'adresses IPv4 de votre VPC
### Points cléfs
* Un VPC est une section logiquement isolée du Cloud AWS.
* Un VPC appartient à une région et nécessite un bloc d'adresse CIDR.
* Un VPC est subdivisé en sous-réseaux.
* Un sous-réseau appartient à une zone de disponibilité et nécessite un bloc d'adresse CIDR.
* Les tables de routage contrôlent le trafic d'un sous-réseau.
* Les tables de routage incluent un acheminement local intégré.
* Vous ajoutez des acheminements supplémentaires à la table.
* L'acheminement local ne peut pas être supprimé
## 5.3 Mise en réseau de VPC
## 5.4 Sécurité de VPC
## 5.5 Amazon Route 53
## 5.6 Amazon CloudFront

# 6. Calcul
## 6.1 Présentation des services de calcul
## 6.2 Amazon EC2
## 6.3 Optimisation des coûts Amazon EC2
## 6.4 Services de conteneurs
## 6.5 Introduction à AWS Lambda
## 6.6 Introduction à AWS Elastic Beanstalk

# 7. Stockage
## 7.1 Amazon Elastic Block Store (Amazon EBS)
## 7.2 Amazon Simple Storage Service (Amazon S3)
## 7.3 Amazon Elastic File System (Amazon EFS)
## 7.4 Amazon Simple Storage Service Glacier

# 8. Bases de données
## 8.1 Amazon Relational Database Service (Amazon RDS)
## 8.2 Amazon DynamoDB
## 8.3 Amazon Redshift
## 8.4 Amazon Aurora

# 9. Architecture cloud
## 9.1 Cadre AWS Well-Architected
## 9.2 Fiabilité et haute disponibilité
## 9.3 AWS Trusted Advisor

# 10. Auto Scaling et surveillance
## 10.1 Elastic Load Balancing
## 10.2 Amazon Cloud Watch
## 10.3 Amazon EC2 Auto Scaling
