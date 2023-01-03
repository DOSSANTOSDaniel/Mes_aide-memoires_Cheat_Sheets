# Commandes pratiques(Nextcloud version SNAP)
Pour plus d'informations : [Nextcloud snap](https://github.com/nextcloud-snap/nextcloud-snap), [Admin manual](https://docs.nextcloud.com/server/stable/admin_manual/).

Applications utilisées.
```
**Database:** mysql 8.0.31

**PHP version:** 8.0.25

**Nextcloud version:** 25.0.2 - 25.0.2.3
```

Il existe un script nommé "occ" à la racine du serveur Nextcloud qui nous permet
d’effectuer certaines tâches d'administration.

Par défaut le serveur écoute sur le port 80, modification du port d'écoute en http.
```Bash
sudo snap set nextcloud ports.http=88
```

Par défaut si https est activé le serveur écoute sur le port 80 et le port 443, tout le trafic http sera redirigé vers https, modification du port d'écoute en https.
```Bash
sudo snap set nextcloud ports.https=448
```

Modifier les deux ports d'écoute.
```bash
sudo snap set nextcloud ports.http=88 ports.https=448
```

Activer https avec un certificat auto-signé.
```bash
sudo snap nextcloud.enable-https
```

Désactive https, le certificat auto-signé ne sera pas supprimé.
```bash
sudo snap nextcloud.disable-https
```

Affiche la liste des commandes possibles.
```Bash
sudo nextcloud.occ list
```

Afficher l'aide sur une commande en particulier.
```Bash
sudo nextcloud.occ help <commande>
```

Affiche la configuration sans les données sensibles.
```Bash
sudo nextcloud.occ config:list
```

Affiche la configuration en montrant aussi des données sensibles comme par exemple les mots de passe.
```Bash
sudo nextcloud.occ config:list --private
```

Exportation de la configuration, des données, de la base de données et des applications.
```Bash
sudo nextcloud.export -a -b -c -d
```
* L'exportation se fait vers le fichier /var/snap/nextcloud/common/backups/20230102-184253.

Importation sur un autre serveur.
```Bash
sudo nextcloud.import -a -b -c -d backups/20230102-184253
```

Nettoyer la mémoire cache de Nextcloud.
```Bash
sudo nextcloud.occ files:cleanup
```

Effacer la corbeille de tous les utilisateurs.
```Bash
sudo nextcloud.occ trashbin:cleanup --all-users
```

Effacer la corbeille d’un utilisateur en particulier.
```Bash
sudo nextcloud.occ trashbin:cleanup <nom utilisateur>
```

Actualisation de toutes les données du serveur Nextcloud.
```Bash
sudo nextcloud.occ files:scan -vvv --all
```

Actualisation de dossiers et fichiers en particulier.
```Bash
sudo nextcloud.occ files:scan -vvv --path="/<nom utilisateur>/files
```

```Bash
sudo nextcloud.occ files:scan -vvv --path="daniel/files/Photos/"
```

Actualiser les dossiers et fichiers d’un utilisateur en particulier.
```Bash
sudo nextcloud.occ files:scan -vvv <nom utilisateur>
```

Actualiser les données des utilisateurs appartenant à un groupe en particulier.
```Bash
sudo nextcloud.occ files:scan -vvv --groups=<nom groupe1>,<nom groupe2>
```

Configuration des logs.
```Bash
sudo nextcloud.occ log:manage
```

Emplacement du fichier log:
```Bash
sudo nextcloud.occ log:file
```

Par défaut, on ne peut téléverser des fichiers de plus de 2Mo, c’est une limitation de la configuration de PHP.
Modifier la limite.
```Bash
sudo snap set nextcloud php.memory-limit=512M
```

Permettre les téléversement de fichiers de taille illimité.
```Bash
sudo snap set nextcloud php.memory-limit=-1
```

Créer un nouvel utilisateur.
```Bash
sudo nextcloud.occ user:add <nom utilisateur>
```

Créer un nouvel utilisateur avec un groupe.
```Bash
sudo nextcloud.occ user:add -g <nom groupe> <nom utilisateur>
```

Supprimer un utilisateur.
```Bash
sudo nextcloud.occ user:delete <nom utilisateur>
```

Supprimer un utilisateur.
```Bash
sudo nextcloud.occ user:delete <nom utilisateur>
```

Afficher la date et l'heure de la dernière fois qu’un utilisateur s’est connecté.
```Bash
sudo nextcloud.occ user:lastseen <nom utilisateur>
```

Afficher un résumé des utilisateurs et des données utilisées sur le serveur.
```Bash
sudo nextcloud.occ user:report
```

Modifier le mot de passe des utilisateurs.
```Bash
sudo nextcloud.occ user:resetpassword <nom utilisateur>
```

Autres commandes(user:).
|commande|Description|
|---|---|
|user:disable|Désactiver un utilisateur.|
|user:enable|Activer un utilisateur.|
|user:info|Affiche des informations sur un utilisateur.|
|user:list|Afficher les utilisateurs.|
|user:report|Afficher un résumé sur les accès des utilisateurs.|
|user:resetpassword|Changer le mot de passe d'un utilisateur.|
|user:setting|Lire et modifier les configurations des utilisateurs.|

Créer un nouveau groupe.
```Bash
sudo nextcloud.occ group:add <nom groupe>
```

Autres commandes(group:).
|commande|Description|
|---|---|
|group:adduser|Ajoute un utilisateur à un groupe.|
|group:delete|Supprime un groupe.|
|group:info|Afficher des informations sur un groupe.|
|group:list|Lister les groupes.|
|group:removeuser|Supprimer un utilisateur d'un groupe.|

Application client de Nextcloud, sur les systèmes Windows le fichier de configuration du client Nextcloud :  %APPDATA%\nextcloud\nextcloud.cfg.

Sur les systèmes MAC OS X le fichier de configuration est ici : $HOME/Library/Preferences/nextcloud/nextcloud.cfg.

Afficher les logs de l'application client, une fois la fenêtre du client ouverte il faut taper <kbd>F12</kbd>.

Domaine de confiance (Trusted domain), ajouter le nom de domaine ou l'adresse IP du serveur à partir du fichier /var/www/html/nextcloud/config/config.php.
```Bash
sudo nano /var/snap/nextcloud/current/nextcloud/config/config.php
```

```Bash
'trusted_domains' =>
  array (
    0 => '192.168.1.52',
  ),
```

Autre façon de configurer le domaine de confiance (Trusted domain).
Afficher les domaines configurés.
```Bash
daniel@server:~$ sudo nextcloud.occ config:system:get trusted_domains
192.168.1.52
```

Ajout d'un domaine.
```Bash
daniel@server:~$ sudo nextcloud.occ config:system:set trusted_domains 1 --value=next.dsjdf.fr
System config value trusted_domains => 1 set to string next.dsjdf.fr
```

```Bash
daniel@server:~$ sudo nextcloud.occ config:system:get trusted_domains
192.168.1.52
next.dsjdf.fr
```

Supprimer un domaine.
```Bash
daniel@server:~$ sudo nextcloud.occ config:system:delete trusted_domains 1
System config value trusted_domains => 1 deleted
```

Mettre le serveur en mode maintenance.
```Bash
sudo nextcloud.occ maintenance:mode --on
```

Désactivation du mode maintenance.
```Bash
sudo nextcloud.occ maintenance:mode --off
```

Afficher les informations de base du serveur.
```Bash
daniel@server:~$ sudo nextcloud.occ status
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
daniel@server:~$ sudo nextcloud.occ upgrade
```

Liste des applications.
```Bash
daniel@server:~$ sudo nextcloud.occ app:list 
```

Mise à jour de tous les applications ou d'une seule application.
```Bash
daniel@server:~$ sudo nextcloud.occ app:update --all
```

Créer une notification pour avertir les utilisateurs.
```Bash
daniel@server:~$ sudo nextcloud.occ notification:generate --long-message "Un long message !" daniel "Message de teste"
```

Générer un rapport système.
```Bash
daniel@server:~$ sudo nextcloud.occ support:report
```

Activation de https.
```Bash
daniel@server:~$ sudo nextcloud.enable-https self-signed
Generating key and self-signed certificate... done
Restarting apache... done
```

Exporter l’entièreté des données du serveur.
```Bash
daniel@server:~$ sudo nextcloud.export
[sudo] password for daniel: 
WARNING: This functionality is still experimental and under
development, use at your own risk. Note that the CLI interface is
unstable, so beware if using from within scripts.

Enabling maintenance mode... done
Exporting apps...
        556.36M 100%   12.20MB/s    0:00:43 (xfr#6299, to-chk=0/7467)   
Exporting database...
Exporting config...
Exporting data...
         31.27M 100%   27.21MB/s    0:00:01 (xfr#96, to-chk=0/267)  

Successfully exported /var/snap/nextcloud/common/backups/20230103-163644
Disabling maintenance mode... done
```

Importer les données vers un autre serveur.
```Bash
daniel@server:~$ sudo nextcloud.import <dossier de sauvegarde>
```

Désactiver https.
```Bash
daniel@server:~$ sudo nextcloud.disable-https
```

Connexion à la base de données.
```Bash
daniel@server:~$ sudo nextcloud.mysql-client
```

 Sauvegarde des bases de données.
```Bash
daniel@server:~$ sudo nextcloud.mysqldump
```