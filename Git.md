# Git
## Schéma des fonctions basiques de Git
```
                          (Local)                      (Distant, ex: GitHub, GitLab...)
     +----------------------------------------------+  +------------------+
     |                (git commit -a)               |  |                  |
     |    |===============================>>|       |  |                  |
     |    |   (git add)       (git commit)  |       |  |                  |
     |    |===============>>|=============>>|    (git push)               |
     |    |                 |               |==================>>|        |
     |    |                 |               |       |  |         |        |
 +--------+--------+     +--+--+     +------+-----+ |  |  +------+------+ |
 |Espace de travail|     |Index|     |Dépôt local | |  |  |Dépôt distant| |
 +--------+--------+     +--+--+     +------+-----+ |  |  +------+------+ |
     |    |                 (git pull)      |       |  |         |        |
     |    |<<====================================================|        |
     |    |                 |               |   (git fetch)      |        |
     |    |                 |               |<<==================|        |
     |                                              |  |                  |
     |                                              |  |                  |
     +----------------------------------------------+  +------------------+
```


## Afficher la version de Git
```Bash
git --version
```

## Créer un nouveau dépôt Git
```Bash
git init
```

## Définir les informations globales
```Bash
git config --global user.email "dossantosjdf@gmail.com"
git config --global user.name "DOSSANTOSDaniel"
```

## Ajouter un fichier à l'index
```Bash
git add <fichiers>
```

## Copier un projet à partir d'un dépôt distant
```Bash
git clone [url]
```

## Afficher l'état d'un projet
```Bash
git status
```

## Copier les modifications sur le dépôt local
```Bash
git commit -m "message" -a
```

|Option|Description|
|---|---|
|-a|Ajoute les modifications au dépôt local|
|-m|Ecrit un message de commentaire.|

## Envoie les modifications du dépôt local vers la branche principale du dépôt distant
```Bash
git push origin main
```

## Effacer des fichiers
### Efface sans préserver le fichier
```Bash
git rm <fichiers>
```
* On peut utiliser l'option "--cached" pour préserver le fichier localement.
* Si le fichier a été indexé, pour le supprimer on doit utiliser l'option -f.

## Déplacer des fichiers
```Bash
git mv "nom_origine" "nom_cible"
```

## Création d’une nouvelle branche
```Bash
git branch [nom de la branche]
```

## Changer de branche
```Bash
git checkout [branche]
```

## Mise en commun entre deux branches
```Bash
git merge [branch]
```

## Récupèrer les modifications sur le dépôt distant
```Bash
git pull
```

## Afficher les différences avec le commit précédent
```Bash
git diff
```

## Afficher la liste des derniers commits
```Bash
git log
```

## Affiche la liste des dépôts distants liés au dépôt local
```Bash
git remote -v
```
