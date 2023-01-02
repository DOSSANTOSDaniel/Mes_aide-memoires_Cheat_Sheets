# SQL avec MariaDB

Connexion au serveur de bases de données.
```sql
daniel@server:~$ sudo mysql -u root -p -h localhost
```

Création d’une nouvelle base de données.
```sql
create database <nom de la base>
```

Affiche les bases de données.
```sql
Show databases;
```

Supprime une base de données.
```sql
drop database <nom de la base>
```

Utiliser une base de données.
```sql
use <nom de la base>
```

Création d’une table avec deux colonnes.
```sql
create table <nom de la table>
(
nom	char(20),
prénom	char(20)
);
```

Afficher toutes les tables.
```sql
show tables;
```

Afficher les colonnes d'une table.
```sql
show columns from <nom de la table>
```

Création d’une table avec clé primaire.
```sql
create table client
(
nom char(20),
prenom char(20),
tel char(20),
primary key (nom)
);
```

Supprimer une table.
```sql
drop table client 
```

Modifier la structure d’une base de données.
```sql
alter table client add column toto char(20) not nul;
```

```sql
alter table client modify tel int(15);
```

Les insertions. 
```sql
insert into client (nom, prenom, tel) values ("dos_santos","daniel","0623****");
```

Afficher la table et ses valeurs.
```sql
select * from client;
```

Ajout d’une grande quantité de données à l’aide d’un fichier texte.
```sql
load data infile "fichier.txt" into table client;
```