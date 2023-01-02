#  Administration de PostgreSQL et commandes PostgreSQL

## Les clients de connexion au serveur PostgreSQL
|programme|Description|
|---|---|
|psql|Client en ligne de commande.|
|pgadmin|Client avec interface graphique.|

## Définitions
||Description|
|---|---|
|users|Utilisateurs avec login et mot de passe.|
|rôle|La gestion des droits sur les bases de données est faite par rôle, un rôle c'est soit un utilisateur soit un groupe d'utilisateurs un rôle peut contenir des objets.|
|database|Ensemble de données structurées|
|Schéma|Espace de nom dans une base de données(un groupe d'éléments).|
|tables|Espace de stockage logique dans une base de données.|
|champs|Une colonne dans une table.|
|lignes|Chaque colonne d'une table contiens des lignes.|

## Les répertoires et fichiers
|Dossier|Description|
|---|---|
|/etc/postgresql/15/main|Configurations.|
|/var/lib/postgresql/15/main|Données des bases de données.|
|/usr/lib/postgresql/15/bin/postgres|Fichier binaire principal.|
|/usr/bin/pg_*|Autres binaires.|

|Fichier|Description|
|---|---|
|/etc/postgresql/15/main/postgresql.conf|Configuration principale.|
|/etc/postgresql/15/main/pg_hba.conf|Configuration des accès au serveur PostgreSQL.|
|/etc/postgresql/15/main/pg_ident.conf|Configuration du mapping entre un utilisateur système et un rôle PostgreSQL.| 

## Les binaires
|Binaire|Description|
|---|---|
|pg_ctl|Démarrer ou arrêter une instance PostgreSQL.|
|psql|Client de connexion en ligne de commande.|
|pg_createcluster|Création d'une instance ou cluster de PostgreeSQL.|
|pg_dropcluster|Supprimer un cluster ou instance.|
|pg_lsclusters|Liste les clusters.|
|pg_ctlcluster|Gérer les clusters.|
|pg_dump|Sauvegarder des instances de PostgreSQL.|
|pg_dumpall|Sauvegarder l'intégralité d'un cluster.|
|pg_restore|Restaurer une sauvegarde faite avec pg_dumpall.|

* postgres est l'utilisateur créé par défaut à l’installation de PosgreSQL.

Gestion du service PostgreSQL via systemd.
```Bash
sudo systemctl start|stop|reload|restart|status postgresql@15-main.service
```

Afficher l'historique des commandes PostgreSQL.
```bash
less $HOME/.psql_history
```

## Connexion à l'invite de commande de PostgreSQL
Connexion avec le compte utilisateur postgres.
```bash
sudo -i -u postgres
```

Connexion à l'invite de commande.
```bash
psql
```

Connexion sur la base de donnée postgres
```bash
daniel@server:~$ psql postgres
psql (15.1 (Ubuntu 15.1-1.pgdg22.04+1))
Saisissez « help » pour l'aide.

postgres=# 
```

## Connexion à l'invite de commande de PostgreSQL à partir d'une machine distante
```bash
sudo vim /etc/postgresql/15/main/postgresql.conf
```
* Modiﬁer la ligne "#listen_addresses = 'localhost'" par "listen_addresses = '0.0.0.0'".

Conﬁguration de l’authentification.
```bash
sudo vim /etc/postgresql/15/main/pg_hba.conf
```
* Ajouter à la fin du fichier : "host    all             all             192.168.1.22/24         scram-sha-256"
* 192.168.1.22 est la machine client qui poura se connecter au serveur PostgreSQL.

Redémarrage du service.
```bash
sudo systemctl restart postgresql@15-main.service
```

Connexion sur la machine distante, (psql -h <IP> -p <Port> -U <User> -d <DB>).
```bash
psql -h 192.168.1.53 -p 5432 -U postgres -d postgres
```

Connexion à une instance d'un cluster en particulier, (psql --cluster <Nom> -h <IP> -p <Port> -U <User> -d <DB>).

## Les applications du client PostgreSQL
* C'est comme des alias pour les commandes SQL.

|Application|Description|
|---|---|
|createdb|Créer une base de donnée.|
|dropdb|Supprimer une base de donnée.|
|createuser|Créer des utilisateurs.|
|dropuser|Supprimer des utilisateurs.|

Création d'un utilisateur non super-utilisateur.
```bash
postgres@server:~$ createuser --interactive --no-superuser --pwprompt daniel
Saisir le mot de passe pour le nouveau rôle : 
Saisir le mot de passe à nouveau : 
Le nouveau rôle est-il autorisé à créer des bases de données ? (o/n) o
Le nouveau rôle est-il autorisé à créer de nouveaux rôles ? (o/n) n
```

Supprimer un utilisateur.
```bash
postgres@server:~$ dropuser daniel
```

Créer une base de données.
```sql
postgres@server:~$ createdb exemple_db -O daniel
```

Supprimer une base de données.
```bash
postgres@server:~$ dropdb exemple_db
```

## Quelques commandes à partir du shell Linux
Afficher la version du serveur PostgreSQL.
```bash
daniel@server:~$ sudo -i -u postgres
postgres@server:~$ psql -c 'SELECT version();'
```

Afficher la version du client PostgreSQL.
```bash
daniel@server:~$ psql -V
```

Liste les bases de données.
```bash
postgres@ubuntu:~$ psql -c '\l'
```

Afficher les utilisateurs.
```bash
postgres@ubuntu:~$ psql -c 'SELECT * FROM User;'
```

## Quelques commandes spécifiques à PostgreSQL
Toutes les commandes PostgreSQL commencent par `\`.

Utiliser un éditeur de texte pour envoyer des requêtes SQL au serveur.
```sql
postgres=# \e
```

Quitter l'invite de commande.
```sql
postgres=# \q
``` 

Affichage des bases de données.
```sql
postgres=# \l
```

Liste les commandes possibles.
```sql
postgres=# \?
```

Aide concernant une commande.
```sql
postgres=# \h SELECT
```

Afficher les utilisateurs.
```sql
postgres=# \du
```

Changer le mot de passe d'un utilisateur, exemple avec postgres.
```sql
postgres=# \password postgres
Saisir le nouveau mot de passe de l'utilisateur « postgres » : 
Saisir le mot de passe à nouveau :
```

Se connecter à la base de donnée postgres.
```sql
postgres=# \c postgres
```

Lister les schémas.
```sql
postgres=# \dn
```

Lister les tables.
```sql
postgres=# \dt *
```

Lister les tables d'une base de données.
```sql
postgres=# \d
```

Lister les champs d'une table.
```sql
postgres=# \dS <nom de la table>
```

* Rajouter + pour afficher plus d'informations, exemple : `postgres=# \l+`.

## Quelques commandes SQL
Création d'un utilisateur.
```sql
postgres=# CREATE USER daniel WITH password '1234';
```

Accorder les privilèges à un utilisateur sur une base de données.
```sql
postgres=# GRANT ALL PRIVILEGES ON DATABASE postgres TO daniel;
```

Supprimer un utilisateur.
```sql
postgres=# DROP USER daniel;
```

Créer un rôle avec plusieurs privilèges.
```sql
postgres=# CREATE ROLE administrateur WITH LOGIN ENCRYPTED PASSWORD '1234' CREATEDB CREATEROLE REPLICATION SUPERUSER;
```

Modifier un rôle.
```sql
postgres=# ALTER ROLE daniel CREATEROLE CREATEDB REPLICATION SUPERUSER;
```

Supprimer un rôle.
```sql
postgres=# DROP ROLE daniel;
```

Créer une base de données.
```sql
postgres=# CREATE DATABASE toto WITH OWNER daniel;
```

Supprimer une base de donnée.
```sql
postgres=# DROP DATABASE tata;
```

Création d'une base de données.
```sql
postgres=# create database exemple_db;
```

Accorder tous les privilèges sur une base de données.
```sql
postgres=# grant all privileges on database exemple_db to daniel;
```

Modifier le mot de passe d’un utilisateur.
```sql
postgres=# ALTER USER postgres WITH PASSWORD 'digital';
```

## Rediriger les résultats de mes requêtes dans un fichier et vise versa.
Redirection dans un fichier.
```bash
postgres@ubuntu:~$ psql -c 'SELECT * FROM User;' -L fichier.log
```

Autre méthode pour la redirection dans un fichier.
```bash
postgres=# \o fichier.sql
```

Puis pour terminer la redirection.
```bash
postgres=# \o
```

Utiliser un fichier pour re exécuter des commandes.
```bash
psql -f script_sql.sql
```

Afficher le résultat au format HTML.
```bash
psql -c 'SELECT * FROM User;' -H
```

## Sauvegardes

toutes les bases de données.
```bash
postgres@server:~$ pg_dumpall -g > all_db.sql
```

sauvegarder une seule base de donnée.
```bash
postgres@server:~$ pg_dumpall -U postgres postgres -f postgres_db.sql
```

## Restauration
Restaurer une base de donnée.
```bash
postgres@server:~$ psql -U postgres -d postgres -f postgres_db.sql
```

Restaurer toutes les bases de données.
```bash
postgres@server:~$ psql -f all_db.sql
```