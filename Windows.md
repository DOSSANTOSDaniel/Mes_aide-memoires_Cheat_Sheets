# Commandes Windows
## Affiche toutes les interfaces réseau
```Batch
ipconfig /all
```

## Récupérer une nouvelle adresse IP
Libère la configuration IP, (DHCP).
```Batch
ipconfig /release
```

Nouvelle demande d’adresse IP, (DHCP).
```Batch
ipconfig /renew
```

## Affiche des informations relatives au système
```Batch
systeminfo
```

## Colore le texte sur le terminal
```Batch
color a
```

## Liste les tâches en cours
```Batch
tasklist
```

## Permet d’arrêter une tâche à l’aide de son PID
```Batch
Taskkill /pid xxxxx /f
```

## Affiche les connexions actives sur l’ordinateur
```Batch
netstat -an
```

## Permet de résoudre les noms de domaines en IP et vice versa
```Batch
nslookup
```

## Permet de vérifier si les fichiers systèmes de Windows ne sont pas corrompus et si oui les restaurer automatiquement
```Batch
sfc /scannow
```

## Permet de connaître l'intégrité d'un support de stockage, et répare les erreurs éventuelles
```Batch
chkdsk c: /f
```

## Permet d’afficher et de modifier la configuration du démarrage de Windows, des logiciels exécutés au lancement du système...
```Batch
Msconfig
```

## Afficher le mot de passe wifi
### Pour afficher tous les SSID
```Batch
netsh wlan show all
```

### Afficher le mot de passe
```Batch
netsh wlan show profile name="Nom SSID" key=clear
```

## Affiche le logo de Windows(Powershell)
```Powershell
get-windowsart
```

## Afficher la base des registres
```Batch
regedit
```

## Affiche toutes les interfaces réseau
```Batch
ipconfig /all
```

## Purge le cache DNS
```Batch
ipconfig /flushdns
```

## Actualise les baux DHCP et réenregistre les noms DNS
```Batch
ipconfig /registerdns
```

## Affiche le contenu du cache DNS
```Batch
ipconfig /displaydns
```

## Tâches/processus
### Lister les tâches/processus en cours
```Batch
tasklist
```

En powershell.
```Powershell
Get-Process
```

Rechercher un processus(Powershell). 
```Powershell
Get-Process | findstr “explorer”
```

### Arrêter une tâche/processus
```Batch
taskkill /pid “PID” /f
```

Stopper processus(Powershell).
```Powershell
stop-process
```

## Affiche le nom de l’utilisateur du compte courant
```Batch
hostname
```

## Affiche le nombre de sauts pour atteindre une adresse IP
```Batch
tracert "IP"
```

## Résout les noms de domaine en IP et vice versa
```Batch
nslookup
```

## Affiche les informations système
```Batch
systeminfo
```

## Affiche les lecteurs réseau locaux
```Batch
net view
```

## Affiche les informations système en mode graphique
```Batch
msinfo32
```

## Ouvre la fenêtre du moniteur de ressources
```Batch
resmon
```

## Ouvre la fenêtre de sauvegarde Windows
```Batch
sdclt
```

## Ouvre la fenêtre des fonctionnalités supplémentaires
```Batch
optionalfeatures
```

## Ouvre la fenêtre de caractères
```Batch
charmap
```

## Ouvre la fenêtre de configuration réseau
```Batch
ncpa.cpl
```

## Ouvre la fenêtre de l’outil de suppression de logiciels malveillants
```Batch
mrt
```

## Ouvre la fenêtre de configuration des périphériques
```Batch
devmgmt.msc
```

## Configuration des utilisateurs
```Batch
netplwiz
```

## Applications Windows
```Batch
appwiz.cpl
```

## Affiche la fenêtre des paramètres de contrôle Windows
```Batch
control
```

## En CMD, répare les associations de fichiers
```Batch
assoc
```

## Éteint l'ordinateur
```Batch
shutdown /s
```

## Redémarre l'ordinateur
```Batch
shutdown /r
```

## Éteint l'ordinateur de manière différée
```Batch
shutdown /s /t “seconds”
```

## Annuler le redémarrage différé
```Batch
shutdown /a
```

## Éteint l'ordinateur au bout de 500 secondes avec un message
```Batch
shutdown -s -t 500 -c “My message.”
```

## Ouvre la fenêtre de l’observateur d’événements
```Batch
eventvwr
```

## Ouvre la fenêtre du pare-feu
```Batch
firewall
```

## Combine la commande ping et tracert
```Batch
pathping
```

## Partitionnement des disques
```Batch
diskpart
```

## Affiche les partitions, (volumes)(Powershell)
### Affiche toutes les partitions.
```Batch
get-partition
```

### Affiche les volumes Windows(Powershell)
```Batch
get-volume
```

## Affiche les disques et le taux de remplissage(Powershell)
```Batch
get-disk
```

## Liste les logiciels installés
```Batch
wmic product get name
```

## Lancer une tâche en arrière-plan(Powershell)
```Powershell
Start-Job -ScriptBlock {Get-Command}
```

### Afficher les tâches en arrière plan(Powershell)
```Batch
get-job
```

## Purge et recharge la table des noms de cache distant NBT
```Batch
nbtstat -R
```

## Supprime tous les paramètres configurés par l’utilisateur, redémarrage obligatoire
```Batch
netsh int ip reset
```

## Force la mise à jour des stratégies de groupe(GPO)
```Batch
gpupdate /force
```

## Équivalent à la commande grep sous Linux
```Batch
| findstr /c "occurrence"
```

* En powershell
```Batch
| select-string "occurrence"
```

## Affiche les connexions réseau, -n pour ne pas résoudre les noms de domaine
```Batch
netstat -an
```

## Télécharge un fichier à partir d’un site web(Powershell)
```Powershell
invoke-webrequest 'URL' -outfile "$pwd\web.pdf"
```

## Affiche la table de routage
```Batch
route print
```

```Batch
netstat -r
```

## Affiche les services Windows(Powershell)
```Powershell
get-service "win*"
```

## Lance un service
```Batch
net start "sshd"
```

Lance un service(Powershell)
```Powershell
start-service -name "sshd"
```

##  Démarrage automatique d’un service(Powershell)
```Powershell
set-service -startuptype automatic -name "sshd"
```

## Nettoie l’écran(Powershell)
```Batch
clear-host
```

## Affiche la fenêtre de configuration des profils utilisateur
```Batch
SYSDM.CPL
```

## Connexion au bureau à distance
```Batch
mstx /v:192.168.1.85
```

## Affiche la fenêtre des services Windows
```Batch
services.msc
```

## Affiche l’historique des commandes(Powershell)
```Powershell
get-history
```

## Trouve la commande si installée(Powershell)
```Powershell
get-command "ssh"
```

## Aide aux commandes
```batch
"commande" /?
```

En Powershell.
```Powershell
get-help "commande"
```

## Affiche des exemples pour chaque commande
```Batch
Get-Help <la commande> -examples
```

## Informations sur les interfaces réseau(Powershell)
```Powershell
get-netipconfiguration
```

## Affiche les adresses MAC de la machine
```Batch
getmac
```

## Informations sur les cartes réseau(Powershell)
```Powershell
get-netadapter
```

## Affiche la table ARP
```Batch
arp -a
```

## Politique d’exécution des scripts (Powershell)

Affiche la politique d’exécution actuelle.
```Powershell
get-executionpolicy
```

Politique d’exécution actuelle.
```Powershell
set-executionpolicy “modes d’execution”

restricted
allsigned
remotesigned
unrestricted
bypass
```

## Affiche les alias(Powershell)
```Powershell
get-alias
```

## Créer des alias(Powershell)
```Powershell
set-alias -name datetime -value get-date
```

## Affiche le chemin réseau vers une machine
```Batch
traceroute 8.8.8.8
```

## Afficher la sortie d'une commande dans un lecteur de fichiers texte
```Batch
“commande” | more
```

## Affiche les dossiers et fichiers en arborescence
```Batch
tree
```

## Gestionnaire d’alimentation
```Batch
powercfg.cpl
```

## Change le nom de l'onglet du terminal
```Batch
title "nom"
```

## Exécution d'un cmd en tant que super administrateur(Powershell)
```Powershell
powershell "start cmd -v runAs"
```

## Cacher un fichier
```Batch
attrib +h fichier.txt
```

Rendre le fichier visible à nouveau.
```Batch
attrib -h fichier.txt
```

## Ouvrir le diagnostic de la mémoire Windows
```Batch
mdsched
```

## Chiffrer des fichiers dossiers
```Batch
cipher /e C:\Users\daniel\Fichier
```

### Déchiffrage
```Batch
cipher /d C:\Users\daniel\Fichier
```

## Compression de fichiers ou dossiers
```Batch
compact /C /S:C:\Users\daniel\Dossier
```

### Décompression
```Batch
compact /U /S:C:\Users\daniel\Dossier
```

## La commande Winget(Powershell)
Mise à jour de Windows.
```Powershell
winget source update
```

Mise à jour des logiciels de sécurité.
```Powershell
winget upgrade
```

Mise à jour des logiciels automatiquement en mode non interactif.
```Powershell
winget upgrade -h --all
```
* -h installe sans assistance.

Désinstaller une application.
```Powershell
winget list --name xxxxxxxx
```

```Powershell
winget uninstall -h --id xxxxx.xxxxxxxx
```

Lister les applications installées.
```Powershell
winget list
```

Affiche des informations sur un paquet.
```Powershell
winget show “paquet”
```

Recherche un paquet.
```Powershell
winget search “paquet”
```