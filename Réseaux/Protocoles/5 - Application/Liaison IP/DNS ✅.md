# Guide DNS
Le DNS, ou **Système de Noms de Domaine**, est un composant essentiel de l'infrastructure internet qui traduit les noms de domaine faciles à comprendre pour les humains (par exemple, [www.example.com](http://www.example.com/)) en adresses IP (par exemple, 192.0.2.44). Ce processus de traduction nous permet de nous connecter facilement à des sites web et autres ressources en ligne sans avoir à mémoriser des adresses IP numériques complexes.

## **Hiérarchie des domaines** :

1. **Résolveur DNS** : C'est le point de contact initial de votre appareil avec l'infrastructure DNS, souvent fourni par votre Fournisseur d'Accès à Internet (FAI) ou par un service tiers comme Google Public DNS.
    
2. **Serveurs Racines** : Ces serveurs se trouvent au sommet de la hiérarchie DNS. Ils guident les requêtes DNS vers les serveurs de domaine de premier niveau appropriés.
    
3. **Serveurs TLD (Top-Level Domain)** : Situés juste en dessous des serveurs racines dans la hiérarchie, ils gèrent les noms de domaine pour les domaines de premier niveau, comme .com, .org, et d'autres. Chaque TLD, tel que .com ou .fr, possède son propre ensemble de serveurs TLD.
    
4. **SLD (Second-Level Domain)** : C'est la partie du nom de domaine qui se trouve juste avant le TLD. Il représente généralement le nom du site web ou de l'organisation. Par exemple, dans "exemple.com", "exemple" est le SLD.
    
5. **Sous-domaine** : Il s'agit d'une subdivision d'un SLD. Par exemple, dans `produits.exemple.com`, "produits" est le sous-domaine. Un SLD peut avoir plusieurs sous-domaines.
    
6. **Serveurs de Noms Autoritaires** : Ces serveurs stockent les enregistrements DNS relatifs à un domaine spécifique (par exemple, example.com) et fournissent des réponses autoritaires aux requêtes concernant ce domaine.
    

## **Types d'enregistrements DNS** :

- **Enregistrement A (Address)** : Traduit un nom de domaine en adresse IPv4. C'est l'enregistrement le plus couramment utilisé pour pointer un nom de domaine ou un sous-domaine vers une adresse IP.
    
- **Enregistrement AAAA (Address)** : Équivalent de l'enregistrement A mais pour les adresses IPv6.
    
- **Enregistrement CNAME (Canonical Name)** : Crée un alias pour un nom de domaine, permettant d'associer un nom de domaine à un autre. C'est utile lorsque plusieurs noms de domaine doivent pointer vers la même adresse IP.
    
- **Enregistrement MX (Mail Exchange)** : Spécifie les serveurs de messagerie qui sont responsables de recevoir les e-mails pour un domaine donné.
    
- **Enregistrement NS (Name Server)** : Indique les serveurs DNS autoritaires pour un domaine ou un sous-domaine. Par exemple, il peut spécifier quel serveur s'occupe de `produits.exemple.com` par rapport à `support.exemple.com`.
    
- **Enregistrement TXT (Texte)** : Peut contenir du texte libre ou des informations formatées, souvent utilisées pour la vérification du domaine ou pour d'autres informations non structurées.

## **Exécution d'une requête DNS** :

1. Lors d'une demande de résolution de nom, le navigateur vérifie d'abord s'il possède déjà cette résolution dans son cache. Si ce n'est pas le cas, il passe à l'étape 2.
2. La demande est alors envoyée à un serveur DNS récursif, qui est généralement un serveur proche de l'utilisateur avec un cache de résolutions réduit. Si la réponse n'est pas dans ce cache, il passe à l'étape 3.
3. La requête est redirigée vers le serveur DNS racine, qui guide la requête en fonction du TLD (par exemple .com, .fr) vers un serveur DNS correspondant à ce TLD.
4. Le serveur TLD contacte ensuite le serveur d'autorité DNS pour obtenir la réponse finale. Cette réponse est ensuite renvoyée au serveur DNS récursif, qui la stocke dans son cache pour des requêtes futures.
## Configuration DNS Cisco

### Coté serveur DNS
1. **Accès au mode de configuration global** :
    ```bash
    Router> enable
    Router# configure terminal
    ```

2. **Définissez l'adresse IP du serveur DNS** (remplacez `x.x.x.x` par l'adresse IP réelle de votre serveur DNS) :
    ```bash
    Router(config)# ip name-server x.x.x.x
    ```

3. **Pour activer le service DNS** :
    ```bash
    Router(config)# ip dns server
    ```

4. **Ajout d'un enregistrement statique** (par exemple, pour un serveur web) :
    ```bash
    Router(config)# ip host www.example.com x.x.x.x
    ```

5. **Quitter le mode de configuration** :
    ```bash
    Router(config)# end
    ```

6. **Sauvegardez la configuration** :
    ```bash
    Router# copy running-config startup-config
    ```
### Coté client DNS 

1. **Accès au mode de configuration global** :
    ```bash
    Router> enable
    Router# configure terminal
    ```

2. **Définir l'adresse IP du serveur DNS** (remplacez `x.x.x.x` par l'adresse IP de votre serveur DNS) :
    ```bash
    Router(config)# ip name-server x.x.x.x
    ```

3. **Configuration de l'interface pour l'utilisation du DHCP (si nécessaire)** :
    ```bash
    Router(config)# interface [type][number]
    Router(config-if)# ip address dhcp
    ```

    Remarque : `[type][number]` représente le type et le numéro d'interface, par exemple `GigabitEthernet0/0`.

4. **Quitter le mode de configuration** :
    ```bash
    Router(config-if)# end
    ```

5. **Sauvegardez la configuration** :
    ```bash
    Router# copy running-config startup-config
    ```

6. **Testez la configuration** :
    Pour vérifier si la résolution DNS fonctionne correctement, utilisez la commande :
    ```bash
    Router# ping www.example.com
    ```
## Commandes d'interrogation DNS
* Interroger les serveurs DNS et obtenir des informations sur la résolution des noms de domaine.
```
nslookup example.com
nslookup -type=ns example.com
```
* Savoir IP serveur DNS configurés sur le système,
```
ipconfig /all
ipconfig /flushdns # Vider cache DNS de ma machine
```
* Interroger les serveurs DNS et d'obtenir des informations sur un nom de domaine via un DNS précis
```
dig @8.8.8.8 example.com
```
* Requêter différents types d'enregistrements DNS
```
dig example.com {A, AAAA, MX, NS, CNAME, SOA}
```
* Afficher tous les serveurs DNS impliqués dans la résolution d'un nom de domaine
```
dig example.com +trace
```
* Résoudre les noms de domaine en adresses IP, d'interroger les serveurs DNS et d'obtenir divers types d'enregistrements DNS (Linux)
```
host example.com
```

**En résumé**, le DNS est un mécanisme vital qui permet une navigation fluide et facile sur internet. Comprendre son fonctionnement et ses enjeux de sécurité est essentiel pour quiconque travaille dans le domaine de l'informatique ou souhaite avoir une meilleure compréhension de la manière dont fonctionne l'internet.