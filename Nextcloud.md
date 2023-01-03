# Commandes pratiques
Pour plus d'informations : [Admin manual](https://docs.nextcloud.com/server/stable/admin_manual/).

Applications utilisées.
```
**Database:** mysql 10.5.18

**PHP version:** 7.4.33

**Nextcloud version:** 25.0.2 - 25.0.2.3
```

Il existe un script nommé "occ" à la racine du serveur Nextcloud qui nous permet
d’effectuer certaines tâches d'administration.

Le script s'exécute avec php et avec les droits de l’utilisateur www-data.

Affiche la liste des commandes possibles.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ list
```

Afficher l'aide sur une commande en particulier.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ help <commande>
```

Affiche la configuration sans les données sensibles.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ config:list
```

Affiche la configuration en montrant aussi les données sensibles comme par
exemple les mots de passe.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ config:list --private
```

Exportation de la configuration.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ config:list --private --output=json > fichier.json
```

Importation de la configuration.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ config:import < "nom du fichier.json"
```

Nettoyer la mémoire cache de Nextcloud.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:cleanup
```

Effacer la corbeille de tous les utilisateurs.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ trashbin:cleanup --all-users
```

Effacer la corbeille d’un utilisateur en particulier.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ trashbin:cleanup <nom utilisateur>
```

Actualisation de tous les dossiers et fichiers et synchronisation des données.

Quand on copie manuellement des fichiers dans le serveur Nextcloud celui-ci prend un certain temps pour actualiser les données, on peut lancer manuellement l'actualisation des fichiers.

Configuration des droits sur les nouveaux fichiers ou dossiers.
```Bash
chown -R www-data:www-data /var/www/html/nextcloud/data/daniel/files/<dossier ou fichier>
```

```Bash
find /var/www/html/nextcloud/data/daniel/files/<chemin du dossier> -type f -exec chmod 644 {} +
```

```Bash
find /var/www/html/nextcloud/data/daniel/files/<chemin du dossier> -type d -exec chmod 755 {} +
```

Actualisation de toutes les données du serveur Nextcloud.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:scan -vvv --all
```

Actualisation d'un dossier ou fichier en particulier.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:scan -vvv --path="/<nom utilisateur>/files
```

```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:scan -vvv --path="daniel/files/Photos/"
```

Actualise les fichiers et dossiers d’un utilisateur en particulier.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:scan -vvv <nom utilisateur>
```

Actualise les données des utilisateurs appartenant à un groupe en particulier.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ files:scan -vvv --groups=<nom groupe1>,<nom groupe2>
```

Configuration des logs.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ log:manage
```

Emplacement du fichier log:
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ log:file
```

Par défaut, on ne peut téléverser des fichiers de plus de 2Mo, c’est une limitation de la
configuration de PHP.
1. Pour modifier la limite, il faut éditer le fichier /etc/php/7.4/apache2/php.ini. 
```Bash
upload_max_filesize = 2M
post_max_size = 8M
```

2. Relancer le serveur Apache2.
```Bash
sudo systemctl restart apache2
```

Créer un nouvel utilisateur.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:add <nom utilisateur>
```

Créer un nouvel utilisateur avec un groupe.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:add -g <nom groupe> <nom utilisateur>
```

Supprimer un utilisateur.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:delete <nom utilisateur>
```

Afficher la date et l'heure de la dernière fois qu’un utilisateur s’est connecté.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:lastseen <nom utilisateur>
```

Afficher un résumé des utilisateurs et des données utilisées sur le serveur.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:report
```

Modifier le mot de passe des utilisateurs.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ user:resetpassword <nom utilisateur>
```

Autres commandes(user:).
|commande|Description|
|---|---|
|user:disable|Désactiver un utilisateur.|
|user:enable|Activer un utilisateur.|
|user:info|Affiche des informations sur un utilisateur.|
|user:list|Afficher les utilisateurs.|
|user:report|Afficher un résumé sur les accès des utilisateurs.|
|user:setting|Lire et modifier les configurations des utilisateurs.|

Créer un nouveau groupe.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ group:add <nom groupe>
```

Autres commandes(group:).
|commande|Description|
|---|---|
|group:adduser|Ajoute un utilisateur à un groupe.|
|group:delete|Supprime un groupe.|
|group:info|Afficher des informations sur un groupe.|
|group:list|Lister les groupes.|
|group:removeuser|Supprimer un utilisateur d'un groupe.|

Application client de Nextcloud, sur les systèmes Windows le fichier de configuration du client Nextcloud :  %APPDATA%\nextcloud\nextcloud.cfg

Sur les systèmes MAC OSX le fichier de configuration est : $HOME/Library/Preferences/nextcloud/nextcloud.cfg

Afficher les logs de l'application client, une fois la fenêtre du client ouverte il faut taper <kbd>F12</kbd>.

Domaine de confiance (Trusted domain), ajouter le nom de domaine ou l'adresse IP du serveur  Nextcloud à partir du fichier /var/www/html/nextcloud/config/config.php.
```Bash
sudo nano /var/www/html/nextcloud/config/config.php
```

```Bash
'trusted_domains' =>
  array (
    0 => '192.168.1.32',
  ),

```

Puis redémarrer le serveur web.
```Bash
sudo systemctl restart apache2
```

Autre façon de configurer le domaine de confiance (Trusted domain).
Afficher les domaines configurés.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ config:system:get trusted_domains
192.168.1.52
```

Ajout d'un domaine.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ config:system:set trusted_domains 1 --value=next.dsjdf.fr
System config value trusted_domains => 1 set to string next.dsjdf.fr
```

```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ config:system:get trusted_domains
192.168.1.52
next.dsjdf.fr
```

Supprimer un domaine.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ config:system:delete trusted_domains 1
System config value trusted_domains => 1 deleted
```

Mettre le serveur en mode maintenance.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ maintenance:mode --on
```

Désactivation du mode maintenance.
```Bash
sudo -u www-data php /var/www/html/nextcloud/occ maintenance:mode --off
```

Afficher les informations de base du serveur.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ status
  - installed: true
  - version: 25.0.2.3
  - versionstring: 25.0.2
  - edition: 
  - maintenance: false
  - needsDbUpgrade: false
  - productname: Nextcloud
  - extendedSupport: false
```

Mise à jour du serveur.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ upgrade
```

Liste des applications.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ app:list 
```

Mise à jour de tous les applications ou d'une seule application.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ app:update --all
```

Créer une notification pour avertir les utilisateurs.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ notification:generate --long-message "Un long message !" daniel "Message de teste"
```

Générer un rapport système.
```Bash
daniel@server:~$ sudo -u www-data php /var/www/html/nextcloud/occ support:report
```