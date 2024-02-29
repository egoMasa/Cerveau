# 1) Principe et explication

## Concept
* Lorsqu'on travaille avec des réseaux complexes par leur taille et par le nombre d’équipements, le routage dynamique devient une solution incontournable pour faciliter la gestion des routes.
* Le routage dynamique permet aux routeurs de choisir automatiquement les routes optimales pour acheminer le trafic réseau. 
* Les routeurs partagent et mettent à jour constamment leurs tables de routage pour réagir rapidement aux changements dans le réseau.
## Fonctionnement
1. Les routeurs annoncent les réseaux auxquels ils sont connectés à leurs voisins.
2. Ces informations sont transmises de routeur en routeur, formant ainsi une image complète de la topologie du réseau.
## Terminologies importantes
- _**Convergence**_ : Le temps nécessaire pour que tous les routeurs aient des tables de routage à jour après un changement de topologie.
- _**Répartition de charge**_ : Possibilité d'utiliser plusieurs chemins pour atteindre une même destination, optimisant ainsi l'utilisation des ressources réseau.
- _**Distance administrative**_ : Indicateur de la fiabilité d'une source d'information de routage. Une valeur faible signifie une grande fiabilité.
- _**Métrique**_ : Valeur utilisée par un protocole de routage pour déterminer le chemin optimal vers une destination.

- **Problématiques courantes** : Certaines routes peuvent être privilégiées par un protocole même si elles ne sont pas les plus optimales. C'est pourquoi il est parfois nécessaire d'ajuster manuellement les distances administratives.

![DYNAMIC_ROUTING1.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/DYNAMIC_ROUTING1.png)


# 2) Routage Intérieur (IGP)

| Caractéristique                  | Vecteur de Distance                                                 | État de Lien (Link-State)                                                                |
| -------------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Principe**                     | Utilisent le cumul des distances pour déterminer le chemin optimal. | Évaluent le coût de chaque lien pour déterminer le chemin le plus court.                 |
| **Base du calcul**               | Basé sur le nombre de sauts.                                        | Basé sur des facteurs comme la bande passante.                                           |
| **Partage d'informations**       | Partage complet de la table de routage entre les routeurs voisins.  | Tous les routeurs ont une vision complète de la topologie.                               |
| **Taille du réseau cible**       | Conçu pour les réseaux de petite à moyenne taille.                  | Adaptable à des réseaux de toutes tailles, souvent utilisé dans des réseaux plus grands. |
| **Convergence**                  | Relativement lente.                                                 | Rapide.                                                                                  |
| **Mises à jour**                 | Fréquentes, souvent via broadcast ou multicast.                     | Immédiate en cas de changement de topologie, via multicast.                              |
| **Exemples de protocoles**       | - EIGRP<br>- RIP/RIPv2                                              | - OSPF<br>- IS-IS                                                                        |
| **Connaissance de la topologie** | Limitée aux informations partagées par les voisins.                 | Complète, identique sur tous les routeurs dans le même domaine de routage.               |
![DYNAMIC_ROUTING2.png](https://github.com/egoMasa/Illustrations/blob/main/Illustrations/DYNAMIC_ROUTING2.png)