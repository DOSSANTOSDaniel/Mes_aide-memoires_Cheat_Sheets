## Interface en ligne de commande Linux

|Raccourcis|Description|
|---|---|
|<kbd>Tab</kbd>|Auto Complétion.|
|<kbd>Ctrl</kbd>+<kbd>l</kbd> ou `clear`|Efface l'écran.|
|<kbd>Ctrl</kbd>+<kbd>d</kbd>|Quitter le terminal agit de la même manière que la commande `exit`.|
|<kbd>Ctrl</kbd>+<kbd>e</kbd>|Aller de la position du curseur à la fin de la ligne.|
|<kbd>Ctrl</kbd>+<kbd>a</kbd>|Aller de la position du curseur au début de la ligne.|
|<kbd>Ctrl</kbd>+<kbd>f</kbd> ou <kbd>---></kbd>|Aller du curseur vers la fin de la ligne lettre par lettre.|
|<kbd>Ctrl</kbd>+<kbd>b</kbd> ou <kbd><---</kbd>|Aller du curseur vers le début de la ligne lettre par lettre.|
|<kbd>Alt</kbd>+<kbd>f</kbd> ou <kbd>Ctrl</kbd>+<kbd>---></kbd>|Déplacement de mots en mots vers la droite.|
|<kbd>Alt</kbd>+<kbd>b</kbd> ou <kbd>Ctrl</kbd>+<kbd><---</kbd>|Déplacement de mots en mots vers la gauche.|
|<kbd>Ctrl</kbd>+<kbd>w</kbd> ou <kbd>Alt</kbd>+<kbd>Backspace</kbd>|Coupe le texte de mot en mot du curseur vers la gauche.|
|<kbd>Echap</kbd>+<kbd>d</kbd>|Coupe le texte de mot en mot du curseur vers la droite.|
|<kbd>Ctrl</kbd>+<kbd>u</kbd>|Coupe tout le texte du curseur jusqu'au début de la ligne.|
|<kbd>Ctrl</kbd>+<kbd>k</kbd>|Coupe tout le texte de la position du curseur à la fin de la ligne.|
|<kbd>Alt</kbd>+<kbd>Backspace</kbd>|Couper du curseur vers le début d'un mot.|
|<kbd>Alt</kbd>+<kbd>d</kbd>|Coupe un mot à partir du curseur vers la droite.|
|<kbd>Ctrl</kbd>+<kbd>y</kbd>|Pour coller.|
|<kbd>Ctrl</kbd>+<kbd>r</kbd>|Recherche inverse de commandes dans l’historique <kbd>Ctrl</kbd>+<kbd>g</kbd> pour quitter.|
|<kbd>Ctrl</kbd>+<kbd>_</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>/</kbd>|Pour un retour en arrière (undo).|
|<kbd>Ctrl</kbd>+<kbd>s</kbd>|Permet de mettre en pause toutes les commandes à l'écran, utiliser <kbd>Ctrl</kbd>+<kbd>q</kbd> pour sortir de la pause.|
|<kbd>Ctrl</kbd>+<kbd>z</kbd>|Permet de suspendre un processus du premier plan, pour reprendre le processus taper la commande `fg`.|
|<kbd>Ctrl</kbd>+<kbd>c</kbd>|Interrompre le processus ou libérer l'invite de commande.|
|<kbd>Echap</kbd>+<kbd>u</kbd> ou <kbd>Alt</kbd>+<kbd>u</kbd>|Permet de transformer en majuscule du curseur à la fin de la ligne.|
|<kbd>Echap</kbd>+<kbd>l</kbd> ou <kbd>Alt</kbd>+<kbd>l</kbd>|Permet de transformer en minuscule du curseur à la fin de la ligne.|
|<kbd>Alt</kbd>+<kbd>$</kbd>+<kbd>$</kbd>|Afficher les variables d'environnement.|
|<kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>.</kbd>|Parcourir les derniers arguments des précédentes commandes pour les replacer dans la commande en cours.|
|<kbd>Echap</kbd>+<kbd>AltGr</kbd>+<kbd>#</kbd>|Commente la commande sur l'invite de commande et libère l'invite de commande.|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>c</kbd>|Copie du texte séléctionné.|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>v</kbd>|Coller le texte copié.|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>n</kbd>|Ouvre un nouveau terminal.|
|<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>t</kbd>|Ouvre un nouveau onglet.|
|<kbd>Ctrl</kbd>+<kbd>Fleche bas</kbd>|Basculer entre les onglets.|

---

|Variable/Commande|Description|
|---|---|
|`$_` ou `!$`|Affiche le dernier argument de la commande précédente.|
|`cd -`|Aller sur le dossier précédent.|
|`cd`|Répertoire courant de l’utilisateur courant.|
|`cd ~/<nom utilisateur>`|Aller dans le répertoire personnel de l'utilisateur.|
|`cd..`|Remonte d'un niveau.|
|`!!`|Exécuter à nouveau la commande précédente.|
