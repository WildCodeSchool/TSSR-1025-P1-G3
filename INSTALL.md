## Sommaire

1. [Prérequis technique](#prerequis-technique)
2. [Installation sur les serveurs](#installation-sur-le-serveur)
3. [Installation sur les clients](#installation-sur-le-client)
4. [FAQ](#faq)

# 1. Prérequis techniques
<span id="prerequis-techniques"></span>
**Étapes 1 :**

  - Crée quatre machines virtuelles :

| Machine Virtuelle | Système d'Exploitation   | NOM      |
| ----------------- | ------------------------ | -------- |
| VM 1              | Debian 12/13             | SRVLX01  |
| VM 2              | Windows Server 2022/2025 | SRVWIN01 |
| VM 3              | Ubuntu 24 LTS            | UBU01    |
| VM 4              | Windows 10/11            | WIN01    |

**Étapes 2 :**

   - Mets les quatre machines  en réseau → rajoute une 2e carte réseau en "réseau interne", avec le même nom "intnet".

   - Configure l'adresse IP de la deuxième carte réseau sur les quatre machines

| VM       | Système d'Exploitation       | Carte_réseau_1 | Carte_réseau_2/Réseau_Interne   | IP           |
| -------- | ---------------------------- | -------------- | ------------------------------- | ------------ |
| SRVLX01  | Debian 12/13 CLI             | NAT            | intnet                          | 172.16.10.6  |
| SRVWIN01 | Windows Server 2022/2025 GUI | NAT            | intnet                          | 172.16.10.5  |
| UBU01    | Ubuntu 24 LTS                | NAT            | intnet                          | 172.16.10.20 |
| WIN01    | Windows 10/11                | NAT            | intnet                          | 172.16.10.10 |

# 2. Installation sur les serveurs
<span id="installation-sur-le-serveur"></span>

## Installation sur le serveur Debian 12/13 (CLI)

## 1. Mise à jour du système avant l’installation de KeePass :

- *Entre cette commande :*

wilder@srvlx01:~$ sudo apt update && sudo apt upgrade -y

![MAJ_paquets](Ressources/mise_a_jour_des_paquets.png)

## 2. Installation de KeePassXC et vérification de la version

- *Entre cette commande :*

 wilder@srvlx01:~$ sudo apt install -y keepassxc && keepassxc-cli --version

![](Ressources/Installer_keepassx_verification_versioncCLI.png)

## 3. Création de l'utilisateur système "keepass_wilder"

- *Entre cette commande :*

wilder@srvlx01:~$ sudo useradd -r -s /usr/sbin/nologin keepass_wilder

## 4. Création du dossier keepass dans /var

- *Entre cette commande :*

wilder@srvlx01:~$ sudo mkdir -p /var/keepass/files

## 5. Donne tous les droits a keepass_wilder pour être propriétaire

- *Entre cette commande :* 

wilder@srvlx01:~$ sudo chown keepass_wilder:keepass_wilder /var/keepass/files

## 6.Donne les droits de lecture, écriture et d'exécution a keepass_wilder

- *Entre cette commande :*

wilder@srvlx01:~$ sudo chmod 700 /var/keepass/files

![](Ressources/Créer_dossier_keepass.png)

## 7. Génération de la clé de chiffrement

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder bash -c 'dd if=/dev/urandom of=/var/keepass/files/dsi_t1.key bs=64 count=1 status=none'

## 8.Donne les droits pour que seule keepass_wilder puisse lire la clé 

- *Entre cette commande :*

wilder@srvlx01:~$ sudo chmod 600 /var/keepass/files/dsi_t1.key

## 9.Donne tous les droits a keepass_wilder pour être propriétaire

- *Entre cette commande :*

wilder@srvlx01:~$ sudo chown keepass_wilder:keepass_wilder /var/keepass/files/dsi_t1.key

![](Ressources/génère_clé-de_chiffrement.png)

## 10.Créer la base KeePass et définit le mot de passe pour Keepass_wilder

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli db-create /var/keepass/files/dsi_t1.kdbx --set-key-file /var/keepass/files/dsi_t1.key --set-password

![](Ressources/Creation_DB.png)

## 11. Vérification des informations de la base de données

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli db-info -k /var/keepass/files/dsi_t1.key /var/keepass/files/dsi_t1.kdbx

La base de données est crée et sécurisée. On peut maintenant créer des comptes et y stocker des informations. Plusieurs solutions s’offrent à nous : soit créer les utilisateurs manuellement, soit utiliser un script pour automatiser cette tâche.


## 12. Création d'un utilisateur manuellement

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli add -k /var/keepass/files/dsi_t1.key /var/keepass/files/dsi_t1.kdbx "wilder6" --username "nathan"

![](Ressources/ajout-user_wild6.png)

## 13. Pour ajouter des informations à l'utilisateur par exemple mail ou téléphone

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli edit -k /var/keepass/files/dsi_t1.key /var/keepass/files/dsi_t1.kdbx "wilder6" --notes "mail:nathan@proton.com\nTél: 06-47-13-48-19"

![](Ressources/ajout_informations_user.png)

## 14. Pour vérifier les entrées dans la base de données

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli ls -k /var/keepass/files/dsi_t1.key /var/keepass/files/dsi_t1.kdbx

![](Ressources/Lister_all_user.png)

## 15. Pour afficher un utilisateur spécifique

- *Entre cette commande :*

wilder@srvlx01:~$ sudo -u keepass_wilder keepassxc-cli show -k /var/keepass/files/dsi_t1.key /var/keepass/files/dsi_t1.kdbx wilder6

![](Ressources/lister_user_wilder6.png)

## 16. Attribution des droits d'accès au client wilder 

- *Entre cette commande :*

wilder@srvlx01:~$ sudo chown -R keepass_wilder:wilder /var/keepass/files

## 17.Donne des droits de lecture/écriture/exécution au groupe

- *Entrez cette commande :*

wilder@srvlx01:~$ sudo chmod -R 770 /var/keepass/files

## 18. Pour vérifier les droits

- *Entrez cette commande :*

wilder@srvlx01:~$ sudo ls -l /var/keepass/files

![](Ressources/verif_droit_distant.png)


## Installation sur le serveur Windown SRVWIN01

## Étape 1 : Installation de KeePassXC sur SRVWIN01

1. Télécharge et installe Keepassxc sur windows server
https://keepassxc.org/download
2. Lancez l'application Keepassxc

## Étap 2 : Création de la base de données

1. Clique sur **Create Database** dans l'écran d'accueil
![](Ressources/ouverture_keepass.png)

2. Entre les informations de la DB et clique sur continue
![](Ressources/info_db.png)

3. Choisis le format **KDBX4**
4. Régle le temps de décryptage si besoin et clique sur **continue** 
![](Ressources/securite.png)

## Étape 3 : Configuration des identifiants

1. Entre un mot de passe principal fort 
2. Confirme le mot de passe
![](Ressources/ajout_mdp_cle.png)

3. Clique sur **Add additional protection** pour renforcer la sécurité
4. Dans la section Key File, clique sur **Generate**
![](Ressources/genere_cle.png)

5. Enregistre le fichier clé  dans ton dossier ou un emplacement securisé  
6. Clique sur **Done**
7. L'interface keepass s'ouvre et tu pourras rajouter des données 

![](Ressources/interfac_keepass.png)

## Étape 4 : Préparation du partage réseau

1. Dans l'explorateur de fichier , ouvre ton dossier keepass a partager
2. Fait un clic droit sur le dossier puis  **Properties**  et  **Sharing**
3. Entre le mot de passe administrateur

![](Ressources/connexion_mode_admin.png)

4. Clique sur Advanced sharing et coche Share this folder 

![](Ressources/cocher_shared.png)

5. Clique sur **Permissions**
6. Sélectionne  le groupe **Everyone**
7. Accorde les permissions :
    - Coche : **Full Control** 
    - Coche : **Change** 
    - Coche : **Read** 
8. Clique sur Aplly et  OK 

# 3. Installation sur les clients

<span id="installation-sur-le-client"></span>

# Configuration du client UBU01 pour acceder a la db SRVLX01

## 1. Mise à jour du système et installation de sshfs et keepassxc

- *Entre cette commande :*

wilder@ubu01:~$ sudo apt update && sudo apt install -y sshfs keepassxc

![](Ressources/installation_sshfs_MAJ_paquets.png)

## 2. Création d'un point de montage

Créer le dossier local où sera montée la base de données distante.

- *Entre cette commande :*

wilder@ubu01:~$ mkdir -p ~/keepass_srvlx01

![](Ressources/création_dossier.png)

## 3. Montage du dossier distant SSHFS

- *Entre cette commande :*

wilder@ubu01:~$ sshfs wilder@172.16.10.6:/var/keepass/files ~/keepass_srvlx01

## 4. Vérification du montage et des droits

- *Entre cette commande :*

wilder@ubu01:~$ ls -l ~/keepass_srvlx01

 dsi_t1.kdbx et dsi_t1.key 

![](Ressources/montage_server_srvlx01.png)

## 5. Liste les entrées de la DB

Affiche les entrées,il demandera le mot de passe principal **keepass_wilder**.

- *Entre cette commande :*

wilder@ubu01:~$ keepassxc-cli ls -k ~/keepass_srvlx01/dsi_t1.key ~/keepass_srvlx01/dsi_t1.kdbx

![](Ressources/liste_entrée_srvlx.png)

## 6. Liste une entrée specifique par exemple wilder1

- *Entre cette commande :*

wilder@ubu01:~$ keepassxc-cli show -k ~/keepass_srvlx01/dsi_t1.key ~/keepass_srvlx01/dsi_t1.kdbx wilder1 

![](Ressources/lister_entrée_wilder1.png)


# Configuration du client UBU01 pour acceder a la db SRVWIN01

## 1. Installer KeePass en mode graphique (GUI)

wilder@ubu01:~$ sudo apt update && sudo apt install keepassxc cifs-utils -y

![](Ressources/Maj_installation.png)

## 2. Crée le dossier local et verification 

wilder@ubu01:~$ mkdir -p ~/keepass_srvwin01

wilder@ubu01:~$ ls -l keepass_srvwin01/

![](Ressources/creation_dossier_verif.png)

## 3. Monte le partage Windows

wilder@ubu01:~$ sudo mount -t cifs //172.16.10.5/Keepass_db_srwin01 ~/keepass_srvwin01 -o username=wilder

![](Ressources/montage_local.png)

## 4. Vérifie le montage 

wilder@ubu01:~$ ls -l keepass_srvwin01/

![](Ressources/verif_montage.png)

## 5. Lance KeePass

wilder@ubu01:~$ keepassxc

## 6. Ouvre la base de données

Cliquer sur **Ouvrir une base de données existante**

![](Ressources/ouverture_keepass_srvwin_sur_ubu.png)

## 7. Sélectionne le fichier de base de données

- Choisir le fichier : **dsi_to**

![](Ressources/selectionne_db.png)

## 8. Parcourir et sélectionne le fichier de clé

- Cliquer sur **Parcourir**

![](Ressources/parcourir.png)

- Sélectionner le fichier de clé (key file)

![](Ressources/key.png)

## 9. Déverrouiller la base de données

- Entrer le mot de passe de la base de données

![](Ressources/mot_de_passe.png)

- Cliquer sur **Déverrouiller**

Puis l'interface s'ouvre

![](Ressources/interface.png)

# Configuration du client WIN01 pour acceder a la Db SRVLX01

**Télécharge et installe les outils suivants  avec les paramètres par défaut** 

- WINSCP :  https://winscp.net/eng/download.php

- KEEPASSXC : (https://keepassxc.org/download/#windows)

#### **Étape 1 : Connexion au serveur SRVLX01 via winSCP**

1. Lance winSCP depuis le menu Démarrer
2. Dans la fenêtre session entre les données demandées
    - Nom d’hôte : 172.16.10.6
    - Nom d’utilisateur : nom_utilisateur_linux(wilder)
    - Mot de passe : Saisie le mot de passe associé à l’utilisateur.
    - Protocole : Choisit SFTP port 22 par défaut
  
3. Clique sur **Connexion** pour te connecter au serveur

![](Ressources/detail_DB.png)

#### **Étape 2 : Entre dans le dossier KeePass_DB**

1. Une fois connecté, sur la droite :

    - Accède au dossier keepass_db .

![](Ressources/keepass_db_.png)

2. Tu devrais voir les fichiers suivants :
    - **dsi_t1.kdbx** : La base de données KeePass.
    - **dsi_t1.key** : La clé de chiffrement associée.
3. Sélectionne les deux fichiers

![](Ressources/detail_keepass_db.png)

#### **Étape 3 : Copier et coller les  fichiers sur ton PC local**

1. Fais glisser **dsi_t1.kdbx** et **dsi_t1.key**  vers le panneau de gauche ton PC local,   C:\Users\wilder\Desktop
2. Vérifie que les fichiers sont bien présents dans le dossier de destination.

![](Ressources/copie-coller.png)

#### **Étape 4 : Ouverture de la base de données avec KeePassXC**

1. Lance KeePassXC depuis de ton pc Windows.
2. Dans l’interface de KeePassXC :
    - Clique sur **Ouvrir une base de données**.

![](Ressources/keepass_interface.png)
    
3. Dans la fenêtre d’ouverture :
    - Sélectionne le fichier **dsi_t1.kdbx** que tu as collé.
    - Clique sur **Ouvrir**.

![](Ressources/ouverture_DB_keepass.png)

4. Pour sélectionner le fichier clé :
    - Clique sur **Parcourir** à côté de Sélectionner le fichier clé.
    - Choisis le fichier **dsi_t1.key** que tu as téléchargé.

![](Ressources/cle_chiffrement.png)

5. Une fenêtre te demande de saisir le mot de passe de la base de données.

![](Ressources/MDP_cle.png)

6. Clique sur **Déverrouiller** pour accéder à la base.

![](Ressources/keepass_infos.png)

Après avoir ouvert la base de données avec Keepassxc, tu peux ajouter, créer ou modifier des entrées utilisateurs et mots de passe.

# Configuration du client WIN01 pour acceder a la Db SRVWIN01

## 1. Télécharge et installe KeePassXC

   - https://keepassxc.org/download

## 2. Monter le partage réseau

   - Ouvrir l'Explorateur Windows
   - Taper dans la barre d'adresse : \\172.16.10.5\Keepass_db_srwin01

![](Ressources/srvwin_win.png)

   - Entre les identifiants : utilisateur **wilder** et son mot de passe
  
 ![](Ressources/info-db-srwwin-win.png) 

## 3. Lance KeePassXC

## 4. Ouvre la base de données
   - Clique sur **Ouvrir une base de données existante**
 
  ![](Ressources/keepass_interface.png)

   - Choisir le fichier : dsi_to

![](Ressources/db_srv_win_win.png)

## 5. Ajoute la  clé
   - Cliquer sur **Parcourir** dans la section fichier clé 
![](Ressources/key_win_win.png)

## 6. Déverrouille la Db
   - Entrer le mot de passe de la base de données
   - Cliquer sur **Déverrouiller**

![](Ressources/ineterface_db_win.png)





# 4. FAQ
<span id="faq"></span>
Cette FAQ aborde les problèmes potentiels et questions techniques courantes lors de la mise en place de KeePass sur différents systèmes. Elle se concentre sur les dépannages pour une installation réussie.

## Sur Windows Server

**Q1 : Que faire si l'installation échoue à cause de .NET Framework ?**  
Vérifiez que .NET Framework 4.8 est installé via le Gestionnaire de serveur. Téléchargez-le depuis le site Microsoft si nécessaire et relancez l'installation.

**Q2 : KeePass est-il compatible avec les rôles serveur comme Active Directory ?**  
Oui, mais exécutez-le via une session Remote Desktop pour éviter les conflits avec les services serveur. Testez en mode compatibilité si des erreurs surgissent.

## Sur Linux Debian

**Q1 : Que faire en cas d'erreur liée à Mono lors du lancement ?**  
Mettez à jour Mono avec sudo apt update && sudo apt upgrade mono-complete . Vérifiez les logs dans le terminal pour des détails spécifiques.

**Q2 : Problèmes de permissions pour les bases de données KeePass ?**  
Assurez-vous que l'utilisateur a les droits en lecture/écriture sur le dossier des fichiers .kdbx. Évitez de lancer en root pour des raisons de sécurité.

## Sur Windows 11 (VM Client)

**Q1 : Pourquoi KeePass est-il lent dans une VM Windows 11 ?**  
Allouez plus de RAM et CPU à la VM via les paramètres de l'hyperviseur. Désactivez les effets graphiques inutiles dans Windows pour améliorer les performances.

**Q2 : Erreurs de synchronisation avec des plugins comme KeeAnywhere ?**  
Vérifiez la connexion réseau de la VM et mettez à jour les plugins. Testez sans plugins pour isoler le problème, souvent lié à des certificats SSL.

## Sur Linux Ubuntu (VM Client)

**Q1 : Que faire si KeePass ne s'ouvre pas après installation dans une VM Ubuntu ?**  
Installez les dépendances manquantes comme mono-complete et xdotool via apt. Relancez et vérifiez les erreurs dans le terminal.

**Q2 : Problèmes d'intégration avec le clipboard dans une VM ?**  
Installez les outils invités de votre hyperviseur (ex. : VirtualBox Guest Additions) pour une meilleure gestion du presse-papiers partagé.
