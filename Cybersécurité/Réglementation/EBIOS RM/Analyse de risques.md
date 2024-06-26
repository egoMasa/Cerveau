# Chronologie d'analyse de risques libre

## 1) Système étudié
### 1.1) Propriétaires et responsable
Lister les personnes responsables et interagissant avec le système étudié (développement, opérationnel, Technique)

| Nom         | Rôle        | Service | Mail                | Numéro         |
| ----------- | ----------- | ------- | ------------------- | -------------- |
| Toto Dupont | Responsable |         | totodupont@toto.com | 06 XX XX XX XX |
| Toto Dupont | Responsable |         | totodupont@toto.com | 06 XX XX XX XX |
### 1.2) Valeurs métiers
Une valeur métier peut être des données spécifiques, ou un processus qui est crucial pour le système d'information (SI) et pour l'ensemble de l'entreprise : 
- ***Processus*** : Quelles taches est censé faire et rend possible le SI etudié ? Que permet t'il de faire (étape de son fonctionnement)
- ***Données*** : Ensemble des données collectés ou générées par le SI etudié

| **Famille**                           | **Valeur métier** | **Description** | **Données à caractère personnelles** |
| ------------------------------------- | ----------------- | --------------- | ------------------------------------ |
| - Données/Informations<br>- Processus | Exemple 1         |                 | Oui/Non                              |

### 1.3) Biens supports
Un bien support désigne les équipements, logiciels, infrastructures, et autres ressources matérielles ou immatérielles sur lesquelles reposent le fonctionnement des valeurs métiers. Les biens supports sont les composants physiques ou logiciels nécessaires pour que les fonctions, les données et les processus (valeurs métier) puissent opérer efficacement. Ils incluent tout ce qui est utilisé pour stocker, traiter, transmettre, et gérer les informations.

| **Bien supports**                   | **Responsables** | **Valeurs métiers** | **Vulnérabilités**                     | **Mesures actuelles**                                  |
| ----------------------------------- | ---------------- | ------------------- | -------------------------------------- | ------------------------------------------------------ |
| Bien support X {Liste bien support} | Nom              | Valeur métier       | Vulnérabilité X {Liste vulnérabilités} | Mesure X {Liste mesures}  <br>Mesure X {Liste mesures} |

### 1.4) Parties prenantes
Lister les clients, partenaires et prestataires intervenant sur l'entreprise à tout les niveaux (ménage, hébergeur, etc...)
Garder les parties prenantes avec un niveau de menaces à partir de zone de danger, zone de controle (4-16)

| **Catégorie partie prenante**               | **Partie prenante** | **Dépendance**                                                                                                                                | **Pénétration**                                                                                                                                    | **Maturité**                                                                                                                                    | **Confiance**                                                                                                                                          | **Niveau de menace**                                                                                                                                     |
| ------------------------------------------- | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - Clients  -Partenaires  <br>- Prestataires | Nom                 | La relation avec cette partie prenante est-elle vitale pour mon activité ?  <br>1 - Insignifiant  <br>2 – Faible  <br>3 – Moyen  <br>4 – Fort | Dans quelle mesure la partie prenante accède-t-elle à mes ressources internes ?  <br>1 - Insignifiant  <br>2 – Faible  <br>3 – Moyen  <br>4 – Fort | Quelles sont les capacités de la partie prenante en matière de sécurité ?  <br>1 - Insuffisante  <br>2 – Faible  <br>3 – Moyenne  <br>4 – Bonne | Les intentions ou les intérêts de la partie prenante sont-ils favorables aux miens ?  <br>1 - Faible  <br>2 – Moyenne  <br>3 – Forte  <br>4 – Maximale | (Dépendance*Pénétration)/(Maturité*Confiance)  <br>0-1 : Hors périmètre  <br>1-3 : Zone de veille  <br>4-5 : Zone de contrôle  <br>5-16 : Zone de danger |

## 2) Modélisation de la menace

### 2.1) Couples SR/OV
Définir les personnes ou groupes de menances potentielles qui pourrait s'en prendre au SI et à ses valeurs métiers, déduire leur motivation et selectionner le plus pertinents

| **Catégorie d’acteur**                                                                                                                                                    | **Acteur de risque** | **Catégorie d’objectif**                                                                                                                    | **Objectif visé**   | **Motivation**                                                                                                                                     | **Ressources**                                                                                                                                                                 | **Activité**                                                                                                                            | **Pertinence**                     | **Retenu** |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | ---------- |
| - Étatique  <br>- Crime organisé  <br>- Terroriste  <br>- Activiste idéologique  <br>- Officine spécialisée  <br>- Amateur  <br>- Vengeur  <br>- Malveillant pathologique | Nom                  | - Espionnage  <br>- Pré-positionnement stratégique  <br>- Influence  <br>- Entrave au fonctionnement  <br>- Lucratif  <br>- Défi, amusement | Description précise | Quelle est la motivation de la source de risque pour atteindre son objectif ?  <br>1 – Minimale  <br>2 – Faible  <br>3 – Moyenne  <br>4 - Maximale | Quelles sont les ressources (financières, compétences, infrastructure d'attaque) de la source de risque ?  <br>1 – Minimale  <br>2 – Faible  <br>3 – Moyenne  <br>4 – Maximale | La source de risque est-elle active dans le périmètre de l'étude ?  <br>1 – Minimale  <br>2 – Faible  <br>3 – Moyenne  <br>4 – Maximale | (Motivation+Ressources+Activité)/3 | Oui/Non    |

## 3) Scénarios

### 3.1) Evènements redoutés
Définir les évènements redoutés par l'entreprise concernant les valeurs métiers listées

| **Évènements redoutés**                                                                                                                                                                                                                                                | **Valeurs métiers** | Gravité                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------- |
| Vol<br>Perte<br>Destruction<br>Contamination<br>Corruption<br>Divulgation<br>Revente<br>Piratage<br>Usurpation<br>Blocage<br>Fuite<br>Infiltration<br>Détérioration<br>Explosion<br>Surchauffe<br>Engorgement<br>Violation<br>Inondation<br>Séisme<br>Sabotage<br><br> | Valeur métier       | 1 - Mineure<br>2 - Significative<br>3 - Grave<br>4 - Critique |

### 3.2) Scénarios de risque
Définir les scénarios de risque rassemblant la menace qui par un moyen va atteindre une valeur métier pour faire une action précise et trier en fonction du niveau de risque réel

| Identifiant | **Scénario**                     | **Chemin d’attaque**  | **Évènements redoutés**                                 | **Gravité actuelle**                                                | **Vraisemblance**                                              | Risque                    |
| ----------- | -------------------------------- | --------------------- | ------------------------------------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------- | ------------------------- |
| SX          | Acteur de risque + Objectif visé | Via quel moyen/acteur | **Évènements redoutés + {Bien support, Valeur métier}** | 1 – Mineure  <br>2 – Significative  <br>3 – Grave  <br>4 - Critique | 1 – Minimale  <br>2 – Moyenne  <br>3 – Forte  <br>4 – Maximale | (Gravité * Vraisemblance) |


## 4) Socle et traitement 

### 4.1) Normes 
Lister l'ensemble des normes pouvant s'appliquer et offrant un ensemble de mesures afin de sécuriser le SI et les données concernées

| **Norme**                  | **Description** |
| -------------------------- | --------------- |
| - ISO<br>- ANSSI<br>- RGPD | Description     |

### 4.2) Mesures de sécurité pour réduction des risques
Calculer le nouveau niveau de risques afin de réduire ou combler la vulnérabilité déterminée et exploitée par les sources de menaces.

| Scénario | Risque initial | Vulnérabilité exploitée | **Mesures de sécurité applicable** | **Gravité résiduelle** | **Vraisemblance résiduelle** | **Risque résiduel** |
| -------- | -------------- | ----------------------- | ---------------------------------- | ---------------------- | ---------------------------- | ------------------- |
| S1       |                |                         |                                    |                        |                              |                     |

## 5) Document final à produire

### 5.1) Tableau des scénarios et niveau de risques

| **Scénarios de menaces** | **Gravité initiale** | **Vraisemblance initiale** | **Risque inital** | **Évitement** | **Réduction** | **Prise** | **Transfert** | **Mesures de sécurité** | **Gravité résiduelle** | **Vraisemblance résiduelle** | **Risque résiduel** | **Évitement** | **Réduction** | **Prise** | **Transfert** |
| ------------------------ | -------------------- | -------------------------- | ----------------- | ------------- | ------------- | --------- | ------------- | ----------------------- | ---------------------- | ---------------------------- | ------------------- | ------------- | ------------- | --------- | ------------- |
|                          |                      |                            |                   | Oui/Non       | Oui/Non       | Oui/Non   | Oui/Non       |                         |                        |                              |                     | Oui/Non       | Oui/Non       | Oui/Non   | Oui/Non       |
# Chronologie par ateliers

## 1) Cadre et socle de sécurité

### 1.1) Cadre du système
Renseigner les informations clés du système
### 1.2) Cadre des participants et acteurs
Renseigner les participants et acteurs clés du système
### 1.3) Paramètre valeurs métier
Renseigner les valeurs métier
### 1.4)Paramètre biens supports
Renseigner les biens support
### 1.5) Vulnérabilités
Définir les vulnérabilités qui affectent les biens supports
### 1.6) Socle de sécurité
Déterminer le socle de sécurité
### 1.7) Normes
Déterminer les normes applicables

## 2) Source de risque

### 2.1) Source de risque
Identifier les sources de risque
### 2.2) Objectifs visés
Identifier les objectifs visés
### 2.3) Couples SR / OV
Evaluer les couples SR / OV
Sélectionner les couples SR / OV retenues

## 3) Scénarios stratégiques

### 3.1) Parties prenantes
Définir les parties prenantes interne/externes au SI (client, prestataires, propriétaire)
Définir critère de confiance pour chaque parties prenantes
Evaluer les parties prenantes internes et externes
### 3.2) Scénarios stratégiques
Elaborer les scénarios stratégiques
Définir les mesures mises en place de l'écosystème

## 4) Scénarios opérationnels

### 4.1) Scénarios opérationnels
Elaborer lesscénarios opérationnels
Evaluer la vraisemblance des scénarios opérationnels

## 5) Traitement du risque

### 5.1) Scénarios de risque
Synthèse des scénarios de risques
Décider de la stratégie de traitement de risques
### 5.2) Mesures
Définir les mesures de sécurité pour réduire les scénarios de risques
### 5.3) Plan de traitement
Définir un plan de traitement 
### 5.4) Rapport
Documenter les risques résiduels
