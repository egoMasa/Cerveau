# 1) Introduction
* IPsec est un framework (ensemble) qui permet de protéger un trafic IP entre 2 points
* IPsec est un protocole de chiffrement et d'authentification utilisé entre 2 interfaces
* IPsec offre les fonctionnalités suivantes 
	* ***Chiffrement*** des données routées entre l'expéditeur et le destinataire
	* ***Intégrité*** : Vérification de la non modification des données transmises via une valeur de hachage qui permet à l'expéditeur et au destinataire de vérifier si des modifications ont été apportées au paquet
	* ***Authentification*** : Authentification mutuelle entre l'expéditeur et le destinataire avant échange
	* ***Anti-rejeu*** (anti-replay) : Empeche via des numéros de séquence d'envoyer un paquet en double
# 2) Détails du Framework

| Catégorie            | Protocole / Algorithme | Description                                                                 |
|----------------------|------------------------|-----------------------------------------------------------------------------|
| **Protocole IPsec**  | ESP                    | Fournit chiffrement, authentification, et intégrité des données.             |
|                      | AH                     | Fournit authentification et intégrité des données, sans chiffrement.         |
|                      | ESP + AH               | Combinaison pour une sécurité accrue, non courante.                          |
| **Chiffrement**      | DES                    | Chiffrement symétrique avec clé de 56 bits, considéré comme peu sûr.         |
|                      | 3DES                   | Amélioration de DES avec triple chiffrement, plus sûr.                       |
|                      | AES                    | Chiffrement symétrique moderne avec clés de 128, 192 ou 256 bits.            |
| **Authentification** | MD5                    | Algorithme de hachage pour authentification, vulnérable et considéré peu sûr.|
|                      | SHA                    | Famille d'algorithmes de hachage plus sûre que MD5.                          |
| **DH (Diffie-Hellman)** | DH1               | Implémentation de Diffie-Hellman avec un groupe de 768 bits.                 |
|                      | DH2                    | Utilise un groupe de 1024 bits, plus sûr que DH1.                            |
|                      | DH5                    | Utilise un groupe de 1536 bits, offre une sécurité renforcée.                |

# 3) Cas d'utilisation d'IPsec 
- Entre deux routeurs pour créer un VPN site à site qui relie deux réseaux locaux.
- Entre un pare-feu et un hôte Windows pour un VPN d'accès à distance.
- Entre deux serveurs Linux pour protéger un protocole non sécurisé comme telnet.

# 4) Etablissement d'un tunnel IPsec entre 2 interfaces via IKE (Internet Key Exchange)
* Le principe est simple, la phase 1 crée un canal sécurisé pour la négociation, tandis que la Phase 2 utilise ce canal pour établir le tunnel IPsec. Ce processus est conçu pour garantir que même si quelqu'un écoute les échanges initiaux, il ne sera pas capable de déchiffrer le trafic qui passe par le tunnel IPsec ou de compromettre les clés et les méthodes de chiffrement utilisées pour protéger les données.
### **Phase 1 - Établissement de la SA IKE:**
1. **Initiation:** L'initiateur envoie une proposition à l'autre partie (le répondant) indiquant les algorithmes qu'il supporte et les paramètres de sécurité qu'il souhaite utiliser.
    
2. **Réponse:** Le répondant choisit les paramètres appropriés à partir de la proposition et envoie cette sélection à l'initiateur.
    
3. **Échange de clés Diffie-Hellman:** Les deux parties échangent ensuite des informations basées sur l'algorithme de Diffie-Hellman pour générer une clé secrète partagée, sans avoir à transmettre la clé elle-même.
    
4. **Authentification:** Les deux parties s'authentifient mutuellement en utilisant des certificats ou des clés pré-partagées. L'authentification assure que vous communiquez avec la bonne entité.
    
À la fin de la phase 1, une SA IKE est établie, ce qui signifie que les deux parties peuvent maintenant communiquer en toute sécurité pour négocier les SAs IPsec.
### **Phase 2 - Négociation des SAs IPsec:**
5. **Initiation:** L'initiateur envoie une proposition pour la SA IPsec, indiquant les protocoles et les algorithmes qu'il souhaite utiliser pour le trafic IPsec.
6. **Réponse:** Le répondant envoie sa sélection de paramètres à l'initiateur.
7. **Création de clés:** Les clés sont générées pour le trafic IPsec basé sur la clé secrète partagée de la phase 1 et les paramètres de la phase 2.
    
À la fin de la phase 2, une SA IPsec est établie pour le trafic réel.
# 5) Transfert de données sécurisées dans le tunnel IPsec:
8. **Encapsulation:** Le trafic est encapsulé selon le mode choisi (transport ou tunnel) et le protocole (AH ou ESP). Si ESP est utilisé, le trafic est également chiffré.
9. **Transmission:** Le paquet encapsulé est ensuite transmis sur le réseau.
10. **Réception et décapsulation:** Le paquet est reçu par l'autre partie, désencapsulé, déchiffré (si ESP est utilisé), et l'intégrité est vérifiée.
# 6) Fin de la session:
11. **Expiration de la SA:** Après une certaine période ou un certain volume de données, la SA expire.
12. **Renégociation:** Si les deux parties souhaitent continuer à communiquer, elles peuvent renégocier de nouvelles SAs.
# 5) Chiffrement et authentification des données dans le tunnel

IPsec peut fonctionner selon deux modes distincts, qui déterminent comment les paquets de données sont traités et transmis sur le réseau :

1. **Mode de Transport** :
    - Dans ce mode, l'en-tête IP d'origine est conservé, et seules les données transportées (le payload) sont éventuellement chiffrées et/ou authentifiées.
    - Ce mode est souvent utilisé pour protéger les communications de bout en bout.
2. **Mode Tunnel** :
    - Le mode tunnel encapsule le paquet IP original dans un nouveau paquet IP avec un nouvel en-tête.
    - Cette méthode est couramment utilisée dans les configurations de VPN site à site où l'encapsulation permet de sécuriser le passage des paquets sur Internet, notamment parce que les adresses IP privées initiales ne peuvent pas être routées sur le réseau public.

### Comparaison des Protocoles IPsec AH et ESP

| Caractéristique       | AH Mode Transport           | ESP Mode Transport           | AH Mode Tunnel               | ESP Mode Tunnel               |
|-----------------------|-----------------------------|------------------------------|------------------------------|-------------------------------|
| **Authentification**  | Authentifie l'en-tête et le payload, sauf champs modifiables de l'en-tête. | Authentifie le payload uniquement. | Authentifie le nouvel en-tête et le payload, sauf champs modifiables de l'en-tête. | Authentifie le payload uniquement. |
| **Chiffrement**       | Non pris en charge.         | Chiffre le payload.          | Non pris en charge.          | Chiffre le payload encapsulé. |
| **Intégrité**         | Fournit l'intégrité pour l'en-tête et le payload. | Fournit l'intégrité pour le payload uniquement. | Fournit l'intégrité pour le nouvel en-tête et le payload. | Fournit l'intégrité pour le payload encapsulé uniquement. |
| **En-tête IP**        | Utilise l'en-tête IP original. | Utilise l'en-tête IP original. | Insère un nouvel en-tête IP pour encapsuler le paquet original. | Insère un nouvel en-tête IP pour encapsuler le paquet original. |
| **Usage commun**      | Protection des communications entre deux points finaux. | Souvent utilisé pour sécuriser la communication de bout en bout. | VPNs site à site, où les adresses IP privées ne sont pas routables sur Internet. | VPNs site à site; privilégié pour sa capacité de chiffrement. |



# 6) Configuration IPsec 

### Étape 1: Configuration de la Phase 1 (ISAKMP)
```plaintext
Router(config)# crypto isakmp policy [NUMÉRO_DE_POLITIQUE]
Router(config-isakmp)# encryption [TYPE_DE_CHIFFREMENT]
Router(config-isakmp)# hash [TYPE_DE_HACHAGE]
Router(config-isakmp)# authentication pre-share
Router(config-isakmp)# group [NUMÉRO_DE_GROUPE_DH]
Router(config-isakmp)# lifetime [DURÉE_DE_VIE]
Router(config-isakmp)# exit

```

### Étape 2: Définir la clé prépartagée utilisée pour l'authentification entre les deux routeurs.
```plaintext
Router(config)# crypto isakmp key [CLÉ_PRÉPARTAGÉE] address [IP_ROUTEUR_DISTANT]
```

### Étape 3: Configuration de la Phase 2 (IPsec)
```plaintext
Router(config)# crypto ipsec transform-set [NOM_DU_TRANSFORM_SET] esp-[ALGO_CHIFFREMENT] esp-[ALGO_HACHAGE]
Router(cfg-crypto-trans)# exit

```
### Étape 4: Créer une ACL pour le trafic à protéger par le tunnel IPsec
```plaintext
Router(config)# access-list [NUMÉRO_ACL] permit ip [RÉSEAU_LOCAL] [MASQUE_DE_SOUS_RÉSEAU_LOCAL] [RÉSEAU_DISTANT] [MASQUE_DE_SOUS_RÉSEAU_DISTANT]

```

### Étape 5: Créer une crypto map

Associez la transform set et l'ACL à une crypto map et définissez le peer.
```plaintext
Router(config)# crypto map [NOM_DE_LA_CRYPTO_MAP] [SÉQUENCE] ipsec-isakmp
Router(config-crypto-map)# set peer [IP_ROUTEUR_DISTANT]
Router(config-crypto-map)# set transform-set [NOM_DU_TRANSFORM_SET]
Router(config-crypto-map)# match address [NUMÉRO_ACL]
Router(config-crypto-map)# exit

```
### Étape 6: Appliquer la crypto map à l'interface

Appliquez la crypto map à l'interface qui se connecte au réseau externe ou à l'Internet.
```plaintext
Router(config)# interface [NOM_INTERFACE]
Router(config-if)# crypto map [NOM_DE_LA_CRYPTO_MAP]
Router(config-if)# exit

```

### Étape 7: Répétez le processus sur le routeur distant

### Étape 8: Vérification de la configuration
```plaintext
Router# show crypto isakmp sa
Router# show crypto ipsec sa
```

