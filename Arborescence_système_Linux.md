
# Structure des répertoires sous Linux

|Dossier|Description|
|---|---|
|**/**|Dossier racine du système.|
|**/bin -> usr/bin**|Contient les programmes et commandes de base du système.|
|**/boot**|Chargeur d'amorçage(noyau, grub, initrd).|
|**/cdrom**|Point de montage pour les CDROMs (obsolète).|
|**/dev**|Liens vers des périphériques (disques dur, clé USB...), ce sont des fichiers spéciaux d'accès au matériel.|
|**/efi**|Point de montage pour la partition système EFI (ESP), /efi remplace le point de montage ESP /boot/efi.|
|**/etc**|Fichiers de configuration des applications et services installés.|
|**/home**|Contient les répertoires personnels des utilisateurs normaux.|
|**/initrd.img**|Initial RAM disk (initrd ou Initramfs) est un système de fichiers qui est monté au démarrage du système quand le système de fichiers principale est indisponible.|
|**/lib -> usr/lib**|Bibliothèques partagées essentielles pour le démarrage du système et pour faire fonctionner les commandes et applications principales contenues dans /bin et /sbin.|
|**/lib32 -> usr/lib32**|Bibliothèques partagées pour les binaires au format 32 bits.|
|**/lib64 -> usr/lib64**|Bibliothèques partagées pour les binaires au format 64 bits.|
|**/libx32 -> usr/libx32**|Bibliothèques partagées pour les binaires au format x32 ABI.|
|**/lost+found**|Contient les fichiers qui ont été supprimés ou perdus pendant des défaillances.|
|**/media**|Contient les points de montages des partitions supplémentaires de l'ordinateur et des médias amovibles.|
|**/mnt**|Contient les points de montage pour les systèmes de fichiers externes montés temporairement.|
|**/opt**|Emplacement pour les logiciels installées manuellement par les sources.|
|**/proc**|Système de fichiers virtuel contenant des informations concernant le noyau et les processus.|
|**/root**|Répertoire personnel de root (optionnel).|
|**/run**|Informations décrivant le système depuis son démarrage.|
|**/sbin -> usr/sbin**|Contient des applications et commandes indispensables au démarrage du système, ne sont généralement pas exécuté par les utilisateurs normaux.|
|**/snap**|Point de montage pour les fichiers des applications snap.|
|**/srv**|Contient des données spécifiques aux serveurs mis en place sur le système.|
|**/swapfile ou /swap.img**|Fichier d'échange permettant d'aider la mémoire RAM quand celle-ci est saturée.|
|**/sys**|Point de montage d'un système de fichiers virtuel(sysfs) permettant de fournir des informations sur le noyau et les composants matériel.|
|**/tmp**|Point de montage d'un système de fichiers(tmpfs), contient des fichiers et répertoires temporaires issus des processus en cours d’exécution, il est accessible à tous les utilisateurs.|
|**/usr**|Contient des des applications et leurs configurations appartenant aux utilisateurs normaux du système.|
|**/var**|Prévu pour tous les fichiers variables, les fichiers d'informations sur les services en cours de fonctionnement, sur les logiciels installés, les journaux système ...|
|**/vmlinuz**|Image compressée du noyau Linux, elle est capable de charger le système d’exploitation en mémoire afin que l’ordinateur devienne utilisable et que les programmes et applications puissent être exécutés.|
