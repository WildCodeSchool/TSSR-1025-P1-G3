## Sommaire
1. [Utilisation de base](#utilisation-de-base)
2. [Utilisation avancée](#utilisation-avancee)
3. [FAQ](#faq)

### # Guide d’utilisation

Ce guide vous accompagnera de l'installation à la maîtrise de KeePass sur **Windows 11** et **Ubuntu**. Vous apprendrez à :

1. Installer et configurer KeePass sur les deux systèmes
2. Créer et organiser votre base de données sécurisée
3. Utiliser les fonctionnalités avancées (plugins, synchronisation, auto-type)
4. Résoudre les problèmes courants


# 1. Utilisation de base
<span id="utilisation-de-base"></span>

## Chapitre 1 : Prise en Main et Utilisation de Base


### 1.1. Installation de KeePass

#### Sous Windows 11

1. **Téléchargement** : Rendez-vous sur le site officiel keepass.info et accédez à la section **Downloads**.
    
2. **Choisir la version** : Deux options s'offrent à vous :
    
    - **L'installeur classique (.exe)** : Recommandé pour la plupart des utilisateurs. Il installe KeePass dans `C:\Program Files\KeePass Password Safe 2\` et crée des raccourcis.
    - **La version portable (.zip)** : Ne nécessite pas d'installation. Idéale pour une clé USB ou si vous n'avez pas les droits administrateur.
3. **Étapes d'installation avec l'installeur** :
    
    - Exécutez le fichier `KeePass-2.xx-Setup.exe` téléchargé
    - Acceptez la licence (G
    - Choisissez le dossier d'installation (laisser par défaut est recommandé)
    - Sélectionnez les options (raccourci bureau, menu démarrer)
    - Cliquez sur **Install** puis **Finish**


#### Sous Ubuntu
    
1. **Ouvrez un terminal** 
    

```bash
sudo apt update
sudo apt install keepass2
```

2. **Lancement** : Une fois installé, KeePass apparaît dans votre menu d'applications sous le nom **KeePass2**.
    

---

### 1.2. Créer votre première base de données (KDBX)

#### Qu'est-ce qu'une base de données KeePass ?

La base de données (fichier avec l'extension **.kdbx**) est votre **coffre-fort numérique**. Elle contient toutes vos entrées (identifiants, mots de passe, notes) dans un format **fortement chiffré** (AES-256).

#### Processus de création

1. Lancez KeePass
2. Allez dans **Fichier > Nouvelle Base de données** (ou File > New)
3. Choisissez l'emplacement et le nom de votre fichier (ex: `MesMotsDePasse.kdbx`)
4. Cliquez sur **Enregistrer**

#### L'étape cruciale : Le Mot de Passe Maître

**Le Mot de Passe Maître** est la **clé unique** qui déverrouille votre coffre-fort. 

**Caractéristiques d'un bon Mot de Passe Maître** :

- **Long** : Minimum 15-20 caractères
- **Complexe** : Mélange de majuscules, minuscules, chiffres et symboles
- **Mémorable** : Utilisez une phrase secrète personnelle 
- **Unique** : Ne le réutilisez jamais ailleurs

**Options supplémentaires de sécurité** :

1. **Fichier Clé (optionnel)** :
    
    - Un fichier physique servant de "seconde clé"
    - **Avantage** : Sécurité renforcée (même avec le mot de passe, impossible d'ouvrir sans le fichier)
    - **Inconvénient** : Si vous perdez ce fichier, vos données sont irrécupérables
    - Cochez **"Key file / provider"** et créez ou sélectionnez un fichier
2. **Compte utilisateur Windows** (Windows uniquement) :
    
    - Lie la base de données à votre compte Windows
    - **À déconseiller** : Nuit à la portabilité (impossible d'ouvrir sur un autre PC ou OS)

#### Configuration de la base de données

Après avoir défini votre Mot de Passe Maître, configurez les paramètres :

- **Nom de la base** : Un nom descriptif (ex: "Mes identifiants personnels")
- **Description** : Optionnelle, pour vos notes
- **Paramètres de chiffrement** : Laissez les valeurs par défaut (AES-256, 60 000 itérations)

Cliquez sur **OK** pour créer votre base de données.

#### L'importance de sauvegarder

⚠️ **CRITIQUE** : Votre fichier `.kdbx` (et le fichier clé si utilisé) sont précieux :

- **Sauvegardez-les régulièrement** sur un support externe (clé USB, disque dur)
- Conservez une copie dans un lieu sûr (coffre-fort physique)
- Sans ces fichiers ET votre Mot de Passe Maître, vos données sont **définitivement perdues**

---

### 1.3. Interface et Organisation

#### Description de l'interface principale

L'interface de KeePass est identique sur Windows 11 et Ubuntu. Elle se compose de trois zones principales :

- **Panneau de gauche** : Arborescence des **groupes** (dossiers)
- **Panneau central** : Liste des **entrées** du groupe sélectionné
- **Panneau inférieur** : Détails de l'entrée sélectionnée

#### Le système de "Groupes"

Les **groupes** fonctionnent comme des dossiers pour organiser vos entrées :

- **Groupes par défaut** : General, Windows, Network, Internet, eMail, Homebanking
- **Créer un groupe** : Clic droit sur la racine > **Add Group**
- **Sous-groupes** : Possibilité de créer une hiérarchie (ex: Banque > Compte Courant)

**Exemples d'organisation** :

- Par catégorie : Réseaux sociaux, Banques, E-commerce, Travail
- Par importance : Critique, Important, Secondaire
- Par usage : Personnel, Professionnel, Familial

#### La Corbeille

Comme un système d'exploitation, KeePass possède une **Corbeille** (Recycle Bin) :

- Les entrées supprimées y sont déplacées temporairement
- Permet de récupérer une entrée supprimée par erreur
- Videz-la régulièrement : Clic droit > **Empty Recycle Bin**

---

### 1.4. Gestion des Entrées (Basique)

#### Créer une nouvelle entrée

1. Sélectionnez le groupe de destination
    
2. Clic droit dans le panneau central > **Add Entry** (ou Ctrl+I)
    
3. Remplissez les champs principaux :
    
    - **Title** (Titre) : Nom du service (ex: "Facebook")
    - **User name** (Nom d'utilisateur) : Votre identifiant ou email
    - **Password** (Mot de passe) : Le mot de passe (voir générateur ci-dessous)
    - **Repeat** : Confirmation du mot de passe
    - **URL** : L'adresse du site web 
    - **Notes** : Informations complémentaires
4. Cliquez sur **OK** pour enregistrer
    

#### Le générateur de mot de passe intégré

Pour créer un mot de passe robuste automatiquement :

1. Dans la fenêtre d'édition d'entrée, cliquez sur l'**icône de clé** à droite du champ Password
2. Sélectionnez **Generate Password** (ou l'icône de dés)
3. Le générateur crée instantanément un mot de passe aléatoire
4. Paramètres par défaut : 20 caractères, lettres majuscules/minuscules, chiffres et symboles
5. Cliquez sur **OK** pour l'utiliser

#### Copier/Coller un mot de passe

Pour utiliser un mot de passe stocké :

1. Cliquez droit sur l'entrée concernée
2. Sélectionnez **Copy Password** (Ctrl+C)
3. Le mot de passe est copié dans le presse-papiers 
4. Collez-le dans le champ de connexion (Ctrl+V)
5. Le presse-papiers est automatiquement effacé pour votre sécurité

**Alternative** : Utilisez **Copy User Name** pour copier d'abord l'identifiant.

#### Auto-Type : L'une des fonctionnalités phares

**Auto-Type** est une fonctionnalité puissante qui **simule la frappe au clavier** pour remplir automatiquement vos identifiants.

**Comment ça fonctionne ?**

1. Ouvrez la page de connexion dans votre navigateur
2. Cliquez dans le premier champ (nom d'utilisateur)
3. Appuyez sur le raccourci **Ctrl+Alt+A** (configurable)
4. KeePass identifie la fenêtre active via son titre
5. Si une entrée correspond, il tape automatiquement : `{USERNAME}{TAB}{PASSWORD}{ENTER}`

**Utilisation concrète** :

- KeePass cherche une entrée dont le titre ou l'URL correspond à la fenêtre active
- Si plusieurs entrées correspondent, une liste de sélection apparaît
- Séquence par défaut : Nom d'utilisateur → Tabulation → Mot de passe → Entrée

**Avantages** :

- Plus sûr que le copier-coller (pas de trace dans le presse-papiers)
- Rapide et efficace
- Fonctionne dans les navigateurs et les applications de bureau

---

### 1.5. Verrouiller et Sauvegarder

#### Verrouiller la base de données

Pour protéger vos données lorsque vous quittez votre poste :

**Verrouillage manuel** :

- Menu **Fichier > Lock Workspace** (ou Ctrl+L)
- Icône de cadenas dans la barre d'outils
- L'interface se verrouille, demandant le Mot de Passe Maître pour rouvrir

**Verrouillage automatique** : Configurez le verrouillage automatique dans **Outils > Options > Sécurité** :

- **Lock workspace after inactivity** : Après X secondes d'inactivité
- **Lock workspace when Windows locks** : Quand l'ordinateur se verrouille
- **Lock workspace when minimizing window** : À la minimisation

#### Sauvegarder les modifications

- KeePass sauvegarde **automatiquement** chaque modification dans le fichier `.kdbx`
- L'icône de disquette clignote lors de la sauvegarde
- Vous pouvez forcer une sauvegarde : **Fichier > Save** (Ctrl+S)

**Bonnes pratiques** :

- Créez des sauvegardes régulières du fichier `.kdbx` sur supports externes
- Utilisez la fonction **Fichier > Export** pour créer des copies de secours
- Ne travaillez jamais directement sur votre unique copie

# 2. Utilisation avancée
<span id="utilisation-avancee"></span>
## Chapitre 2 : Fonctionnalités Avancées


### 2.1. Utilisation des Fichiers Clés

#### Qu'est-ce qu'un Fichier Clé ?

Un **Fichier Clé** est un fichier quelconque (image, document, fichier généré) qui sert de **seconde clé** pour déverrouiller votre base de données. C'est une couche de sécurité supplémentaire basée sur le principe : "ce que vous savez (mot de passe) + ce que vous possédez (fichier)".

#### Comment créer un Fichier Clé

**Lors de la création d'une base de données** :

1. Dans la fenêtre **Composite Master Key**, cochez **Key file / provider**
2. Cliquez sur **Create** pour générer un nouveau fichier clé
3. Choisissez l'emplacement et le nom (ex: `ma_cle.keyx`)
4. KeePass génère un fichier cryptographiquement aléatoire

**Alternative** : Utilisez n'importe quel fichier existant (photo, document PDF, etc.)

#### Associer un Fichier Clé à une base existante

1. Ouvrez votre base de données
2. Menu **Fichier > Change Master Key**
3. Cochez **Key file / provider**
4. Cliquez sur le bouton avec trois points et sélectionnez votre fichier
5. Entrez votre Mot de Passe Maître actuel
6. Validez

À partir de maintenant, vous aurez besoin **des deux** pour ouvrir la base.

#### ⚠️ Avertissement critique

- **Ne perdez jamais votre Fichier Clé** : Sans lui, impossible d'accéder à vos données
- **Sauvegardez-le séparément** du fichier `.kdbx` (clé USB distincte, coffre-fort)
- **Ne le stockez pas au même endroit** que votre base de données (annulerait la sécurité)
- Considérez créer **plusieurs copies** stockées en lieux sûrs différents

---

### 2.2. Le Générateur de Mots de Passe (Avancé)

#### Explorer les options avancées

Accédez au générateur complet : **Outils > Generate Password** (ou depuis l'édition d'entrée).

**Paramètres détaillés** :

1. **Length of generated password** (Longueur) :
    
    - Ajustez entre 1 et 9999 caractères
    - Recommandation : 16-32 caractères pour un bon équilibre sécurité/praticité
2. **Character sets** (Jeux de caractères) :
    
    - **Upper-case (A, B, C, ...)** : Lettres majuscules
    - **Lower-case (a, b, c, ...)** : Lettres minuscules
    - **Digits (0, 1, 2, ...)** : Chiffres
    - **Special characters (!, $, %, ...)** : Symboles spéciaux
    - **Minus (-), Underline (_), Space ( ), Brackets ([, ])** : Caractères spécifiques
3. **Advanced options** :
    
    - **Also include the following characters** : Ajoutez des caractères personnalisés
    - **Exclude look-alike characters** : Évite I/l/1, O/0 (recommandé pour saisie manuelle)
    - **Exclude the following characters** : Exclut certains symboles (utile si un site les refuse)
    - **Each character must occur at most once** : Pas de répétition
4. **Pattern** :
    
    - Définissez un modèle personnalisé (ex: `d-dddd-dddd` pour format type 1-2345-6789)
    - Syntaxe : `a` (minuscule), `A` (majuscule), `d` (chiffre), `\` (échappement)

#### Les profils de génération

KeePass permet de **sauvegarder des profils** de génération :

1. Configurez vos paramètres préférés
2. Cliquez sur l'icône de disquette **"Save Profile"**
3. Nommez votre profil (ex: "Banque 16 car", "Site web 24 car")
4. Sélectionnez rapidement vos profils depuis le menu déroulant

**Profils utiles pré-configurés** :

- **40-Bit Hex Key** : Clé hexadécimale
- **128-Bit Hex Key** : Clé de chiffrement
- **MAC Address** : Format adresse MAC

---

### 2.3. Plugins et Intégration

#### Qu'est-ce que le système de plugins ?

KeePass possède une **architecture extensible** permettant d'ajouter des fonctionnalités via des **plugins** (fichiers `.plgx`). Ces extensions offrent :

- Intégration avec les navigateurs web
- Import/export de formats supplémentaires
- Fonctionnalités de synchronisation avancées
- Personnalisation de l'interface

#### Sous Windows 11

**Où trouver les plugins** :

- Site officiel : -keepass.info/plugins.html
- Vérifiez la compatibilité avec KeePass 2.x

**Installation d'un plugin** :

1. Téléchargez le fichier `.plgx` du plugin désiré
2. Localisez le dossier d'installation de KeePass :
    - Installation standard : `C:\Program Files\KeePass Password Safe 2\`
    - Version portable : Votre dossier KeePass
3. Ouvrez le sous-dossier **Plugins** (créez-le s'il n'existe pas)
4. **Copiez** le fichier `.plgx` dans ce dossier
5. Redémarrez KeePass
6. Vérifiez l'installation : **Outils > Plugins**

**Exemple : Plugin d'intégration navigateur**

Pour connecter KeePass à votre navigateur (Chrome, Firefox, Edge) :

- **KeePassRPC** : Plugin côté KeePass
- **Kee** : Extension navigateur associée

**Installation** :

1. Installez le plugin KeePassRPC dans le dossier Plugins
2. Installez l'extension Kee depuis le store de votre navigateur
3. Redémarrez KeePass et le navigateur
4. Configurez la connexion via l'interface de Kee


#### Sous Ubuntu

**Installation de plugins** :

Le processus est similaire, mais l'emplacement du dossier Plugins diffère :

1. Téléchargez le fichier `.plgx`
2. Localisez le dossier Plugins :
    - Chemin utilisateur : `~/.config/KeePass/Plugins/` (créez-le si nécessaire)
    - OU chemin système : `/usr/lib/keepass2/Plugins/`
3. Copiez le fichier `.plgx` via le terminal :

```bash
mkdir -p ~/.config/KeePass/Plugins
cp ~/Téléchargements/MonPlugin.plgx ~/.config/KeePass/Plugins/
```

4. Redémarrez KeePass

**Difficultés potentielles** :

- **Dépendance à Mono** : Certains plugins peuvent mal fonctionner sous Mono
- **Performances** : L'exécution via Mono peut être moins fluide
- **Compatibilité** : Tous les plugins ne sont pas testés sous Linux

**Alternative recommandée : KeePassXC**

Pour une meilleure intégration native sous Linux :

- **KeePassXC** est un fork de KeePass développé en C++
- **Avantages** :
    - Ne nécessite pas Mono
    - Interface moderne et native
    - Intégration navigateur native (KeePassXC-Browser)
    - Meilleure performance sous Linux et macOS
    - Développement actif
- **Compatible** avec le format `.kdbx`
- Installation Ubuntu : `sudo apt install keepassxc`

---

### 2.4. Synchronisation de la Base de Données (Cloud)

#### L'intérêt de la synchronisation

Synchroniser votre base de données KeePass vous permet de :

- **Accéder à vos mots de passe** depuis plusieurs ordinateurs
- **Maintenir vos données à jour** automatiquement
- **Utiliser KeePass** sur PC bureau, PC portable, et mobile simultanément

#### Méthode recommandée : Dossier cloud synchronisé

La méthode la plus simple consiste à **placer votre fichier `.kdbx`** dans un dossier synchronisé par un service cloud :

**Services compatibles** :

- Google Drive
- Dropbox
- OneDrive (Microsoft)
- Nextcloud (open-source, auto-hébergeable)
- Syncthing (peer-to-peer, sans cloud)

#### Configuration (Windows 11 et Ubuntu)

Les étapes sont conceptuellement identiques sur les deux systèmes :

**Étape 1 : Installer le client de synchronisation**

- **Exemple avec Google Drive** :
    
    - Windows : Téléchargez "Google Drive pour ordinateur" depuis drive.google.com
    - Ubuntu : Utilisez une solution comme `rclone` ou `insync`
- **Exemple avec Nextcloud** :
    
    - Téléchargez le client Nextcloud pour votre OS
    - Connectez-vous avec vos identifiants Nextcloud

**Étape 2 : Placer le fichier .kdbx dans le dossier synchronisé**

1. Localisez votre dossier de synchronisation :
    
    - Google Drive : `C:\Users\VotreNom\Google Drive\` (Windows) ou `~/GoogleDrive/` (Ubuntu)
    - Dropbox : `C:\Users\VotreNom\Dropbox\` (Windows) ou `~/Dropbox/` (Ubuntu)
2. **Copiez** (ne déplacez pas immédiatement) votre fichier `.kdbx` dans ce dossier
    
3. Créez un sous-dossier dédié (ex: `KeePass/`) pour plus d'organisation
    

**Étape 3 : Ouvrir le fichier depuis KeePass**

1. Sur chaque appareil, ouvrez KeePass
2. **Fichier > Open > Open File**
3. Naviguez vers le dossier synchronisé
4. Ouvrez le fichier `.kdbx` depuis son nouvel emplacement

**Étape 4 : Utiliser les "Déclencheurs" (Triggers) pour éviter les conflits**

Lorsque plusieurs appareils modifient la même base simultanément, des **conflits de synchronisation** peuvent survenir.

**Solution** : Configurer des déclencheurs pour synchroniser au lieu d'écraser.

**Configuration des Triggers** :

1. Menu **Outils > Triggers**
    
2. Créez un nouveau trigger :
    
    - **Event** : Saved database file
    - **Action** : Synchronize active database with a file/URL
    - **Parameters** : Chemin vers votre fichier `.kdbx` dans le cloud
3. Créez un second trigger :
    
    - **Event** : Opened database file
    - **Action** : Synchronize active database with a file/URL

Cette configuration :

- **Synchronise** au lieu de remplacer
- **Fusionne** les modifications des deux sources
- **Préserve** les changements effectués hors ligne

**[INCLURE CAPTURE D'ÉCRAN : Fenêtre des "Déclencheurs" (Triggers) de KeePass]**

#### Sécurité et bonnes pratiques

✅ **Recommandations** :

- Votre fichier `.kdbx` reste **chiffré** même dans le cloud
- Utilisez un **Mot de Passe Maître très robuste**
- Envisagez un **Fichier Clé** stocké localement (pas dans le cloud)
- Activez l'**authentification à deux facteurs** sur votre compte cloud

⚠️ **Précautions** :

- Ne partagez jamais votre dossier cloud KeePass avec d'autres personnes
- Vérifiez les paramètres de confidentialité de votre service cloud
- Créez des sauvegardes locales régulières (indépendantes du cloud)

---

### 2.5. Champs personnalisés et Historique

#### Ajouter des champs personnalisés

KeePass permet d'ajouter des **champs supplémentaires** à vos entrées pour stocker toute information complémentaire.

**Cas d'usage** :

- Clé de licence logicielle
- Numéro de série
- Question/réponse secrète
- Code PIN
- Numéro de compte bancaire

**Procédure** :

1. Ouvrez une entrée (double-clic ou clic droit > Edit)
    
2. Allez dans l'onglet **Advanced**
    
3. Cliquez sur **Add** dans la section "String fields"
    
4. Définissez :
    
    - **Field name** : Nom de votre champ (ex: "Clé de licence")
    - **Field value** : La valeur (ex: "XXXX-YYYY-ZZZZ-1234")
    - **Enable in-memory protection** : Cochez pour protéger les données sensibles
5. Cliquez sur **OK**
    

Votre champ personnalisé apparaît maintenant dans l'entrée et peut être copié comme un mot de passe.

#### Consulter l'historique d'une entrée

KeePass conserve un **historique complet** de toutes les modifications d'une entrée.

**Utilité** :

- Retrouver un ancien mot de passe
- Restaurer une version précédente
- Auditer les changements

**Accès à l'historique** :

1. Ouvrez l'entrée concernée
2. Allez dans l'onglet **History**
3. Vous voyez la liste des versions précédentes avec date et heure
4. Cliquez sur une version pour voir ses détails
5. Utilisez **Restore** pour revenir à cette version (attention : cette action est elle-même historisée)

**Options** :

- **Delete** : Supprimer une entrée d'historique spécifique
- **Delete All** : Vider tout l'historique (libère de l'espace)

**Configuration** : Dans **Fichier > Database Settings > Advanced**, vous pouvez limiter le nombre de versions conservées.

# 3. FAQ
<span id="faq"></span>
## Chapitre 3 : Foire Aux Questions (FAQ) Essentielles

### Q : J'ai perdu mon Mot de Passe Maître. Comment le récupérer ?

**R :** Malheureusement, **vous ne pouvez pas le récupérer**. C'est le principe fondamental de KeePass et de sa sécurité.

**Pourquoi ?**

- KeePass ne stocke **aucune porte dérobée** ou mécanisme de récupération
- Votre base est chiffrée avec votre Mot de Passe Maître comme clé unique
- Personne, pas même les développeurs, ne peut déverrouiller votre base sans ce mot de passe

**Conséquences** :

- Sans le Mot de Passe Maître (et le Fichier Clé si utilisé), vos données sont **définitivement inaccessibles**
- Il n'existe aucune fonction "Mot de passe oublié ?"

**Solutions préventives** :

- **Mémorisez absolument** votre Mot de Passe Maître (utilisez une phrase secrète personnelle)
- Écrivez-le sur papier et conservez-le dans un **lieu physiquement sûr** (coffre-fort)
- Créez des **sauvegardes régulières** de votre fichier `.kdbx`
- Envisagez un **gestionnaire de mots de passe de secours** pour le Mot de Passe Maître uniquement

---

### Q : KeePass est-il vraiment sécurisé ?

**R : Oui, KeePass est extrêmement sécurisé** pour plusieurs raisons :

**1. Chiffrement robuste** :

- Utilise l'algorithme **AES-256** (Advanced Encryption Standard)
- Norme militaire et bancaire, considéré comme incassable avec la technologie actuelle
- Dérivation de clé avec **100 000+ itérations** (ralentit les attaques par force brute)

**2. Sécurité locale** :

- Vos données restent **sur votre ordinateur**, pas dans le cloud d'une entreprise
- Vous avez le **contrôle total** de votre base de données
- Aucun risque de piratage de serveur distant

**3. Open-source et audité** :

- Le code source est **public et transparent**
- Des experts en sécurité du monde entier peuvent l'**auditer**
- Aucun code malveillant caché
- Développement communautaire depuis 2003