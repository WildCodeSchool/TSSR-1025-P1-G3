## Sommaire

1. [Utilisation de base](#utilisation-de-base)
2. [Utilisation avancée](#utilisation-avancee)
3. [FAQ](#faq)

# 1. Utilisation de base
<span id="utilisation-de-base"></span>

# 2. Utilisation avancée
<span id="utilisation-avancee"></span>

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