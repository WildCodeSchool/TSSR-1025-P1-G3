![logo de la Wild Code SChool en exemple](Ressources/logo_WCS.jpg)

  


# 📜 Introduction

- **Imaginez une DSI** (Direction des Systèmes d'Information) où les **mots de passe critiques** de l'infrastructure ceux qui ouvrent les portes des serveurs de production, des routeurs ou des bases de données sont stockés dans un simple fichier texte partagé ou, pire, dans un tableur non chiffré sur un lecteur réseau.

- **Une simple erreur humaine, la compromission d'un poste, ou une faille de permission** suffisent à exposer l'ensemble de l'entreprise à une paralysie opérationnelle ou à un vol de données massif. Ce scénario, malheureusement trop courant, représente le **risque numéro un** en matière de sécurité informatique.

# 🎯 Présentation du projet

### Gestion de BDD sécurisées de mots de passe

### Présentation du projet

Ce projet s'inscrit dans le cadre de la sécurisation des mots de passe au sein d'une infrastructure informatique. L'objectif principal consiste à déployer deux bases de données (BDD) chiffrées hébergées sur des serveurs distincts : la première "DSI_T0" sur un serveur Windows et la seconde "DSI_T1" sur un serveur Linux. Ces bases de données, accessibles depuis les postes clients, utilisent le logiciel KeePass pour permettre une gestion centralisée et sécurisée des identifiants. Chaque BDD est protégée par une signature de chiffrement différente, et les clés de chiffrement sont sauvegardées sur le serveur correspondant. Le projet inclut également la mise en place d'une sauvegarde automatique avec synchronisation des fichiers entre les serveurs, accompagnée d'une vérification et d'une journalisation automatiques pour garantir l'intégrité des données.

---

### Chapitre 1 : Qu'est-ce que KeePass ?

KeePass est un gestionnaire de mots de passe open source et gratuit qui permet de stocker l'ensemble de ses identifiants dans une base de données chiffrée. Il utilise des algorithmes de chiffrement robustes comme AES-256 pour protéger les informations sensibles. L'accès à la base se fait via un mot de passe maître, et éventuellement un fichier clé pour renforcer la sécurité. KeePass génère également des mots de passe complexes et aléatoires, ce qui évite la réutilisation de mots de passe faibles.

**Lien externe :** https://keepass.info/help/base/firststeps.html

---

### Chapitre 2 : Pourquoi KeePass ?

Le choix de KeePass pour ce projet repose sur plusieurs critères essentiels. D'abord, c'est une solution gratuite et open source, ce qui permet une maîtrise totale de l'outil sans coûts de licence. Ensuite, KeePass fonctionne aussi bien sur Windows que Linux, ce qui correspond parfaitement à notre architecture avec deux serveurs différents. La possibilité de stocker les bases de données sur des serveurs permet une centralisation, et la compatibilité avec la synchronisation garantit la cohérence des données entre les deux environnements.



# 👥 Membres du groupe par sprint

| Membre  | Rôle       | Missions                                                                                                                                                                                      |
| ------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Eros    | PO         | Mise en place d'une base de données sécurisée (DSI_T1) avec un utilisateur dédié, intégrant une nouvelle signature de chiffrement dont la clé est sauvegardée sur un serveur Linux chiffré.   |
| Nicolas | Technicien | Installer KeePass sur un client Windows et Linux et en comprendre le fonctionnement, mise en réseaux des VM.                                                                                  |
| Georges | SM         | Mise en place d'une base de données sécurisée (DSI_T0) avec un utilisateur dédié, intégrant une nouvelle signature de chiffrement dont la clé est sauvegardée sur un serveur Windows chiffré. |

# ⚙️ Choix Techniques

### Serveur Windows

- **Point clé 1 (Hébergement BDD)** : Installation et configuration du serveur pour héberger le fichier de base de données **KeePass "DSI_T0"** dans un répertoire partagé ou accessible.
    
- **Point clé 2 (Stockage Clé)** : Mise en place d'un emplacement sécurisé sur ce serveur pour sauvegarder la **clé de chiffrement** (signature) spécifique à la BDD DSI_T0.
    
---
### Serveur Linux

- **Point clé 1 (Hébergement BDD)** : Installation et configuration du serveur pour héberger le fichier de base de données **KeePass "DSI_T1"**.
    
- **Point clé 2 (Stockage Clé)** : Définition d'un répertoire sécurisé (permissions strictes) sur ce serveur pour sauvegarder la **clé de chiffrement** (signature) spécifique à la BDD DSI_T1.
    

---
### Postes Clients

- **Point clé 1 (Logiciel)** : Déploiement du logiciel **KeePass** (ou d'un client compatible) sur tous les postes clients nécessitant l'accès aux mots de passe.
    
- **Point clé 2 (Accès BDD)** : Configuration des accès réseau permettant aux clients de se connecter indifféremment aux serveurs Windows (pour DSI_T0) ou Linux (pour DSI_T1).
    
---
### Infrastructure de Synchronisation (Tâche secondaire)

- **Point clé 1 (Automatisation)** : Mise en place d'un **d'un service** configuré via une tâche planifiée (CRON sur Linux, Planificateur de tâches sur Windows) pour synchroniser _automatiquement_ les fichiers BDD entre les deux serveurs.
    
- **Point clé 2 (Vérification et Journalisation)** : Le script de synchronisation doit inclure une étape de **vérification** (ex: checksum) et générer un fichier de **log (journal)** daté pour tracer le succès ou l'échec de chaque opération.

- [🧗Difficultés rencontrées](#difficultes-rencontrees)

- [💡 Solutions trouvées](#solutions-trouvees)

- [🚀 Améliorations possibles](#ameliorations-possibles)

  

