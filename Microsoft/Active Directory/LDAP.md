# Acteurs de LDAP
1. **AD contient l'annuaire du réseau** : Active Directory est le service d'annuaire qui stocke les informations sur les utilisateurs, les ordinateurs, les groupes et d'autres ressources dans un environnement réseau.
  
2. **Les applications AD qui ont besoin d'accéder à des informations de l'annuaire utilisent le protocole LDAP afin d'effectuer des requêtes vers l'annuaire AD** (controleur de domaine): Lorsque des applications ou des services ont besoin d'extraire ou de manipuler des données de l'annuaire d'Active Directory, elles utilisent le protocole LDAP pour ce faire.

3. Les contrôleurs de domaine AD : Ce sont eux les serveurs LDAP qui possède une copie de l'annuaire AD et qui capable de répondre au requête LDAP pour AD. 
# Sécurité et authentification de LDAP
* Comme tout services au sein de AD, il est nécessaire d'être pré-enregistré au sein d'AD pour pouvoir obtenir un ticket de service pour pouvoir interagir avec le service LDAP du controleur de domaine 
1. **Authentification initiale** :
    - Lorsqu'un ordinateur (ou utilisateur) rejoint un domaine Active Directory, il est créé un compte d'ordinateur (ou compte utilisateur) dans l'AD. Ce compte est associé à un mot de passe secret.
    - Chaque fois que cet ordinateur démarre (ou que l'utilisateur se connecte), il utilise ce mot de passe pour prouver son identité auprès du contrôleur de domaine (DC) et obtenir un ticket Kerberos (comme expliqué précédemment).
    - Une fois le ticket obtenu, l'ordinateur ou l'utilisateur peut s'authentifier auprès de n'importe quel service au sein du domaine sans avoir à ressaisir des identifiants, grâce au mécanisme de Kerberos.
2. **Consultation de l'annuaire via LDAP** :
    - Une fois qu'un ordinateur ou un utilisateur est authentifié, lorsqu'il fait une requête LDAP pour consulter l'annuaire, cette requête est accompagnée du ticket Kerberos.
    - Le contrôleur de domaine vérifie le ticket pour s'assurer que la requête provient bien d'un ordinateur ou d'un utilisateur authentifié du réseau AD.
    - Par défaut, n'importe quel utilisateur authentifié peut consulter l'annuaire AD, mais des permissions peuvent être configurées pour restreindre les accès à certaines parties de l'annuaire.

Si un acteur malveillant tente simplement d'envoyer une demande à tous les hôtes, sans disposer d'un ticket Kerberos valide, le contrôleur de domaine refusera l'accès à l'annuaire. Cependant, des précautions supplémentaires doivent être prises car il existe d'autres vecteurs d'attaque, tels que des attaques par usurpation, pour lesquels le réseau doit être préparé et protégé.
