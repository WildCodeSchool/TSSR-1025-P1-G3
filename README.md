![logo_de_keepass](Ressources/keepasxc.png)

## Sommaire 

- [📜 Introduction](#-introduction)
- [🎯 Présentation du projet](#-présentation-du-projet)
    - [Pourquoi Kesspass?](#pourquoi-kesspass)
- [👥 Membres du groupe par sprint](#-membres-du-groupe-par-sprint)
- [⚙️ Choix techniques](#️-choix-techniques)
- [🧗 Difficultés rencontrées et](#-difficultés-rencontrées-et)
- [💡 Solutions trouvées](#-solutions-trouvées)
- [🚀 Améliorations possibles](#-améliorations-possibles)

# 📜 Introduction

<span id="introduction"></span>
Vous faites partie de ces organisations où la sécurité des mots de passe est une priorité absolue ? Ce projet est conçu pour vous . L’objectif est de mettre en place une solution robuste et centralisée  pour stocker et gérer les mots de passe, en utilisant Keepass, un logiciel open source reconnu pour sa fiabilité et sa simplicité d’utilisation.
# 🎯 Présentation du projet
<span id="presentation-du-projet"></span>
Ce projet a pour objectif de sécuriser et centraliser la gestion des mots de passe au sein d’une infrastructure informatique, en utilisant le logiciel Keepass. L’enjeu est de permettre à plusieurs utilisateurs d’accéder de manière sécurisée à des bases de données chiffrées, hébergées sur des serveurs Windows et Linux, tout en garantissant la confidentialité et l’intégrité des données.

Le projet se concentre sur :
- Deux bases de données KeePass hébergées sur des serveurs dédiés :

    - Une base **DSI_T0** hébergée sur un serveur Windows Server
    - Une base **DSI_T1** hébergée sur un serveur Linux Debian

- Chaque base est protégée par un chiffrement unique avec sa propre clé
- Les clés de chiffrement sont stockées de manière sécurisée sur leurs serveurs respectifs
- Les postes clients sont équipés du logiciel KeePassXC permettant l'accès distant aux bases

**Objectifs finaux**

- Garantir un stockage sécurisé et chiffré des mots de passe .
- Permettre aux utilisateurs d'accéder aux bases de données depuis leurs postes clients
- Assurer la disponibilité des données sur des infrastructures Windows et Linux
### Pourquoi Kesspass?

Le choix de KeePassXC s'est imposé pour sa gratuité, sa compatibilité cross-platform, et son niveau de sécurité élevé. L'utilisation combinée de WinSCP et SSHFS permet aux utilisateurs Windows d'accéder facilement aux bases stockées sur le serveur Linux sans manipulation complexe.

> Pour plus d'informations: [Keepassxc](https://keepassxc.org/docs/KeePassXC_GettingStarted)

>Pour plus d'informations: [WINSCP](https://winscp.net/eng/docs/start)

> Pour plus d'informations: [SSHFS_WIN](https://github.com/winfsp/sshfs-win)

> Pour plus d'informations: [SSHFS_UBUNTU](https://help.ubuntu.com/community/SSHFS)


# 👥 Membres du groupe par sprint
<span id="membres-du-groupe-par-sprint"></span>
**Sprint 1**

| Membre      | Rôle       | Missions                                                                                                          |
| ----------- | ---------- | ----------------------------------------------------------------------------------------------------------------- |
| EROS-NATHAN | PO         | Installer KeePass, configurer la base de données et la chiffrer sur le serveur Debian, commencer la documentation |
| GEORGES      | SM         | Installer KeePass, configurer la base de données et la chiffrer sous Windows Server, commencer la documentation   |
| NICOLAS     | Technicien | Installer KeePass sur les deux machines clientes et commencer la documentation                                    |

**Sprint 2**

| Membre      | Rôle       | Missions                                                                                                                               |
| ----------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| NICOLAS     | PO         | Accéder aux serveurs Windows et Debian et terminer la documentation                                                                    |
| EROS-NATHAN | SM         | Créer des mots de passe et des utilisateurs sur le serveur Debian, les chiffrer et permettre l’accès des clients à la base de données  |
| GEORGES      | Technicien | Créer des mots de passe et des utilisateurs sur le serveur Windows, les chiffrer et permettre l’accès des clients à la base de données |

# ⚙️ Choix techniques
<span id="choix-techniques"></span>
**Matériel**

| Machine Virtuelle | Système d'Exploitation   | NOM      |
| ----------------- | ------------------------ | -------- |
| VM 1              | Debian 12/13             | SRVLX01  |
| VM 2              | Windows Server 2022/2025 | SRVWIN01 |
| VM 3  ( client)   | Ubuntu 24 LTS            | UBU01    |
| VM 4  (client)    | Windows 10/11            | WIN01    |
- Infrastructure réseau permettant la communication sécurisée entre clients et serveurs

**Logiciel**

serveurs :
- **Windows Server** : hébergement de la base DSI_T0
- **Linux Debian** : hébergement de la base DSI_T1 avec service SSH configuré
- **KeePassXC** : format de base de données choisi pour sa robustesse et son chiffrement AES-256

clients :
- **KeePassXC** : gestionnaire de mots de passe open-source, compatible multi-plateformes, permettant l'ouverture des bases distantes
- **WinSCP** : client SFTP/SCP pour Windows, facilitant le transfert sécurisé de fichiers et l'accès aux serveurs Linux
- **SSHFS** : système de fichiers permettant le montage distant des répertoires via SSH, offrant un accès transparent aux bases hébergées sur Linux

# 🧗 Difficultés rencontrées et 
<span id="difficultes-rencontrees"></span>

- Configuration des permissions SSH : Mise en place des droits d'accès appropriés sur le serveur Linux pour permettre l'accès aux fichiers .kdbx tout en maintenant la sécurité
-  Configuration réseau: Ouverture des ports nécessaires (SSH port 22) et configuration des pare-feu

# 💡 Solutions trouvées
<span id="solutions-trouvees"></span>
- Documentation d'une procédure de montage SSHFS standardisée pour faciliter l'installation sur les nouveaux postes clients

# 🚀 Améliorations possibles
<span id="ameliorations-possibles"></span>

- Documentation utilisateur : Créer des guides d'utilisation illustrés pour les utilisateurs finaux
- Automatiser le déploiement des bases de données et des clés SSH via des scripts
- Mettre en place des sauvegardes automatiques
