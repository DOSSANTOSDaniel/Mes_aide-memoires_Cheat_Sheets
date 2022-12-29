# Tcpdump

TCPdump est un outil d’écoute du réseau, par défaut Tcpdump utilise la première interface réseau active.

## Syntaxe
```
tcpdump [options] [expression]
           |               |
           |               +---------------> Désigne le filtre (quels paquets sont capturés)
           v
Comportement de la commande
```

## Quelques options expliquées
|Option|Description|
|---|---|
|-vvv|Affichage plus verbeux.|
|-c <n>|Capturer seulement n paquets.|
|-t|N'affiche pas l'horodatage en début de ligne.|
|-D|Affiche les interfaces réseaux disponibles.|
|-A|Affiche le contenue d’un paquet.|
|-p|Passe l’interface réseau en mode "non promiscous", capture seulement les événement concernant la machine locale et pas sur tout le réseau.|
|-n|Pour éviter que tcpdump traduise les IP et port en nom de domaines.|
|-i <nom de l’interface réseau>|Permet de choisir l’interface d’écoute, par défaut tcpdump choisi la première interface activée, on peut aussi écouter sur l’ensemble de toutes les interfaces avec "any".|
|-w <fichier.pcap>|Permet d’enregistrer la capture dans un fichier pour l'analyser par Wireshark ou un autre outil d’analyse.|
|-r <fichier.pcap>|Permet de relire un fichier(pcap) pour pouvoir l’étudier.|
|-s <taille de capture d’un paquet>|Taille maximal que pourra faire un paquet capturé, mettre "0" pour pouvoir capturer la totalité des paquets peut importe leurs taille.|
|-X|Affiche les paquets en hexadécimal et ASCII, pour l’analyse de protocoles basés sur du texte.|
|-l|Mettre la ligne de sortie en mémoire tampon.|

## La commande tcpdump sans aucune option écouter sur l’ensemble du réseau.
```bash
tcpdump
```

## Affichage de la version
```bash
tcpdump --version
```

## Syntaxe des lignes de sortie
[Timestamp] [Protocol] [Src IP].[Src Port] > [Dst IP].[Dst Port]: [Flags], [Seq], [Ack], [Win Size], [Options], [Data Length]
* Chaque ligne représente la transmission d’un paquet.
* Afficher la liste des ports disponibles sur Linux : `cat /etc/services`

## Les filtres
Tcpdump utilise les Filtres de paquets Berkeley (BPF), pour filtrer les paquets capturés à l'aide de divers paramètres tels que les protocoles, les adresses IP et les ports source et de destination...
* Liste de tous les filtres disponibles(pcap-filtre) : <https://www.tcpdump.org/manpages/pcap-filter.7.html>

### Filtrage par hôte
```bash
sudo tcpdump -n host 192.168.1.1
```

```Bash
tcpdump -n -i enp1s0 host 192.168.1.21
```

### Filtrage par protocole
```bash
sudo tcpdump -n udp
```

```bash
sudo tcpdump -n proto 17
```
* Liste des protocoles : <https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers>

### Filtrage par sous réseau
```bash
sudo tcpdump -n net 192.168.1.0/24
```

### Filtrage par port
```bash
sudo tcpdump -n port 23
```

```Bash
tcpdump port ftp
```

### Filtrage par plage de port
```bash
sudo tcpdump -n portrange 110-150
```

### Filtrage par IP source et IP de destination

* Paquets provenant de 192.168.1.1
```bash
sudo tcpdump -n src host 192.168.1.1
```

* Paquets à destination de 192.168.1.1
```bash
sudo tcpdump -n dst host 192.168.1.1
```

Ecoute les paquet qui ont pour adresse de destination 192.168.1.22
```Bash
tcpdump dst 192.168.1.22
```

Ecoute les paquet qui ont pour adresse source 192.168.1.1
```Bash
tcpdump src 192.168.1.1
```

### Filtrage par port source et port de destination
```bash
sudo tcpdump -n dst port 80
```

```bash
sudo tcpdump -n src port 80
```

### Filtres avancés
* Combinaison de filtres possible à l'aide de and (&&), or (||), et not (!).

#### Capturer tout le trafic HTTP provenant de l'adresse IP 192.168.1.85
```bash
sudo tcpdump -n src 192.168.1.85 and tcp port 80
```

#### Vous pouvez également utiliser des parenthèses pour regrouper les options et créer des filtres plus complexes
```bash
sudo tcpdump -n 'host 192.168.1.185 and (tcp port 80 or tcp port 443)'
```

#### Capturer tout le trafic sauf SSH à partir d'une adresse IP source 192.168.1.85
```bash
sudo tcpdump -n src 192.168.1.85 and not dst port 22
```

#### Filtrer par machine et par port
```Bash
tcpdump -n -i eth0 'host 192.168.0.30 and (port https)'
```

#### Écoute du trafic entre deux machines
```Bash
tcpdump -n -i enp1s0 'host 192.168.1.21 and (host 192.168.1.22 or 192.168.1.35)'
```

#### Écoute de tous les paquets IP transmis entre la machine 192.168.1.22 et le réseau, sauf pour la machine 192.168.1.85
```Bash
tcpdump ip 'host 192.168.1.22 and not (host 192.168.1.85)'
```

#### Écoute sur seulement 10 paquets d'un serveur WEB et ses clients sur l’interface enp1s0
```Bash
tcpdump -vv -i enp1s0 -X port http -c 10
```

#### Capture d’une session SSH par l’interface loopback
```Bash
tcpdump -vv -i lo -XX port ssh
```

#### Capture du trafic voix RTP en temps réel
```Bash
tcpdump -nqt portrange 10000-20000
```
* Enregistrer la capture dans un fichier
```Bash
tcpdump -n -s 0 udp portrange 10000-20000 -vvv -w /tmp/fichier
```

#### Capture du trafic SIP en temps réel
```Bash
tcpdump -nqt -s 0 -A port 5060
```