# Aide mémoire Vim

## Vim possède 4 modes de fonctionnement

1. **Le mode normal**
   
   * Permet de naviguer dans un fichier et de couper, copier ou coller du texte.

2. **Le mode d'insertion**
   
   * Permet l'édition du texte.
   * Pour entrée en mode insertion taper <kbd>i</kbd>.

3. **Le mode visuel**
   
   * Permet une sélection d'éléments du texte plus approfondie et aussi de couper, copier et coller les éléments sélectionnés.
   * Pour entrée en mode visuel taper <kbd>Ctrl</kbd>+<kbd>v</kbd> pour une sélection par bloques, taper <kbd>V</kbd> pour une sélection par lignes et  taper <kbd>v</kbd> pour une sélection par caractères.

4. **Le mode commande**
   
   * Permet d'envoyer des ordres à Vim, comme par exemple quitter le fichier, le sauvegarder, faire des substitutions... .
   * Pour entrer en mode commande, taper <kbd>:</kbd>.

**Pour sortir d'un mode taper <kbd>Echap</kbd>.**

## Afficher l'aide

- En mode commande taper `:help`.
- Pour rechercher un élément taper <kbd>/</kbd>.
- Pour suivre un lien, positionner le curseur sur le lien et taper <kbd>Ctrl</kbd>+<kbd>AltGr</kbd>+<kbd>]</kbd>.
- Pour revenir à l'emplacement initial, taper <kbd>Ctrl</kbd>+<kbd>t</kbd> ou <kbd>Ctrl</kbd>+<kbd>o</kbd>.

## Quitter Vim

| Commande | Description                                                                          |
|:-------- |:------------------------------------------------------------------------------------ |
| `:q`     | Pour quitter.                                                                        |
| `:q!`    | Forcer la sortie de Vim même s'il y a des modifications non enregistrées.            |
| `:wq`    | `w` pour enregistrer les modifications et `q` pour quitter.                          |
| `:x`     | Pour quitter en enregistrant les modifications seulement s'il y a des modifications. |

### Différence entre :wq et :x

- Avec la commande `:wq` La date de modification change toujours même si on a rien modifier.
- Avec la commande `:x` s'il n'y a aucun changement la date de modification n'est pas changée.

## Les déplacements

| Commande                                           | Description                                                                          |
|:-------------------------------------------------- |:------------------------------------------------------------------------------------ |
| <kbd>w</kbd>                                       | De mot en mot du début de ligne vers la fin de la ligne à chaque début de mot.       |
| <kbd>e</kbd>                                       | De mot en mot vers la fin de la ligne à chaque fin de mot.                           |
| <kbd>b</kbd>                                       | De mot en mot de la fin de la ligne vers le début de la ligne à chaque début de mot. |
| <kbd>^</kbd> ou <kbd>0</kbd>                       | Pour aller au début de la ligne.                                                     |
| <kbd>$</kbd>                                       | Pour aller à la fin d'une ligne.                                                     |
| <kbd>+</kbd> et <kbd>-</kbd>                       | Pour se déplacer de ligne en ligne sur chaque début de ligne.                        |
| <kbd>(</kbd> et <kbd>)</kbd>                       | Pour aller au début et en fin d'un paragraphe.                                       |
| <kbd>{</kbd> ou <kbd>}</kbd>                       | Pour aller au début et en fin d'un texte.                                            |
| <kbd>Shift</kbd>+<kbd>h</kbd>                      | Se déplacer en haut par rapport à la fenêtre active.                                 |
| <kbd>Shift</kbd>+<kbd>m</kbd>                      | Se déplacer au milieu par rapport à la fenêtre active.                               |
| <kbd>Shift</kbd>+<kbd>l</kbd>                      | Se déplacer en bas par rapport à la fenêtre active.                                  |
| <kbd>g</kbd> <kbd>g</kbd>                          | Pour aller au début du fichier.                                                      |
| <kbd>G</kbd>                                       | Pour aller à la fin du fichier.                                                      |
| `:81`                                              | Pour aller à la ligne 81.                                                            |
| <kbd>Ctrl</kbd>+<kbd>o</kbd>                       | Pour revenir à la position d'origine.                                                |
| La touche <kbd>\*</kbd> toute seule en mode normal | Permet d'aller sur la prochaine occurrence du mot sous le curseur.                   |

## Rechercher un élément

- Pour trouver les occurrences d'un mot dans un texte, placer le curseur sur le mot choisi et taper <kbd>\*</kbd> ou <kbd>AltGr</kbd>+<kbd>#</kbd> puis taper <kbd>n</kbd> ou <kbd>\*</kbd> pour voire l'occurrence suivante et <kbd>N</kbd> pour l'occurrence précédente. 
- Pour rechercher un mot dans un texte taper `/<mot>` et taper <kbd>n</kbd> pour le résultat suivant et taper <kbd>N</kbd> pour le résultat précédent.

## Actions sur le texte

| Commande                                               | Description                                                             |
|:------------------------------------------------------ |:----------------------------------------------------------------------- |
| <kbd>r</kbd>                                           | Permet de remplacer un caractère.                                       |
| <kbd>x</kbd>                                           | Coupe le caractère en dessous du curseur.                               |
| <kbd>d</kbd> <kbd>d</kbd>                              | Pour couper une ligne.                                                  |
| <kbd>d</kbd><kbd>w</kbd>                               | Pour couper un mot.                                                     |
| <kbd>d</kbd> <kbd>5</kbd> <kbd>d</kbd>                 | Pour couper 5 lignes à partir du curseur.                               |
| <kbd>y</kbd> <kbd>y</kbd>                              | Pour copier une ligne.                                                  |
| <kbd>y</kbd> <kbd>w</kbd>                              | Pour copier un mot.                                                     |
| <kbd>y</kbd> <kbd>5</kbd> <kbd>y</kbd>                 | Pour copier 5 lignes à partir du curseur.                               |
| <kbd>p</kbd>                                           | Pour coller la sélection en dessous de la ligne courante.               |
| <kbd>P</kbd>                                           | Pour coller la sélection en dessus de la ligne courante.                |
| <kbd>d</kbd> <kbd>G</kbd> ou `:1,$d` ou `:%d`          | Pour supprimer toutes les lignes d'un fichier.                          |
| <kbd>d</kbd> <kbd>$</kbd>                              | Pour supprimer ou couper à partir du curseur vers la fin de la ligne.   |
| <kbd>d</kbd> <kbd>0</kbd> ou <kbd>d</kbd> <kbd>^</kbd> | Pour supprimer ou couper à partir du curseur vers le début de la ligne. |

### Faire des actions sur plusieurs lignes en même temps

1. Se mettre en mode "VISUEL BLOC", <kbd>Ctrl</kbd>+<kbd>v</kbd>.
2. Sélectionner les caractères à modifier.
3. Se mettre en mode insertion <kbd>Shift</kbd>+<kbd>i</kbd>.
4. Saisir les caractères voulus puis appuyer sur <kbd>Echap</kbd>.

## Actions sur les fichiers

| Commande                                  | Description                                                                                                                                           |
|:----------------------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:r <nom du fichier>`                     | Ajoute le fichier à la ligne suivante, à partir de la position du curseur.                                                                            |
| `:w /chemin/`                             | Faire une copie du fichier ouvert.                                                                                                                    |
| `:r! <commande>`.                         | Pour insérer le résultat d’une commande externe à partir de la position du curseur.  **on peut utiliser l'auto-complétion pour trouver le fichier !** |
| `:e <nom du dossier>`                     | Ouvrir l'explorateur de fichiers.                                                                                                                     |
| `:Vex <nom du dossier>`                   | Divise la fenêtre en deux parties à la verticale d'un coté le fichier courant et de l'autre l'explorateur de fichiers.                                |
| `:Sex <nom du dossier>`                   | Divise la fenêtre en deux parties à l’horizontal d'un coté le fichier courant et de l'autre l'explorateur de fichiers.                                |
| `:e <nom du fichier>`                     | Pour éditer un autre fichier.                                                                                                                         |
| `:sp <nom du fichier>`                    | Ouvrir un fichier et diviser horizontalement la fenêtre courante.                                                                                     |
| `:vsp <nom du fichier>`                   | Ouvrir un fichier et diviser verticalement la fenêtre courante.                                                                                       |
| <kbd>Ctrl</kbd> <kbd>w</kbd> <kbd>w</kbd> | Pour passer d'une fenêtre à l'autre.                                                                                                                  |
| <kbd>Ctrl</kbd> <kbd>w</kbd> <kbd>q</kbd> | Pour enregistrer et fermer une fenêtre.                                                                                                               |
| <kbd>g</kbd> <kbd>f</kbd>                 | Éditer un fichier positionné sous le curseur.                                                                                                         |
| `vim -o <fichier1.txt> <fichier2.txt>`    | ouvrir 2 fichiers cote à cote, avec une division horizontale de la fenêtre.                                                                           |
| `vim -O <fichier1.txt> <fichier2.txt>`    | ouvrir 2 fichiers cote à cote, avec une division verticale de la fenêtre.                                                                             |

### Ouvrir plusieurs fichiers sans quitter Vim

1. Pour ouvrir un fichier sans avoir à fermer Vim, taper `:badd <nouveau fichier>`.
2. Pour afficher les fichiers dans le buffer, taper `:ls`.
3. Pour basculer entre les différents fichiers, taper `:b<numéro>`
4. Une autre façon de basculer vers un autre fichier :
   - Occurrence suivante, `:bn`.
   - Occurrence précédente, `:bp`.

## Retour à un état ultérieur

| Commande                                                               | Description                                              |
|:---------------------------------------------------------------------- |:-------------------------------------------------------- |
| <kbd>U</kbd>                                                           | Annule toutes les dernières modifications sur une ligne. |
| <kbd>u</kbd> ou `:earlier` ou `:later` ou <kbd>Ctrl</kbd>+<kbd>r</kbd> | Annule la dernière action.                               |
| `:earlier 2h`                                                          | Revenir en arrière de 2 heures.                          |

## Insertion de texte

| Commande                  | Description                                                                 |
|:------------------------- |:--------------------------------------------------------------------------- |
| <kbd>o</kbd>              | pour insérer du texte en dessous de la ligne courante.                      |
| <kbd>O</kbd>              | pour insérer du texte au dessus de la ligne courante.                       |
| <kbd>i</kbd>              | pour insérer du texte avant le curseur.                                     |
| <kbd>I</kbd>              | pour insérer du texte avant le premier caractère de la ligne courante.      |
| <kbd>a</kbd>              | pour insérer du texte après le curseur.                                     |
| <kbd>A</kbd>              | pour insérer du texte a la fin de la ligne courante.                        |
| <kbd>c</kbd>              | efface la ligne courante et nous met en mode insertion.                     |
| <kbd>c</kbd> <kbd>e</kbd> | Pour effacer un mot après le curseur puis se mettre dans le mode insertion. |

## Substitutions de texte

Exemple : remplacer jean par daniel.
| Commande | Description |
|:---|:---|
| `:s/jean/daniel/` | Pour remplacer la première occurrence de la ligne ou se trouve le curseur. |
| `:s/jean/daniel/g` | Pour remplacer toutes les occurrences de la ligne ou se trouve le curseur. |
| `:<numéro de ligne, début>,<numéro de ligne, fin>s/jean/daniel/g` | Pour remplace toutes les occurrences sur une plage de lignes. |
| `:5,16s/jean/daniel/g` | Pour remplacer toutes les occurrences de la ligne 5 à la ligne 16. |
| `:%s/jean/daniel/g` | Pour remplace toutes les occurrences dans tout le fichier. |
| `:%s/jean/daniel/gc` | Pour remplace toutes les occurrences dans tout le fichier mais de façon interactive. |

## Numéro de ligne

* Numéro de la ligne ou se trouve le curseur <kbd>Ctrl</kbd>+<kbd>G</kbd>.
* Pour afficher les numéros de ligne sur un fichier, taper `:set number` ou `:set nu`.

## Créer un fichier chiffré

1. `vim -x fichier.txt`
2. Indiquer une clé de chiffrement puis valider.

## Correcteur d'orthographe

1. Téléchargement des fichiers de langue.

```bash
mkdir -p ~/.vim/spell

cd ~/.vim/spell

wget http://ftp.vim.org/vim/runtime/spell/fr.latin1.spl

wget http://ftp.vim.org/vim/runtime/spell/fr.latin1.sug

wget http://ftp.vim.org/vim/runtime/spell/fr.utf-8.spl

wget http://ftp.vim.org/vim/runtime/spell/fr.utf-8.sug
```

2. Activation de la correction.

Ouvrir un fichier avec Vim et taper, `:setlocal spell spelllang=fr`

* Les mots mal orthographiés sont surlignés en rouge.

| Commande                               | Description                           |
|:-------------------------------------- |:------------------------------------- |
| <kbd>z</kbd> <kbd>g</kbd>              | Ajoute un mot au dictionnaire.        |
| <kbd>z</kbd> <kbd>G</kbd>              | Ajoute un mot au dictionnaire global. |
| <kbd>z</kbd> <kbd>u</kbd> <kbd>g</kbd> | Enlève le mot précédemment mit.       |
| <kbd>z</kbd> <kbd>=</kbd>              | Affiche la liste des mots proposés.   |
| <kbd>]</kbd> <kbd>s</kbd>              | Va au prochain mot mal orthographié.  |
| <kbd>[</kbd> <kbd>s</kbd>              | Va au précédent mot mal orthographié. |

## Autres commandes Vim

| Commande                     | Description                                                                                   |
|:---------------------------- |:--------------------------------------------------------------------------------------------- |
| `: + flèches` ou `:history`  | Pour afficher l'historique.                                                                   |
| `:!<commande>`               | Pour lancer une commande externe à Vim.                                                       |
| `:w !sudo tee %`             | Si on ouvre un fichier et qu'on l'édite alors que nous n'avons pas les droits.                |
| <kbd>z</kbd> <kbd>z</kbd>    | Centrer la fenêtre active par rapport à la position du curseur.                               |
| `:!.`                        | Répète la dernière commande.                                                                  |
| <kbd>Ctrl</kbd>+<kbd>p</kbd> | Complétion automatique de mots, cela fonction que avec les mots déjà présent dans le fichier. |
| `vim +5 toto.txt`            | Ouvrir un fichier et se positionner sur une ligne en particulier.                             |

## Autres raccourcis en mode insertion

| Raccourci                                                                     | Description                                                                                                     |
| ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| <kbd>Ctrl</kbd>+<kbd>n/p</kbd>                                                | Permet l'auto-complétion  de mots.                                                                              |
| <kbd>Ctrl</kbd>+<kbd>h</kbd>                                                  | Efface du curseur vers le début de la phrase.                                                                   |
| <kbd>Ctrl</kbd>+<kbd>k</kbd>                                                  | Permet d'insérer les noms des touches du clavier.                                                               |
| <kbd>Ctrl</kbd>+<kbd>+</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>+</kbd> | Zoomer.                                                                                                         |
| <kbd>Ctrl</kbd>+<kbd>-</kbd>                                                  | Dézoomer.                                                                                                       |
| <kbd>Ctrl</kbd>+<kbd>0</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>0</kbd> | Retour à la taille d'origine.                                                                                   |
| <kbd>Ctrl</kbd>+<kbd>w</kbd>                                                  | Coupe de mots en mots.                                                                                          |
| <kbd>Ctrl</kbd>+<kbd>r</kbd>+<kbd>x</kbd>                                     | Lister les entrées du presse papier, :reg, puis coller la ligne correspondant au registre x  avec le raccourci. |
| <kbd>Win</kbd>+<kbd>$</kbd>                                                   | Insertion d'emojis.                                                                                             |
| <kbd>Alt</kbd>+<kbd>$</kbd>                                                   | Aller à la fin de la ligne.                                                                                     |
| <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>0</kbd>                                  | Aller au début de la ligne.                                                                                     |
| <kbd>Alt</kbd>+<kbd>*</kbd>                                                   | Rechercher un mot correspondant au mot sous le curseur.                                                         |

## Le copier coller, registres Vim et presse-papiers système

Le but ici est de pouvoir faire un copier coller à partir du presse-papiers système vers un fichier ouvert avec Vim et vise versa.

Le presse-papiers sous Vim contient plusieurs registres et chaque registre est comme un presse-papier, les presses-papier de Vim ne sont pas reliés au presse-papier du système par défaut.

Pour afficher les presses-papier de Vim (registres), taper `:register ou :reg`.

Chaque ligne des registres correspond à un registre, on va utiliser le registre "+" ou "*" car ces deux registres sont associés au presse-papier de Linux ou de Windows.

**Premièrement pour que cela fonctionne il faut installer le paquet `vim-gtk3` sur votre système!**

### De Vim vers le système

Dans l'exemple suivant, on va copier une ligne de texte à partir de Vim puis on va coller cette ligne sur un éditeur de texte graphique sur notre système.

#### Méthode 1

1. On va ouvrir un fichier avec Vim : `vim fichier.txt`.
2. On utilise la commande `:y+` pour copier la ligne courante dans le registre "+".
3. Une fois dans votre système faite un clique droit puis coller.

#### Méthode 2

1. On va ouvrir un fichier avec Vim : `vim fichier.txt`.
2. On se met en mode visuel, <kbd>Ctrl</kbd>+<kbd>v</kbd>.
3. On sélectionne la ligne voulue.
4. On copie la sélection, <kbd>"</kbd> <kbd>+</kbd> <kbd>y</kbd>.
5. Une fois dans votre système faite un clique droit puis coller ou pour coller dans Vim, taper <kbd>"</kbd> <kbd>+</kbd> <kbd>p</kbd>.

Pour copier tout le texte d'un fichier dans le registre "+" de Vim, taper `:%y+`.

### Du système vers Vim

Dans ce deuxième exemple, on va copier une ligne de texte à partir d'un éditeur de texte vers un fichier ouvert avec Vim.

1. On va ouvrir un fichier avec un éditeur de texte graphique, puis on copie une ligne.
2. On ouvre un fichier avec Vim puis on utilise la commande <kbd>"</kbd> <kbd>+</kbd> <kbd>p</kbd>.

#### Une autre méthode
Vim n'est pas toujours configuré pour utiliser le copier coller en utilisant la sourie, on peut utiliser <kbd>Ctrl</kbd>+<kbd>insert</kbd> pour coller.

## Imprimer des documents directement à partir de Vim

### Configuration de lpr sur le système

Trouver le nom de votre imprimante.

`lpstat -p -d`
ou
`lpstat -t`

```Bash
┌──[daniel👾L875-10E]-(~)
│
└─$ lpstat -p -d

printer EPSON_ET_3750_Series is idle.  enabled since mar. 28 juin 2022 07:13:09
no system default destination

┌──[daniel👾L875-10E]-(~)
│
└─$ lpstat -t

scheduler is running
no system default destination
matériel pour EPSON_ET_3750_Series : implicitclass://EPSON_ET_3750_Series/
EPSON_ET_3750_Series accepte des requêtes depuis mar. 28 juin 2022 07:13:09
printer EPSON_ET_3750_Series is idle.  enabled since mar. 28 juin 2022 07:13:09
```

Configurer l'imprimante comme imprimante par défaut, si ce n'est pas déjà le cas.

```
lpoptions -d <nom imprimante>

lpstat -p -d <nom imprimante>
```

```Bash
┌──[daniel👾L875-10E]-(~)
│
└─$ lpoptions -d EPSON_ET_3750_Series

device-uri=ipps://EPSON%20ET-3750%20Series._ipps._tcp.local/ printer-info='EPSON ET-3750 Series' printer-location printer-make-and-model='EPSON EPSON ET-3750 Series' printer-type=83890204

┌──[daniel👾L875-10E]-(~)
│
└─$ lpstat -p -d EPSON_ET_3750_Series

printer EPSON_ET_3750_Series is idle.  enabled since mar. 28 juin 2022 07:13:09
system default destination: EPSON_ET_3750_Series
```

Vérifier que l'imprimante est bien configurée

`lpq`

```Bash
┌──[daniel👾L875-10E]-(~)
│
└─$ lpq

EPSON_ET_3750_Series est prêt
no entries
```

### Lancer une impression

Après avoir configuré l'imprimante on va pouvoir imprimer des documents directement à partir de Vim, pour cela on va ouvrir un fichier avec Vim.

`vim fichier.txt`

On peut à présent lancer une impression avec la commande, `:hardcopy`.

```Bash
~                                                                                                                                                                            
~                                                                                                                                                                            
~                                                                                                                                                                            
:hardcopy
```

```Bash
~                                                                                                                                                                            
~                                                                                                                                                                            
~                                                                                                                                                                            
Tâche d'impression envoyée.  
```

Ou si on veut imprimer un autre fichier, `:hardcopy <nom fichier>`.