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
## 1.1 Introduction au cloud computing
## 1.2 Avantages du cloud computing
## 1.3 Introduction à Amazon Web Services (AWS)
## 1.4 Framework d’adoption d’AWS Cloud (AWS CAF)

# 2. Coûts et facturation du Cloud
## 2.1 Bases de la tarification
## 2.2 Coût total de possession
## 2.3 AWS Organizations
## 2.4 Facturation et gestion des coûts AWS
## 2.5 Support technique
## 2.6 Calculateur de prix AWS

# 3. Infrastructure mondiale AWS
## 3.1 Infrastructure mondiale AWS
## 3.2 Services et catégories de services AWS
## 3.3 Console de gestion AWS

# 4. Sécurité du cloud AWS
## 4.1 Modèle de responsabilité partagée AWS
## 4.2 AWS Identity and Access Management (IAM)
## 4.3 Sécurisation d’un nouveau compte AWS
## 4.4 Sécurisation des comptes
## 4.5 Sécurisation des données sur AWS
## 4.6 Efforts pour assurer la conformité
## 4.7 Services et ressources de sécurité supplémentaires

# 5. Mise en réseau et diffusion de contenu
## 5.1 Bases de la mise en réseau
## 5.2 Amazon Virtual Private Cloud (Amazon VPC)
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
