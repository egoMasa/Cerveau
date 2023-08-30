# Guide sur chiffrement et crytographie

## Eléments du chiffrement 

1.  Clés publiques et privées : Dans le système de cryptographie asymétrique, chaque entité dispose d'une paire de clés, une clé publique et une clé privée. La clé publique est partagée avec tous, tandis que la clé privée reste secrète. Tout message chiffré avec la clé publique d'une entité ne peut être déchiffré qu'avec sa clé privée correspondante.
    
2.  Certificats : Un certificat est un document numérique émis par une autorité de certification (CA) qui atteste l'identité d'une entité (comme un site web) et associe cette identité à sa clé publique. Les certificats utilisent généralement le format X.509.
    
3.  Signatures : Les signatures numériques sont utilisées pour garantir l'intégrité et l'authenticité des données. Une signature est créée en appliquant un algorithme de hachage au contenu, puis en chiffrant le hachage avec la clé privée du signataire. Pour vérifier la signature, le destinataire déchiffre la signature avec la clé publique du signataire, puis compare le hachage obtenu avec le hachage calculé à partir du contenu reçu.

## Etablissement d'une connexion sécurisée
1.  Le Navigateur se connecte au Site en utilisant HTTPS. Le Site envoie au Navigateur son certificat, qui contient la clé publique du Site et est signé par la cléf privée une autorité de certification (CA) de confiance.
    
2.  Le Navigateur vérifie la validité du certificat en s'assurant que la signature correspond à la clé publique de l'autorité de certification, et que le certificat n'est pas expiré ou révoqué. Si le certificat est valide, le Navigateur sait qu'il communique avec le vrai Site et non avec un imposteur.
    
3.  Le Navigateur et le Site établissent une clé de session en utilisant un protocole d'échange de clés, tel que le protocole de Diffie-Hellman. Le Navigateur chiffre la clé de session avec la clé publique du Site et l'envoie au Site, qui la déchiffre avec sa clé privée. À ce stade, le Navigateur et le Site disposent de la même clé de session.
    
4.  Les données échangées entre le Navigateur et le Site sont maintenant chiffrées et déchiffrées à l'aide de la clé de session, assurant la confidentialité des informations. Les messages peuvent également être signés numériquement pour garantir leur intégrité et leur authenticité.
    
5.  Lorsque le Navigateur envoie des données au Site, il peut également utiliser la clé publique du Site pour chiffrer les données. De cette manière, seuls le Site, avec sa clé privée correspondante, peut déchiffrer et accéder aux données.
    
6.  Le Site peut également utiliser sa clé privée pour signer numériquement les messages envoyés au Navigateur. Le Navigateur peut vérifier la signature en utilisant la clé publique du Site, garantissant ainsi l'intégrité et l'authenticité des données reçues.
    
7.  La clé de session est utilisée pour chiffrer les données échangées entre le Navigateur et le Site pendant toute la durée de la session. Cette clé est éphémère et généralement remplacée périodiquement ou à chaque nouvelle session pour garantir la sécurité des communications.
    
8.  À la fin de la session, la clé de session est détruite des deux côtés, garantissant ainsi que les données échangées ne peuvent plus être déchiffrées même si la clé de session est compromise ultérieurement.

# Hashing

* Notion de hashage 
	* Sortie d'une fonction de hashage
	* Convertit une entrée (par exemple, un mot de passe) en une chaîne fixe de caractères, qui représente l'empreinte numérique de l'entrée
	* Une fonction de hachage transforme toujours la même entrée en la même sortie
	* Pas possible de récupérer l'information d'origine à partir de cette valeur de hash.
	* Un petit changement dans l'entrée produit une modification significative dans le hash résultant
* Exemple d'un fonctionnement de hashage 
	* Le serveur stocke le mot de passe renseigne par l'utilisateur en créant un hash de ce mot de passe 
	* Quand le client veut se connecter, il retape son mdp, le serveur refait le hash du mot de passe et si la correspondance entre la BDD et le mot de passe renseingné est correct c'est bon 
	* Ca permet que le serveur ne stocke jamais le mot de passe directement.
* Notion de Rainbow table
	* Quand 2 utilisateurs on le meme mot de passe et donc le meme hash
	* Pour eviter ca on ajoute un sel au mot de passe qui est un chiffre généré aléatoirement dans la base de données et unique à chaque user avant de le hasher

* Notion de chiffrement 
	* Transforme les mots de passe en une forme illisible à l'aide d'un algorithme de chiffrement
	* Possibilité de retrouver l'information de base grace à la cléf de déchiffrement
	* AES, RSA, DES

* Différence entre hasher et crypter
	* Le hashage est  unidirectionnel ttandis que le chiffrement est  bidirectionnel. 
	* Le hashage est généralement préféré pour stocker les mots de passe, car même si quelqu'un parvient à accéder à la base de données de mots de passe, il ne pourra pas récupérer les mots de passe d'origine à partir des valeurs de hash.

* Fonction de hashage
	* Il n'y a pas de clé 
	* Censé être impossible à retrouver le mot originel
	* Prend des données d'entrée de n'importe quelle taille et crée un résumé ou "condensé" de ces données. La sortie est de taille fixe.
	* MD5 et SHA-256, SHA-3

* Faiblesse du chiffrement 
	* Il n'est pas possible de crypter les mots de passe, car la clé doit être stockée quelque part. Si quelqu'un obtient la clé, il peut simplement décrypter les mots de passe.

* Intéret du hashage
	1.  **Protection des données sensibles** : Lorsqu'un mot de passe est haché, le mot de passe d'origine ne peut pas être retrouvé même si le hachage est compromis. C'est une caractéristique essentielle pour protéger les informations sensibles contre les attaques.
	    
	2.  **Vérification sans révélation** : Un autre avantage important du hachage est qu'il permet de vérifier si un mot de passe est correct sans avoir besoin de connaître le mot de passe réel. Par exemple, lorsque vous entrez votre mot de passe sur un site web, le site web hache le mot de passe que vous avez entré et compare ce hachage avec le hachage stocké dans sa base de données. Si les deux hachages correspondent, vous êtes authentifié. Cela signifie que le site web n'a pas besoin de stocker votre mot de passe en clair, ce qui améliore considérablement la sécurité.
	    
	3.  **Intégrité des données** : Le hachage peut également être utilisé pour vérifier l'intégrité des données. Par exemple, si vous téléchargez un fichier, vous pouvez calculer le hachage du fichier et le comparer avec le hachage fourni par le site web à partir duquel vous avez téléchargé le fichier. Si les deux correspondent, cela signifie que le fichier n'a pas été altéré pendant le téléchargement.
	    
	4.  **Uniformité** : Les fonctions de hachage produisent une sortie de taille fixe quelle que soit la taille de l'entrée. Cela peut être utile pour gérer efficacement l'espace de stockage, surtout lorsque vous traitez de grandes quantités de données.

## Reconnaitre les différents types de hash
* Outils de reconnaissance de HASH comme HashCat ou [hashID]( https://pypi.org/project/hashID/)
* Les hachages Unix stocker dans ``/etc/shadow`` et du format 
```
est$format$rounds$salt$hash.
```
* Les hachages Windows
	* **SAM** : SAM est l'acronyme de Security Accounts Manager. Il s'agit d'une base de données dans Windows qui stocke les identifiants et mots de passe des utilisateurs locaux sous forme de hachages.
	* **Mimikatz** : C'est un outil de sécurité populaire qui peut être utilisé pour extraire des informations d'authentification de Windows, y compris les hachages de mots de passe stockés dans le SAM. Bien qu'il soit un outil légitime dans le cadre de tests de sécurité (comme des tests d'intrusion), il est souvent utilisé de manière malveillante par les pirates pour voler des informations d'authentification.
	- **Hachages NT et LM** : Ces termes font référence à deux types de hachages utilisés par Windows pour stocker les mots de passe.
	    - Le hachage NT (NT Hash), ou NTLMv1, est un algorithme de hachage plus récent et plus sûr que Windows utilise pour stocker les mots de passe. Il est basé sur l'algorithme MD4.
	    - Le hachage LM (Lan Manager Hash), ou LM Hash, est un ancien algorithme de hachage qui était utilisé dans les versions plus anciennes de Windows. Il est moins sûr que le hachage NT et est désactivé par défaut dans les versions plus récentes de Windows. Cependant, dans certains cas, les hachages LM peuvent encore être présents dans le SAM.

## Cracker des hachages
* CrackStation 
* HashCat 
```
hashcat -m 0 -a 0 hashfile.txt wordlist.txt
- m : Spécifie le type de hash à partir de la numérotation sur le site de hashcat 
- a : Spécifie le mode d'attaque : dico(0), combinaison(1), bruteforce(3)
```
* John The Ripper 
```
john --wordlist=wordlist.txt hashfile.txt     #Dictionnaire
john --incremental hashfile.txt               #Brutefore

```
* Méthode de déhachage
	* Attaque brute force 
		* On essaye toutes les combinaisons possibles de mots de passe jusqu'à ce que vous trouviez celui qui produit le bon hachage
	* Attaque par dictionnaire
		* On utilise une liste de mots de passe couramment utilisés (le "dictionnaire") et à hacher chacun d'eux jusqu'à ce que vous trouviez une correspondance.
	* Tables arc-en-ciel
		* On utilise une table précalculée de hachages et de mots de passe correspondants. Au lieu de hacher chaque mot de passe possible au moment de l'attaque, l'attaquant prépare une table de correspondances à l'avance et peut alors chercher rapidement un hachage dans la table.