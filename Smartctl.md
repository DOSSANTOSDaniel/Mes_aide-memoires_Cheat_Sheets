# Smartctl

Smartmontools est un paquet regroupant plusieurs outils dont smartctl qui permet de surveiller l'état d’un disque dur.

## Installation du paquet smartmontools
```Bash
apt-get install smartmontools
```

## Scanner le système à la recherche d’un périphérique
```Bash
smartctl --scan
```

## Active le protocole smart sur un disque
```Bash
smartctl -s on /dev/sdX
```

## Afficher toutes les informations Smart du périphérique
```Bash
smartctl --all /dev/sdX
```

## Affiche toutes les informations Smart et non Smart du périphérique:
```Bash
smartctl --xall /dev/sdX
```

## Affiche seulement le statut de santé du disque
```Bash
smartctl --health /dev/sdX
```

## Affiche les différentes mesures constructeur
```Bash
smartctl --attributes /dev/sdX
```

## Afficher le résumé des information sur le disque
```bash
sudo smartctl --info /dev/sdX
```

## Test complet d’un disque
### Deux options possibles
* `--test long` : Test approfondi.
* `--test short` : Test rapide.

```Bash
smartctl /dev/sdX --test long
```

## Afficher le résultat du test
```Bash
smartctl -l selftest /dev/sdX
```

## Affiche le statu des testes et autres informations
```Bash
smartctl --capabilities /dev/sdX
```