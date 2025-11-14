## Sommaire

1. [Utilisation de base](#utilisation-de-base)
2. [Utilisation avancée](#utilisation-avancee)
3. [FAQ](#faq)

# 🔑 Guide Utilisateur de Base KeePass
<span id="utilisation-de-base"></span>

## 1. Création de la base de données

1. Cliquez sur **Fichier** $\rightarrow$ **Nouveau...**

2. Choisissez un emplacement sécurisé sur votre disque dur et renommez le.

3. Saisissez un **Mot de Passe**, le plus long possible mais qui soit facile à retrouver pour vous.

4. Renommez votre base de données.

5. Cliquez sur **OK** pour enregistrer et ouvrir votre nouvelle base de données.

## 2. Ajout de nom d'utilisateurs avec leurs mots de passe

1. Cliquez sur l'icône **Ajouter une nouvelle entrée** (souvent une clé ou un $+$ vert).

2. Remplissez les champs :

    * **Titre** : Nom du site

    * **Nom d'utilisateur** : Votre identifiant pour ce site

    * **Mot de passe** : Votre mot de passe pour ce site

    * **URL** : L'adresse web du site

3. Cliquez sur l'icône du **Générateur de mots de passe**

4. Cliquez sur **OK** pour valider la nouvelle entrée.

## 3. Connexion à un site web

1.  Faites un **clic droit** sur l'entrée désirée.

2.  Choisissez **Copier le nom d'utilisateur** et collez-le dans le formulaire du site.

3.  Faites un clic droit $\rightarrow$ **Copier le mot de passe** et collez-le.
 

## 4. Verrouillage de la base de données

1. Quand vous n'utilisez plus la base de données :
    * Cliquez sur l'icône du **cadenas** : la base est verrouillée et nécessite votre Mot de Passe pour la rouvrir.

    * Ou **Quittez** complètement le logiciel.

# 🛡️ Guide Utilisateur Avancé KeePass
<span id="utilisation-avancee"></span>

## 1. **Intégration au Navigateur**

Possibilité d'intégrer KeePassXC à votre navigateur web pour un remplissage automatique des formulaires de connexion.


1. **Installation des Composants**
 
   - Dans KeePassXC, allez dans **Outils** → **Paramètres** → **Intégration du navigateur**.
    
   - **Cochez** "Activer l'intégration du navigateur KeePassXC" et activez le support     

     pour votre navigateur (Chrome, Firefox, etc.).

   - Téléchargez l'extension KeePassXC-Browser depuis votre navigateur et installez la.

3. **Couplage de la Base de Données**

   - Cliquez sur l'icône de l'extension KeePassXC dans votre navigateur.

   - Entrez un nom de connexion.

   - Une fenêtre pop-up de KeePassXC apparaît. Cliquez sur **Enregistrer et Accéder** 
    
     pour autoriser l'extension à communiquer avec votre base de données ouverte.

## 2. **Stocker des fichiers**

Peut également stocker des fichiers (documents, images, etc.) dans les entrées de votre base de 

données.   
 
   - Dans l'édition d'une entrée, allez dans l'onglet **Avancé**.   
   
   - Cliquez sur **Ajouter** sous la section Pièces jointes.

1. **Vérification de la Robustesse des Mots de Passe**

     Vous avez la possibilité d'auditer votre base de données pour identifier les mots de passe 
     
     faibles, réutilisés ou manquants.

   - Allez dans Base de données → Rapport de la base de données.

   - Le rapport vous montrera :

        - Les mots de passe utilisés plusieurs fois.

        - Les mots de passe faibles (selon une complexité configurable).

        - Les entrées sans URL.

# Guide d'utilisation de KeePassXC sous Windows 11

## Prérequis

Ce guide suppose que KeePassXC est déjà installé et configuré sur votre système Windows 11.

---

## Ouverture de votre base de données

### Étape 1 : Lancer l'application

Démarrez KeePassXC depuis la barre des tâches Windows 11 ou via le menu Démarrer.

![W1](Ressources/W1.png)




_Figure 1 : Icône KeePassXC dans la barre des tâches Windows 11 (icône verte avec une clé)_

**Méthodes de lancement :**

- Cliquez sur l'icône KeePassXC dans la barre des tâches
- Menu Démarrer → Recherchez "KeePassXC"
- Raccourci sur le bureau (si créé lors de l'installation)

---

### Étape 2 : Ouvrir une base de données existante

Dans la fenêtre principale de KeePassXC, cliquez sur le menu **"Base de données"** puis sélectionnez **"Ouvrir une base de données..."**

![W2](Ressources/W2.png)




_Figure 2 : Menu "Base de données" avec l'option "Ouvrir une base de données" (Ctrl+O)_

**Méthodes alternatives :**

- Raccourci clavier : `Ctrl + O`
- Menu : **Base de données → Ouvrir une base de données...**
- Lien direct : **"Je dispose d'un fichier clé"** (si affiché dans la fenêtre d'accueil)

---

### Étape 3 : Sélectionner votre base de données

L'explorateur de fichiers Windows s'ouvre. Naviguez jusqu'à l'emplacement de votre fichier de base de données (extension `.kdbx`).

![W3](Ressources/W3.png)



_Figure 3 : Explorateur Windows avec le fichier DSI_T0.kdbx à sélectionner_

**Navigation dans l'explorateur :**

1. Utilisez l'arborescence de gauche pour naviguer vers votre dossier (exemple : `Réseau > srvwin01 > dsi_t0`)
2. Sélectionnez le fichier `.kdbx` dans la zone centrale
    - Dans l'exemple : `DSI_T0` (Type : KeePass Password...)
    - Modifié le : 13/11/2025 19:35
3. Vérifiez que le filtre affiche **"Base de données KeePass 2 (*.kdbx)"**
4. Cliquez sur le bouton **"Ouvrir"**

> **💡 Astuce** : Vous pouvez épingler votre dossier de bases de données dans "Accès rapide" pour un accès facilité.

---

### Étape 4 : Sélectionner le fichier clé (double authentification)

Si votre base de données utilise la double authentification, une nouvelle fenêtre s'ouvre pour sélectionner votre fichier clé.

![W5](Ressources/W5.png)



_Figure 4 : Explorateur Windows avec le fichier clé DSI_T0.keyx_

**À cette étape :**

1. Naviguez vers le dossier contenant votre fichier clé (souvent le même que la base)
2. Sélectionnez le fichier avec l'extension `.key` ou `.keyx`
    - Dans l'exemple : `DSI_T0.keyx` (Type : Fichier KEYX)
    - Modifié le : 13/11/2025 19:34
3. Vérifiez que le filtre affiche **"Tous les fichiers"** ou le type approprié
4. Cliquez sur **"Ouvrir"**

> **⚠️ Important** : Le fichier clé doit être EXACTEMENT celui utilisé lors de la création de la base. Une différence d'un seul octet rendra la base inaccessible.

---

### Étape 5 : Authentification (saisie du mot de passe)

Après avoir sélectionné le fichier clé, vous devez entrer votre mot de passe principal pour déverrouiller la base de données.

![W4](Ressources/W4.png)



_Figure 5 : Fenêtre de déverrouillage avec double authentification_

**Procédure d'authentification complète :**

**① Sélectionner le fichier clé** (partie inférieure)

- Le champ **"Sélectionner le fichier clé :"** affiche le chemin du fichier (masqué pour la sécurité)
- Si nécessaire, cliquez sur **"Parcourir..."** pour changer le fichier clé

**② Saisir le mot de passe** (partie supérieure)

- Entrez votre mot de passe principal dans le champ **"Saisissez le mot de passe :"**
- Le mot de passe est masqué par des points noirs pour la sécurité
- Cliquez sur l'icône 👁️ pour afficher temporairement le mot de passe (si nécessaire)

**③ Déverrouiller** (bouton en bas à droite)

- Cliquez sur le bouton vert **"Déverrouiller"** pour ouvrir votre base
- Ou appuyez sur `Entrée` après avoir saisi le mot de passe

**Ordre des étapes :** L'ordre recommandé est : ① Fichier clé → ② Mot de passe → ③ Déverrouiller

> **🔒 Sécurité renforcée** : La combinaison mot de passe + fichier clé offre une protection maximale. Sans ces DEUX éléments, vos données restent inaccessibles, même en cas de vol de votre ordinateur.

---

### Étape 6 : Accès à votre base de données

Une fois l'authentification réussie, vous accédez à l'interface principale de KeePassXC avec toutes vos entrées sécurisées.

![W6](Ressources/W6.png)



_Figure 6 : Interface principale avec la base de données DSI_T0 déverrouillée_


# Guide d'utilisation de KeePassXC sous Ubuntu

## Prérequis

Ce guide suppose que KeePassXC est déjà installé et configuré sur votre système Ubuntu.

---

## Ouverture de votre base de données

### Étape 1 : Lancer l'application

Démarrez KeePassXC depuis votre menu d'applications Ubuntu ou via la ligne de commande :

```bash
keepassxc
```

![U1](Ressources/U1.png)




_Figure 1 : Icône KeePassXC dans le dock Ubuntu (icône verte avec une clé)_

---

### Étape 2 : Ouvrir une base de données existante

Dans la fenêtre principale de KeePassXC, cliquez sur le menu **"Base de données"** puis sélectionnez **"Ouvrir une base de données..."**

![U2](Ressources/U2.png)




_Figure 2 : Menu "Base de données" avec l'option "Ouvrir une base de données" (Ctrl+O)_

**Méthodes alternatives :**

- Raccourci clavier : `Ctrl + O`
- Menu : **Base de données → Ouvrir une base de données...**

---

### Étape 3 : Sélectionner votre base de données

Dans la boîte de dialogue qui s'ouvre, naviguez dans vos dossiers pour localiser votre fichier de base de données (extension `.kdbx`).

![U3](Ressources/U3.png)




_Figure 3 : Fenêtre de sélection avec le fichier DSI_T0.kdbx à choisir_

**Points importants :**

- Les bases de données KeePassXC ont l'extension `.kdbx`
- Dans l'exemple : le fichier `DSI_T0.kdbx` (2,2 Ko) est identifié comme "KeePass 2 database"
- Sélectionnez votre fichier puis cliquez sur **"Choisir"** ou **"Ouvrir"**

---

### Étape 4 : Sélectionner le fichier clé (double authentification)

Si votre base de données utilise la double authentification, vous devrez d'abord sélectionner votre fichier clé.

![U5](Ressources/U5.png)




_Figure 4 : Fenêtre de sélection du fichier clé (DSI_T0.keyx dans cet exemple)_

**À cette étape :**

- Vous voyez le fichier `.keyx` ou `.key` dans votre dossier
- Dans l'exemple : `DSI_T0.keyx` (240 octets)
- Sélectionnez votre fichier clé puis cliquez sur **"Choisir"**

---

### Étape 5 : Authentification (saisie du mot de passe)

Après avoir sélectionné le fichier clé, vous devez entrer votre mot de passe principal pour déverrouiller la base de données.

![U4](Ressources/U4.png)




_Figure 5 : Fenêtre de déverrouillage avec les trois éléments requis_

**Procédure d'authentification :**

1. **① Sélectionner le fichier clé** : Cliquez sur le bouton **"Parcourir..."** pour choisir votre fichier `.key` ou `.keyx`
    
    - Le chemin du fichier clé apparaît dans le champ (masqué par des points pour la sécurité)
2. **② Saisir le mot de passe** : Entrez votre mot de passe principal dans le champ **"Saisissez le mot de passe :"**
    
    - Le mot de passe est masqué pour la sécurité
    - Attention aux majuscules/minuscules
3. **③ Déverrouiller** : Cliquez sur le bouton vert **"Déverrouiller"** pour ouvrir votre base
    

> **⚠️ Note de sécurité** : La double authentification (mot de passe + fichier clé) renforce considérablement la sécurité de votre base de données. Sans ces DEUX éléments, impossible d'accéder à vos données. Conservez votre fichier clé dans un emplacement sécurisé et distinct de votre base de données.

---

### Étape 6 : Accès à votre base de données

Une fois authentifié avec succès, vous accédez à l'interface principale de KeePassXC avec toutes vos entrées.

![U6](Ressources/U6.png)




_Figure 6 : Interface principale avec la base de données déverrouillée_

**Éléments de l'interface :**

**Panneau gauche - Arborescence des groupes :**

- 📁 DSI_T0 (dossier racine)
    - General
    - Windows
    - Network
    - Internet
    - eMail
    - Homebanking
    - Recycle Bin (corbeille)

**Section "Recherches et Étiquettes" :**

- 🔍 Effacer la recherche
- 📋 Toutes les entrées
- ⏰ Expirés
- 🔑 Mots de passe faibles

**Panneau central - Liste des entrées :**

- Affiche les entrées du groupe sélectionné
- Colonnes : Titre, Nom d'utilisateur, URL, Notes, Modifiée
- Exemple visible : entrée "Sample..." avec "User Name"

**Panneau inférieur - Détails de l'entrée :**

- Onglets : Général, Avancé, Saisie automatique
- Informations détaillées : Nom d'utilisateur, Mot de passe (masqué), URL, Expiration, Étiquettes, Notes






# 3. FAQ
<span id="faq"></span>
Cette FAQ répond aux questions courantes sur l'utilisation de KeePass sur Windows 11 et Linux Ubuntu. On se concentre sur l'essentiel pour une prise en main facile.

## Sur Windows 11

**Q1 : Comment créer une nouvelle base de données de mots de passe ?**  
Ouvrez KeePass, allez dans Fichier > Nouveau. Choisissez un mot de passe maître fort et enregistrez le fichier .kdbx dans un endroit sécurisé.

**Q2 : Comment utiliser l'auto-saisie pour remplir les formulaires ?**  
Sélectionnez une entrée, appuyez sur Ctrl+V ou configurez une séquence d'auto-saisie personnalisée dans les propriétés de l'entrée. Ça marche bien avec les navigateurs.

**Q3 : Que faire si j'oublie mon mot de passe maître ?**  
Malheureusement, il n'y a pas de récupération. Utilisez un fichier clé en plus du mot de passe pour plus de sécurité, et sauvegardez régulièrement.

## Sur Linux Ubuntu

**Q1 : Comment ouvrir une base de données existante ?**  
Lancez KeePass via le menu ou terminal (`keepass2`), allez dans Fichier > Ouvrir, et entrez votre mot de passe maître.

**Q2 : L'auto-saisie fonctionne-t-elle avec les apps Linux ?**  
Oui, mais installez `xdotool` si besoin (`sudo apt install xdotool`). Configurez la séquence dans les options de l'entrée pour simuler les touches.

**Q3 : Comment synchroniser ma base de données entre appareils ?**  
Utilisez un cloud comme Dropbox ou un dossier partagé. Ouvrez le fichier .kdbx depuis n'importe où, mais assurez-vous d'une bonne encryption.
