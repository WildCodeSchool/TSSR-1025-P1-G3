## Sommaire

1. [Prérequis technique](#prerequis-technique)
2. [Installation sur le serveur](#installation-sur-le-serveur)
3. [Installation sur le client](#installation-sur-le-client)
4. [FAQ](#faq)

# 1. Prérequis techniques
<span id="prerequis-techniques"></span>

# 2. Installation sur le serveur
<span id="installation-sur-le-serveur"></span>
# Guide d'installation KeePass sur Windows Server 2022

## Vue d'ensemble

Ce guide décrit la procédure d'installation et de configuration sécurisée de KeePass Password Safe 2.6 sur Windows Server 2022.

---

## 1. Installation du logiciel

### 1.1 Téléchargement

- Accéder au site officiel : [https://keepass.info/](https://keepass.info/)
- Télécharger la version **2.6**

### 1.2 Configuration de l'installation

- **Chemin d'installation** : `C:\Program Files\KeePass Password Safe 2\KeePass.exe`
- **Type d'installation** : Installation complète

![download.png](Ressources/download.png)

---

## 2. Préparation de l'environnement

### 2.1 Création du dossier de stockage

Créer un dossier `DSI_T0` à la racine du disque C: pour héberger :

- La base de données KeePass (.kdbx)
- Le fichier de clé crypté (.keyx)

```
C:\DSI_T0\
```
![[dir dsi.png]]
---

## 3. Création de la base de données

### 3.1 Initialisation

1. Lancer KeePass depuis le bureau
2. Créer une nouvelle base : **File → New**
3. Prendre connaissance des recommandations de sécurité et de sauvegarde
![[new bdd.png]]
 ![[advert soft.png]]
 
 
 ### 3.2 Enregistrement

Enregistrer la base de données dans le dossier créé précédemment :

```
C:\DSI_T1\DSI_T0.kdbx
```
![[touch filebdd.png]]
---

## 4. Configuration de la sécurité

### 4.1 Master Password

- Définir un mot de passe maître robuste
- **Recommandation** : Utiliser le générateur de mots de passe de KeePass ou un outil tiers spécialisé
- **Pour cet exercice** : Utiliser le mot de passe standard de la session de formation

### 4.2 Double authentification (Key File)

1. Cocher l'option **"Key file/provider"** pour ajouter une couche de sécurité supplémentaire
2. Générer le fichier de clé avec la méthode **"Random mouse input"**
3. Le fichier `DSI_T0.keyx` est automatiquement créé dans `C:\DSI_T0\`
![[security hey mdp.png]]
### 4.3 Vérification

Confirmer la présence des fichiers suivants dans `C:\DSI_T0\` :

- `DSI_T0.kdbx` (base de données)
- `DSI_T0.keyx` (fichier de clé)
![[result bdd dir.png]]
---

## 5. Sécurisation avancée du fichier de clé

### 5.1 Objectif

Protéger le fichier de clé contre :

- La perte accidentelle
- Les accès non autorisés
- Le piratage

### 5.2 Création d'un dossier sécurisé

1. Créer un dossier `Keepasskey`
2. Déplacer le fichier `.keyx` dans ce dossier

### 5.3 Configuration des permissions

#### Conversion des autorisations héritées

1. Ouvrir les **Propriétés** du dossier → Onglet **Sécurité**
2. Cliquer sur **Avancé**
3. **Désactiver l'héritage** et convertir les autorisations héritées en permissions explicites
![[erithee.png]]
#### Application des restrictions

Configurer les permissions comme suit :

|Compte|Permissions|
|---|---|
|**SYSTEM**|Contrôle total (Full Control)|
|**Administrators**|Lecture seule (Read)|
|**Autres comptes**|❌ Supprimer tous les accès|

#### Vérification

1. Rouvrir les **Propriétés** du dossier
2. Vérifier que seuls SYSTEM et Administrators apparaissent
3. Confirmer les niveaux d'accès définis
4. Sauvegarder le fichier DSI_T0.keyx dans ce dossier
![[result perm.png]]
---

## 6. Résultat final

La configuration mise en place garantit :

- ✅ Une base de données protégée par mot de passe maître
- ✅ Une double authentification via fichier de clé
- ✅ Des permissions restrictives sur les fichiers sensibles
- ✅ Une séparation physique entre la base et le fichier de clé

---

## Notes importantes

> **⚠️ Sauvegarde** : Mettre en place une stratégie de sauvegarde régulière de la base de données et du fichier de clé sur un support externe sécurisé.

> **⚠️ Documentation** : Conserver le mot de passe maître dans un lieu sûr (coffre-fort physique, gestionnaire de secrets d'entreprise).

> **⚠️ Accès** : Sans le mot de passe maître ET le fichier de clé, l'accès à la base de données est impossible.

---

**Version** : 1.0  
**Date** : Novembre 2024  
**Logiciel** : KeePass Password Safe 2.6  
**Système** : Windows Server 2022







































# 3. Installation sur le client
<span id="installation-sur-le-client"></span>

# 4. FAQ
<span id="faq"></span>
