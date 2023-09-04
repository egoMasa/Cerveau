# Guide sur les emails

# Résume 

1. **SMTP (Simple Mail Transfer Protocol) :** C'est le protocole utilisé pour envoyer des e-mails. Si vous voulez considérer la messagerie électronique comme un service postal, SMTP serait le facteur qui livre le courrier.
    
2. **POP3 (Post Office Protocol version 3) :** Il permet à un client de messagerie électronique de télécharger les e-mails depuis un serveur de messagerie vers l'ordinateur de l'utilisateur. Une fois téléchargés, les e-mails sont généralement supprimés du serveur. Pensez-y comme à une boîte postale : une fois que vous avez pris le courrier, il n'y reste plus.
    
3. **IMAP (Internet Message Access Protocol) :** Il permet également à un client de messagerie électronique de récupérer des e-mails depuis un serveur, mais contrairement à POP3, IMAP laisse les e-mails sur le serveur. Cela permet à plusieurs appareils (comme un téléphone et un ordinateur) d'accéder aux mêmes e-mails. Pensez-y comme à une boîte postale transparente : vous pouvez voir et lire le courrier, mais il reste dans la boîte pour que d'autres puissent également le voir.
    

En somme, SMTP est pour envoyer, tandis que POP3 et IMAP sont pour recevoir, chacun avec une manière différente de traiter les e-mails reçus.

# 1) SMTP (Simple Mail Transfer Protocol)

- Protocole est utilisé pour l'_**envoi**_ des emails
- Etape lors d'un envoi de mail :

1. Le client de messagerie de l'envoyeur (par exemple, Gmail, Outlook) se connecte au serveur SMTP de son fournisseur de services de messagerie
2. Le serveur SMTP transfére le message vers le serveur de messagerie du destinataire.
	1. Extraction du domaine : Le serveur SMTP extrait le domaine de l'adresse e-mail du destinataire, qui est la partie après le "@". Par exemple, pour l'adresse "[destinataire@example.com](mailto:destinataire@example.com)", le domaine est "example.com".
	
	4. Requête DNS : Le serveur SMTP effectue une requête DNS pour rechercher l'enregistrement MX (Mail eXchanger) associé au domaine. L'enregistrement MX indique le nom d'hôte du serveur de messagerie qui gère les e-mails pour ce domaine.
	
	5. Résolution du nom d'hôte : Le DNS renvoie le nom d'hôte du serveur MX associé au domaine. Le serveur SMTP effectue alors une nouvelle requête DNS pour obtenir l'adresse IP du serveur MX en résolvant le nom d'hôte.
	
	6. Connexion et transmission : Une fois l'adresse IP du serveur MX obtenue, le serveur SMTP établit une connexion avec ce serveur et transfère l'e-mail.
        

# 2) POP3 (Post Office Protocol 3) et IMAP (Internet Message Access Protocol)

## **POP3**
Permet de télécharger les e-mails depuis le serveur de messagerie vers l'ordinateur ou l'appareil mobile de l'utilisateur. Une fois téléchargés, les e-mails sont généralement supprimés du serveur, et les modifications apportées aux e-mails localement (par exemple, la suppression ou le marquage comme lu) ne sont pas synchronisées avec le serveur.
	- Les emails sont téléchargés et stockés sur un seul appareil.
	- Les messages envoyés sont stockés sur le seul appareil à partir duquel l'email a été envoyé.
	- Les emails ne peuvent être consultés que depuis le seul appareil sur lequel les emails ont été téléchargés.
	- Si vous souhaitez conserver les messages sur le serveur, assurez-vous que l'option "Garder les emails sur le serveur" est activée, sinon tous les messages sont supprimés du serveur une fois téléchargés sur l'application ou le logiciel du seul appareil.
- 
## IMAP: 
Permet de synchroniser les e-mails entre le serveur de messagerie et les appareils de l'utilisateur. Les e-mails restent stockés sur le serveur, et les modifications apportées aux e-mails sont synchronisées entre tous les appareils connectés au même compte de messagerie.
	- Les emails sont stockés sur le serveur et peuvent être téléchargés sur plusieurs appareils.
	- Les messages envoyés sont stockés sur le serveur.
	- Les messages peuvent être synchronisés et consultés sur plusieurs appareils.

- Etapes de réception :
1. Le serveur de messagerie du destinataire (serveur MX) reçoit l'email et le stocke dans la boîte de réception du destinataire. L'e-mail reste sur le serveur jusqu'à ce que le destinataire le consulte.
2. Le destinataire se connecte à sa boîte de réception en utilisant un client de messagerie (Gmail, Outlook) et un protocole de réception (POP3 ou IMAP) pour lire l'email reçu.
3. Le client de messagerie doit fournir les informations d'authentification (adresse e-mail et mot de passe) du destinataire pour accéder à la boîte de réception.
4. Le client de messagerie récupère les e-mails du serveur en fonction du protocole utilisé (POP3 ou IMAP) et les affiche dans la boîte de réception du destinataire.

# 4) Menaces via mails

- Phising : e-mails frauduleux qui ressemblent à des messages légitimes d'entreprises ou d'institutions, incitant les destinataires à cliquer sur des liens ou à ouvrir des pièces jointes malveillantes.
- Bruteforce : Compliqué car souvent restreint + 2FA
- Envoi de fichier malveillant
- MITM : Interceptent et modifient les communications entre deux parties en se faisant passer pour un serveur MX

# 5) ProtonMail

- Service de messagerie sécurisé basé en Suisse
- Offre un chiffrement de bout en bout pour les e-mails.
- e-mails sont chiffrés sur l'appareil de l'expéditeur et ne peuvent être déchiffrés que sur l'appareil du destinataire.
- ProtonMail ne peut pas accéder aux e-mails chiffrés
- Différentes méthode de chiffrements selon le destinataire
	- Communication entre 2 emails proton
		- Chiffrement de bout en bout est automatiquement appliqué.
		- e-mail est chiffré sur l'appareil de l'expéditeur et ne peut être déchiffré que sur l'appareil du destinataire.
	- Communication entre proton et gmail
		- On utilise la fonction "Envoyer un e-mail chiffré à des adresses non-ProtonMail" de ProtonMail.
		- Définir un mot de passe pour l'e-mail, qui sera chiffré avant d'être envoyé.
		- Le destinataire recevra un lien vers une page Web sécurisée où il pourra entrer le mot de passe pour déchiffrer et lire l'e-mail.
		- Partager le mot de passe avec le destinataire par un moyen de communication sûr et distinct, comme un message texte ou un appel téléphonique.
		- Particularité :
			- Si on n'utilise pas "Envoyer un e-mail chiffré à des adresses non-ProtonMail", l'e-mail sera chiffré en transit via TLS mais il ne sera pas chiffré de bout en bout. Cela signifie que le fournisseur de services de messagerie du destinataire pourrait potentiellement accéder au contenu de l'e-mail.