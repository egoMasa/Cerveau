# Guide d'authentification SSO 

## Notion de SSO 
* Le **Single Sign-On (SSO)** est un mécanisme d'authentification qui permet à un utilisateur de se connecter à plusieurs systèmes ou applications en utilisant une seule paire d'identifiants.
* Une fois que l'utilisateur s'est authentifié auprès d'un service ou d'une application, il n'a pas besoin de se reconnecter lorsqu'il accède aux autres services associés.

## Fonctionnement du SSO
1. L'utilisateur tente de se connecter à une application ou un service.
2. Si l'utilisateur n'est pas encore authentifié, il est redirigé vers le service d'authentification SSO.
3. Une fois l'authentification réussie, le service SSO génère un ticket/token qui valide l'identité de l'utilisateur pour les autres services ou applications.
4. L'utilisateur utilise ce ticket/token pour accéder sans obstacle aux autres services associés.

## Types de SSO 

### 1) SSO Interne 
* Spécifiquement conçu pour un usage interne au sein des entreprises.
* Après s'être connecté une fois au réseau de l'entreprise, l'utilisateur peut accéder à diverses applications sans avoir à s'authentifier à nouveau.

### 2) SSO Externe
* Autorise l'authentification en utilisant les identifiants d'une plateforme extérieure (par exemple, Facebook, Google).
* Offre une expérience utilisateur fluide tout en utilisant des services d'authentification reconnus.

## Protocoles et services SSO

### 1) CAS (Central Authentication Service) 
* Conçu principalement pour les environnements web.
* Après une authentification réussie avec CAS, l'utilisateur peut accéder à toutes les applications associées sans se reconnecter.

### 2) OAuth
* OAuth n'est pas strictement pour l'authentification mais plutôt pour l'autorisation. Il permet à une application d'accéder à certaines informations d'un utilisateur à partir d'un autre service sans exposer le mot de passe de l'utilisateur.

### 3) OpenID Connect 
* Basé sur OAuth 2.0, il ajoute une couche d'authentification, retournant des informations sur l'identité de l'utilisateur ainsi qu'un token.

## Méthodes de connexion à un service

### 1) Portail d'authentification
* Typiquement une interface web où les utilisateurs entrent leurs identifiants pour accéder à un service ou une application.

### 2) Connexion VPN 
* Pour une sécurité accrue, les employés peuvent se connecter à leur réseau d'entreprise via un VPN, garantissant que la connexion est sécurisée et cryptée.

---

J'ai essayé de clarifier certains points, d'ajouter des informations manquantes et d'apporter une meilleure distinction entre certains concepts. Vous pouvez intégrer ces modifications selon ce qui convient le mieux à votre public cible.