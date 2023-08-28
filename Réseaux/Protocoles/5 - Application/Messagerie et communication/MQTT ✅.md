# Guide MQTT

## **Introduction** :
MQTT, ou Message Queuing Telemetry Transport, est un protocole de messagerie léger conçu pour les systèmes de communication M2M (machine à machine) et IoT (Internet des Objets). Étant donné sa faible empreinte, sa faible consommation de bande passante et sa capacité à fonctionner dans des environnements réseau instables, MQTT est particulièrement bien adapté aux dispositifs connectés et aux applications mobiles.

**Historique** :
Créé en 1999 par Andy Stanford-Clark d'IBM et Arlen Nipper d'Arcom, MQTT a été conçu pour relier les pipelines via satellite avec une faible bande passante.

## **Principales Caractéristiques** :
1. **Léger** : Conçu pour minimiser la bande passante et les ressources du système.
2. **Publish/Subscribe** : Les clients peuvent publier des messages sur des "topics" et s'abonner à des topics pour recevoir des messages.
3. **Qualité de service (QoS)** : Offre trois niveaux de livraison : 0 (au plus une fois), 1 (au moins une fois) et 2 (exactement une fois).
4. **Maintien de session** : Possibilité de conserver les informations de session entre les sessions avec les "Last Will and Testament" (LWT) et les messages retenus.
5. **Sécurité** : Prise en charge native de SSL/TLS pour le cryptage des données et l'authentification.

## **Fonctionnement** :
- **Broker** : Le serveur central en MQTT est appelé "broker". Il est responsable de la gestion des messages entre les clients.
- **Client** : Dispositif ou application qui publie des messages à des topics ou s'abonne à des topics pour recevoir des messages.

## **Avantages** :
- **Efficacité** : Utilise moins de bande passante par rapport à d'autres protocoles.
- **Flexibilité** : Bien adapté aux dispositifs à faible puissance et aux réseaux instables.
- **Scalabilité** : Capable de gérer un grand nombre de clients simultanément.

## **Inconvénients** :
- **Dépendance au broker** : Nécessite un broker pour fonctionner, ce qui peut être un point unique de défaillance.
- **Sécurité** : Bien que MQTT supporte SSL/TLS, il n'est pas toujours implémenté, ce qui peut exposer les systèmes à des risques.

## **Ports standards pour MQTT** :
- **Port 1883** : Utilisé pour les communications MQTT non sécurisées.
- **Port 8883** : Utilisé pour les communications MQTT sécurisées avec SSL/TLS.

## **Extensions et variantes** :
- **MQTT-SN (MQTT for Sensor Networks)** : Une variante de MQTT conçue pour les réseaux de capteurs sans fil qui ne sont pas basés sur TCP/IP.

## **Résumé** :
MQTT est un protocole de communication efficace et fiable conçu pour les environnements où la bande passante et les ressources système sont limitées. Son modèle de publication/abonnement facilite la mise en réseau des appareils et le partage d'informations de manière cohérente. Avec l'explosion de l'IoT, MQTT est de plus en plus adopté dans de nombreuses applications allant de la domotique à l'industrie 4.0. Comprendre son fonctionnement et ses caractéristiques peut aider à construire des systèmes plus réactifs et évolutifs.