# Commandes CISCO
## Configuration du nom d’un routeur ou commutateur
```
enable
configure terminal
hostname 'nom du routeur'
```

## Configuration du mot de passe d’un routeur ou commutateur.
```
enable
configure terminal
enable secret 'mot de passe'
```

## Bloque la résolution de noms des commandes inconnues.
```
enable
configure terminal
no ip domain-lookup
```

## Les bannières
Il y a 3 types de bannières :
1. "MOTD" quand un utilisateur se connecte au routeur (message du jour).
2. "Connection" s’affiche avant l’invite d’authentification.
3. "Exec" quand un utilisateur se connecte via telnet.

Exemple :
```
enable
configure terminal
banner motd "Bonjour"
```

## Mot de passe pour les connexions
### Pour les connexions console
```
enable
configure terminal
line console 0
password ‘pass’
```

### Pour les connexions VTY
```
enable
configure terminal
line VTY 0
password ‘pass’
```
* Autres types de connexions, aux, tty.

## Enregistrement de la configuration en mémoire NVRAM
Il y a deux types de configurations :
1. startup-config, configuration utilisée au démarrage.
2. running-config, configuration courante, en cours d’utilisation.

### Affichage de la configuration de démarrage
```
enable
show startup-config
```

### Affichage de la configuration en cours
```
enable
show running-config
```

### Enregistrement de la configuration actuelle vers la configuration de démarrage
```
enable
copy running-config startup-config
```
* Autres raccourcis pour la commande `copy running-config startup-config` : `co ru st`, `write` et `wr`.

## Supprimer la configuration de démarrage (startup-config) 
```
enable
write erase
```

## Redémarrer le routeur ou commutateur
```
reload
```

## Afficher la table de routage
```
show ip route
show ipv6 route
```

## Configuration d’une route statique
```
ip route "network" "masque" {addrese|interface} [ad]
```

|Option|Description|
|---|---|
|"network"|Réseau à joindre.|
|"masque"|Masque du réseau à joindre.|
|{addrese|Adresse du prochain routeur directement connecté pour atteindre le réseau cible.|
|interface}|Interface réseau du prochain routeur directement connecté pour atteindre le réseau cible.|
|[ad]|La distance administrative est la fonctionnalité que les routeurs utilisent afin de sélectionner le meilleur chemin quand il y a deux routes ou plus vers la même destination.|

## Enregistre la configuration en cours dans un fichier
```
enable
copy running-config flash
```
* flash : Mémoire en cours d’utilisation.

## Remise à zéro simple
```
enable
erase startup-config
reload
```

## Afficher la configuration des interfaces réseau
```
show ip interface brief
```

## Configuration d’une route par défaut
```
enable
configure terminal
ip route 0.0.0.0 0.0.0.0 "interface"
```

## Remise en zéro total
### Supprime le fichier des bases de données des Vlans
```
delete flash:vlan.dat
```

### Supprimer la mémoire vive non volatile (NVRAM) 
```
erase startup-config
```

### Redémarrer le routeur ou commutateur 
```
reload
```

## La différence entre enable secret et enable password
```
enable password 'pass'
```
* Ici le mot de passe n’est pas chiffré, il est stocké en clair.

```
enable secret 'pass'
```
* Ici le mot de passe est chiffré avec MD5.

## Affiche la configuration d’un VLAN
```
show interface vlan "numéro"
```

## Configuration d’une interface VLAN
```
enable
configure terminal
interface vlan 1
ip address 192.168.1.5 255.255.255.0
no shutdown
```

## Configuration d’une passerelle réseau
```
ip default-gateway 192.168.1.1
```