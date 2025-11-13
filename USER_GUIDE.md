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

Possiblité d'intégrer KeePassXC à votre navigateur web pour un remplissage automatique des formulaires de connexion.


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

## 2. **Stockers des fichiers**

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
