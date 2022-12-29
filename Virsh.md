# Aide mémoire
## Gestion des machines virtuelles avec virsh
* Virtual shell "virsh", est basé sur l'api libvirt.

|Commande|Description|
|---|---|
|virsh list|Liste les machines virtuelles en fonctionnement.|
|virsh list --all|Liste les machines virtuelles en fonctionnement ou non.|
|virsh shutdown "nom de la machine virtuelle"|Éteint une machine virtuelle.|
|virsh start "nom de la machine virtuelle"|Démarre une machine virtuelle.|
|virsh suspend "nom de la machine virtuelle"|Suspend une machine virtuelle.|
|virsh resume "nom de la machine virtuelle"|Démarre une machine virtuelle qui est en suspend.|
|virsh reboot "nom de la machine virtuelle"|Redémarre une machine virtuelle.|
|virsh destroy "nom de la machine virtuelle"|Supprime une machine virtuelle.|
|virsh undefine "nom de la machine virtuelle"|Dés-enregistre une machine virtuelle.|

## Informations sur les machine virtuelles
|Commande|Description|
|---|---|
|virsh vcpuinfo "nom de la machine virtuelle"|Informations sur le CPU d'une machine virtuelle.|
|virsh domid "nom de la machine virtuelle"|Affiche l'ID d'une machine virtuelle.|
|virsh domuuid "nom de la machine virtuelle"|Affiche l'UUID d'une machine virtuelle.|
|virsh dominfo "nom de la machine virtuelle"|Affiche les informations concernant une machine virtuelle en particulier.|
|virsh domstate "nom de la machine virtuelle"|Affiche l'état d'une machine virtuelle.|
|virsh dumpxml "nom de la machine virtuelle"|Affiche la configuration d'une machine virtuelle au format xml.|

## Ajouter et enlever des ressources
Il y a deux manières de configurer une machine virtuelle soit on passe par la commande virsh soit on peut modifier directement le fichier de configuration au format xml.

* Toujours éteindre la machine virtuelle avant d'ajouter ou d'enlever des ressources !

|Commande|Description|
|---|---|
|virsh setvcpus "nom de la machine virtuelle" 4 –config|Augmente le nombre de CPU's virtuels.|
|virsh setmem "nom de la machine virtuelle" 4G –config|Augmente la taille de la mémoire RAM.|
|virsh edit "nom de la machine virtuelle"|Édite la configuration xml de la machine virtuelle.|
|virsh dumpxml "nom de la machine virtuelle" > /home/daniel/machine virtuelle.xml|Récupére la configuration xml de la machine virtuelle puis là modifie, "vim /home/daniel/machine virtuelle.xml".|
|virsh define /home/daniel/machine virtuelle.xml|Applique la configuration à une machine virtuelle.|
