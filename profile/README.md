<h1 align="center">Vaelor</h1>

<p align="center">
  <strong>Serveur Minecraft survie semi-RPG français</strong><br>
  Java Edition · 1.21.8
</p>

<p align="center">
  <a href="https://vaelor.net/"><img src="https://img.shields.io/badge/Site-vaelor.net-2ea44f?style=for-the-badge" alt="Site"></a>
  <a href="https://discord.gg/hd4ZUTdEVs"><img src="https://img.shields.io/badge/Discord-Rejoindre-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"></a>
  <a href="https://vaelor.net/vote"><img src="https://img.shields.io/badge/Voter-Soutenir-orange?style=for-the-badge" alt="Vote"></a>
</p>

<p align="center">
  <code>play.vaelor.net</code>
</p>

---

## Le serveur

Vaelor est un serveur **survie semi-RPG** francophone : la base d'une survie classique,
enrichie de systèmes de progression : guildes, métiers, quêtes, donjons, exploits et
une économie joueur suivie de bout en bout.

Le réseau est réparti sur plusieurs instances (Spawn, Minage, Habitable, Donjon, Nether,
End) reliées par une proxy Velocity. Les données suivent le joueur partout : groupes,
guildes, positions, quêtes et économie sont synchronisés entre les instances.

## Architecture

```
                       ┌─────────────┐
                       │   Velocity  │  proxy réseau
                       └──────┬──────┘
                              │
   ┌────────┬────────┬────────┼────────┬────────┬────────┐
 Spawn   Minage  Habitable  Donjon   Nether    End      …     backends Paper 1.21.8
   └────────┴────────┴────────┼────────┴────────┴────────┘
                              │
                  ┌───────────┴───────────┐
                  │  MariaDB  ·   Redis   │  état partagé + messagerie
                  └───────────────────────┘
```

**Stack** : Paper 1.21.8 · Velocity · Java 21 · Kotlin · Maven · MariaDB (HikariCP) · Redis (Jedis)

## Les plugins maison

Tout ce qui suit est développé en interne pour Vaelor. Les dépôts sont privés :
les liens ne sont accessibles qu'aux membres de l'organisation.

### Progression & RPG
| Plugin | Rôle |
|---|---|
| [VaelorGuildes](https://github.com/Vaelor-MC/VaelorGuildes) | Guildes : rangs, niveaux, banque, chat, quêtes, raids, alliances |
| [VaelorQuests](https://github.com/Vaelor-MC/VaelorQuests) | Quêtes PNJ multi-serveur |
| [VaelorDailyQuests](https://github.com/Vaelor-MC/VaelorDailyQuests) | Quêtes journalières |
| [VaelorExploits](https://github.com/Vaelor-MC/VaelorExploits) | Exploits multi-instances, paliers et récompenses |
| [VaelorEmploi](https://github.com/Vaelor-MC/VaelorEmploi) | Métiers |
| [VaelorJobsPapi](https://github.com/Vaelor-MC/VaelorJobsPapi) | Placeholders JobsReborn, niveaux archivés inclus |
| [VaelorEnchantLimit](https://github.com/Vaelor-MC/VaelorEnchantLimit) | Plafond d'enchantements par objet et par groupe |

### Économie & commerce
| Plugin | Rôle |
|---|---|
| [aureus](https://github.com/Vaelor-MC/aureus) | Traçabilité économique et analytics multi-serveur |
| [VaelorPlayerShop](https://github.com/Vaelor-MC/VaelorPlayerShop) | Shops de coffre, recherche et notifications inter-serveurs |
| [QuickShop-CrossServer](https://github.com/Vaelor-MC/QuickShop-CrossServer) | `/qs finditem` à l'échelle du réseau |
| [QuickShop-Lands-Addon](https://github.com/Vaelor-MC/QuickShop-Lands-Addon) | Intégration Lands pour QuickShop-Hikari |

### Social & communication
| Plugin | Rôle |
|---|---|
| [VaelorParty](https://github.com/Vaelor-MC/VaelorParty) | Groupes cross-serveur, sans dépendance externe |
| [VaelorVoteParty](https://github.com/Vaelor-MC/VaelorVoteParty) | Compteur de votes et récompenses réseau |
| [VaelorPub](https://github.com/Vaelor-MC/VaelorPub) · [VaelorPubEco](https://github.com/Vaelor-MC/VaelorPubEco) | Publicités joueurs `/pub` : filtres, mute, facturation |
| [BroadcastMessagePaper](https://github.com/Vaelor-MC/BroadcastMessagePaper) · [BroadcastMessageVelocity](https://github.com/Vaelor-MC/BroadcastMessageVelocity) | Annonces réseau depuis un backend |

### Déplacement & monde
| Plugin | Rôle |
|---|---|
| [VaelorBack](https://github.com/Vaelor-MC/VaelorBack) | `/back` multi-instances |
| [VaelorRTP](https://github.com/Vaelor-MC/VaelorRTP) | Téléportation aléatoire |
| [VaelorPortal](https://github.com/Vaelor-MC/VaelorPortal) · [VaelorPortalVelocity](https://github.com/Vaelor-MC/VaelorPortalVelocity) | Portails d'entrée de donjons |
| [WarpAddon](https://github.com/Vaelor-MC/WarpAddon) | Interface de warps pour HuskHomes |
| [VaelorTrees](https://github.com/Vaelor-MC/VaelorTrees) | Arbres du pack Iris en génération vanilla |
| [VaelorPeche](https://github.com/Vaelor-MC/VaelorPeche) | Records globaux de pêche |

### Infrastructure
| Plugin | Rôle |
|---|---|
| [RestartCountdown](https://github.com/Vaelor-MC/RestartCountdown) | Redémarrages annoncés, transfert Velocity |
| [VaelorAfkDisconnect](https://github.com/Vaelor-MC/VaelorAfkDisconnect) | Déconnexion réseau des joueurs inactifs |
| [VaelorFallBack](https://github.com/Vaelor-MC/VaelorFallBack) | Repli automatique en cas d'instance indisponible |
| [VaelorMenuHider](https://github.com/Vaelor-MC/VaelorMenuHider) | Masquage d'entrées de menu |

## Écosystème externe

Vaelor s'appuie aussi sur : MythicMobs · MythicDungeons · MMOCore · Jobs Reborn ·
Lands · QuickShop-Hikari · CustomFishing · Nexo · Iris · HuskHomes · Vault · PlaceholderAPI

---

<p align="center">
  <sub>Rejoignez-nous sur <code>play.vaelor.net</code> · <a href="https://vaelor.net/">vaelor.net</a> · <a href="https://discord.gg/hd4ZUTdEVs">Discord</a></sub>
</p>
