# Commandes pratiques
## Démarrage d'une machine virtuelle en mode graphique
```bash
vboxmanage startmachine virtuelle <nom de la machine virtuelle>
```

## Démarrage d'une machine virtuelle en mode non graphique
```bash
vboxmanage startmachine virtuelle <nom de la machine virtuelle> --type headless
```

## Redémarrer une machine virtuelle
```bash
VBoxManage controlmachine virtuelle <nom de la machine virtuelle> reset
```

## Mettre une machine virtuelle en pause
```bash
VBoxManage controlmachine virtuelle "machine virtuelle" pause
```

## Sort une machine virtuelle de la pause
```bash
VBoxManage controlmachine virtuelle "machine virtuelle" resume
```

## Affiche la liste des machines virtuelles
```bash
vboxmanage list vms
```

## Affiche la liste des machines virtuelles démarrées
```bash
vboxmanage list runningvms
```

## Éteindre une machine virtuelle par simulation d'appui sur le bouton power
```bash
vboxmanage controlmachine virtuelle <nom de la machine virtuelle> acpipowerbutton
```

## Éteindre de manière forcé
```bash
VBoxManage controlmachine virtuelle <nom de la machine virtuelle> savestate
```
* Éteindre la machine virtuelle en sauvegardant son état (sans perte de données)

```bash
VBoxManage controlmachine virtuelle <nom de la machine virtuelle> poweroff
```
* Éteindre la machine virtuelle sans sauvegarder son état (perte de données)

## Affiche les différentes informations d'une machine virtuelle
```bash
vboxmanage showmachine virtuelleinfo <nom de la machine virtuelle> --details
```

## Modification de la mémoire RAM en MB, (fonctionne seulement si la machine virtuelle est éteinte et pas en état sauvegardé)
```bash
VBoxManage modifymachine virtuelle <nom de la machine virtuelle> --memory 1024
```
