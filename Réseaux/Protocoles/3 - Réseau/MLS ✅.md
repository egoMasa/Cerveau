
## Multilayer Switching (MLS)

Les commutateurs multicouches (MLS) permettent à la fois la commutation (couche 2) et le routage (couche 3) sur un seul équipement. Ce type de commutation améliore la performance des réseaux en éliminant le besoin de routeurs pour les opérations de routage entre différents VLANs sur le même commutateur.

### Configuration :

1. **Passage d'un port de commutation (Layer 2) à un port de routage (Layer 3)**:
Pour qu'un port fonctionne comme un port de routage plutôt que comme un port de commutation, il faut désactiver la fonctionnalité "switchport".
```cisco
interface G0/0
    no switchport
```

2. **Activer le routage IPv6**:
Si vous avez l'intention d'utiliser IPv6, activez le routage IPv6 avec la commande suivante.
```cisco
ipv6 unicast-routing
```

3. **Création d'une Interface de VLAN (SVI)**:
Une Interface de VLAN (SVI) est une interface virtuelle sur un commutateur multiniveau, associée à un VLAN particulier.
```cisco
interface vlan XX
    ipv6 address [ADRESSE IPV6]/[MASQUE]
    no shutdown
```
**Note:** Remplacez `[ADRESSE IPV6]/[MASQUE]` par l'adresse et le masque appropriés.

4. **Activer IPv6 sur le commutateur multicouche**:
Pour optimiser le commutateur pour les opérations IPv4 et IPv6, vous pouvez définir le modèle SDM (Switching Database Manager) pour privilégier une configuration dual-stack.
```cisco
sdm prefer dual-ipv4-and-ipv6 default
copy run startup-config
reload
```

### Suggestions supplémentaires:

- **Définition de la Gateway par défaut**: Une fois la SVI configurée, vous voudrez peut-être définir une gateway par défaut pour le commutateur :
```cisco
ip default-gateway [ADRESSE IP GATEWAY]
```

- **Activer le routage IP**: Si vous envisagez d'utiliser également IPv4, n'oubliez pas d'activer le routage IP avec la commande :
```cisco
ip routing
```

- **Expliquer le rôle des SVI**: Il pourrait être utile de mentionner pourquoi quelqu'un voudrait configurer une SVI. Par exemple, une SVI peut être utilisée pour gérer le commutateur à distance, pour le routage inter-VLAN ou pour appliquer des ACL.

- **Explication SDM**: Le modèle de la base de données de commutation (SDM) détermine comment le système utilise les ressources matérielles. Expliquer un peu plus en détail comment et pourquoi vous pourriez vouloir changer le modèle SDM serait bénéfique pour les apprenants.

---

Globalement, votre leçon offre un bon point de départ pour ceux qui sont nouveaux dans la configuration des commutateurs multicouches. Selon votre public, vous pourriez envisager d'approfondir certains sujets ou d'ajouter des exemples pratiques pour renforcer la compréhension.