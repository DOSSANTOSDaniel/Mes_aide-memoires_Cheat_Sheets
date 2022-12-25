# La syntaxe Markdown pour GitHub
## Les titres
```md
# Titre 1
## Titre 2
### Titre 3
#### Titre 4
##### Titre 5
###### Titre 6
```

# Titre 1
## Titre 2
### Titre 3
#### Titre 4
##### Titre 5
###### Titre 6

## Style de texte
```md
*Italique*
**Gras**
__Gras__
~~Barré~~
$Important$
$$Très   important$$
```

*Italique*
**Gras**
__Gras__
~~Barré~~
$Important$
$$Très important$$

## Images
```md
![Image logo google](https://www.google.fr/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png)
```

![Image logo google](https://www.google.fr/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png)

### Utiliser une image en mode référence
```md
![Image Google][image_google]

[image_google]: https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.8-ladc.gif "Logo Google !"
```

![Image Google][image_google]

[image_google]: https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.8-ladc.gif "Logo Google !"

### Une image cliquable
```md
[![icon_google](https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.8-ladc.gif)](https://google.com)
```

[![icon_google](https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.8-ladc.gif)](https://google.com)

## Les liens
### Simple lien
```md
[Youtube](https://youtube.com)
```

[Youtube](https://youtube.com)

Ou

```md
<https://tpdaniel.fr/blog/>
```

<https://tpdaniel.fr/blog/>

### Liens vers un fichier
```md
[Fichier39](dossier39/fichier39.txt)
```

[Fichier39](dossier39/fichier39.txt)

### Liens avec info bulle au passage de la souris
```md
[Fichier39](dossier39/fichier39.txt "Fichier de configuration")
```

[Fichier39](dossier39/fichier39.txt "Fichier de configuration")

### Les liens de références
#### Notes de bas de page

```md
Jai installé [Linux][linux] sur mon ordinateur portable.

[linux]: https://fr.wikipedia.org/wiki/Linux
```

Ou

```md
Jai installé [Linux] sur mon ordinateur portable.

[Linux]: https://fr.wikipedia.org/wiki/Linux

```

Jai installé [Linux][linux] sur mon ordinateur portable.

[linux]: https://fr.wikipedia.org/wiki/Linux


#### Notes de bas de page avec renvoie
```md
Ubuntu est une distribution Linux[^1] sortie le 20 octobre 2004.

[^1]: Linux est La partie noyau d'un système d'exploitation.
```

Ubuntu est une distribution Linux[^1] sortie le 20 octobre 2004.

[^1]: Linux est La partie noyau d'un système d'exploitation.

#### Liens fesant référence à une partie du texte
* On peut utiliser cela pour créer un sommaire. 

```md
$$Sommaire$$

- [La pomme](#La-pomme "La pomme")
- [La poire](#La-poire "La poire")

### La pomme
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !

### La poire
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !
```

$$Sommaire$$

- [La pomme](#La-pomme "La pomme")
- [La poire](#La-poire "La poire")

### La pomme
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !

### La poire
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !
Tux n'est pas un pingouin c'est un manchot !

## Lignes horizontales
```md
***
---
```

***
---

## Les listes
### Simple liste
```md
- Liste 1
- Liste 2
* Liste 3
```

- Liste 1
- Liste 2
* Liste 3

### Liste avec sous-éléments 
```md
* Élément 1
* Élément 3
   * Sous-élément 1
   * Sous élément 2
* Élément 2
```

* Élément 1
* Élément 3
   * Sous-élément 1
   * Sous élément 2
* Élément 2

### Liste ordonnée 
```md
1. Élément 1
2. Élément 2
   1. Sous-élément 1
   2. Sous élément 2
3. Élément 3
```

1. Élément 1
2. Élément 2
   1. Sous-élément 1
   2. Sous élément 2
3. Élément 3

## Les paragraphes
```md
Un paragraphes.
```

Un paragraphes.

## Les tableaux
```md
| Tâches | Temps |
|:--|:--|
| Le ménage | 1 heure |
| Faire à manger | 1 heure |
| Regarder une série | 22 heures |
```

| Tâches | Temps |
|:--|:--|
| Le ménage | 1 heure |
| Faire à manger | 1 heure |
| Regarder une série | 22 heures |

### Alignement du texte dans les cellules
|Alignement|Description|
|---|---|
|`:---`| à droite|
|`---:` ou `---`| à gauche|
|`:---:`| au centre|

## Les check box
```md
- [x] Tâche 1
- [ ] Tâche 2
- [x] Tâche 3
```

- [x] Tâche 1
- [ ] Tâche 2
- [x] Tâche 3

## Les citations
```md
> Nous gagnerions plus de nous laisser voir tels que nous sommes,
> que d'essayer de paraître ce que nous ne sommes pas.
```

> Nous gagnerions plus de nous laisser voir tels que nous sommes,
> que d'essayer de paraître ce que nous ne sommes pas.

## Afficher du Code
### Simple commande
```md
`ls`
```

`ls`

### Commande en une ligne
```md
``bash
apt install htop -y
``
```

``bash
apt install htop -y
``

### Bloque de code
````md
```bash
#!/bin/bash
echo "Bonjour !"
uptime
```
````

```bash
#!/bin/bash
echo "Bonjour !"
uptime
```

Liste des languages supportées : <https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers>

## Afficher des émojis
Liste d'émojis <https://www.webfx.com/tools/emoji-cheat-sheet/>

```md
:smile:

:snowman:

:floppy_disk:
```

:smile:

:snowman:

:floppy_disk:

## Représenter les touches du clavier
```html
Le raccourci permettant d'ouvrir un terminal sur Ubuntu : <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>t</kbd>.
```

Le raccourci permettant d'ouvrir un terminal sur Ubuntu : <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>t</kbd>.

## Caracteres d'echappement
Il suffit de précéder les caractères spécifiques à ignorer par des backslash \ (<kbd>AltGr</kbd>+<kbd>7</kbd>).

## Formules de Math
Utilisation du langage LaTex

```tex
$$
\begin{Bmatrix}
   a & b \\
   c & d
\end{Bmatrix}
$$
```

$$
\begin{Bmatrix}
   a & b \\
   c & d
\end{Bmatrix}
$$

Voir la syntaxe : <https://katex.org/docs/supported.html>

## Autre
Documentation Markdown : <https://spec.commonmark.org/0.30/>
