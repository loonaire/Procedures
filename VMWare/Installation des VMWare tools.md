# Installation des VMWare Tools

## Sous Windows
Dans VMWare, aller dans VM -> Install VMWare Tools...  
Ensuite, lorsque le cd d'installation est prêt, aller dans un explorateur de fichier puis dans le lecteur cd et ensuite executer le fichier setup64.exe

> **NOTE**  
> Si l'on veux simplement mettre à jour les VMWare Tools (en cas de mise à jour de VMWare par exemple), il faut executer le fichier VMWareToolsUpgrader.exe





---
## Sous Linux
Il y a 2 manières:
### 1. Via le paquet apt open-vm-tools (recommandé):

En mode root (su -) ou via sudo:
```
# apt install open-vm-tools
```

### 2. Via le cd vmware:

Dans VMWare, aller dans VM -> Install VMWare Tools...  
Puis, dans la machine virtuelle:  
Si le cd n'est pas monté automatiquement:
```
# mount /dev/cdrom0 /mnt
```
On extrait l'archive à la racine
```
# tar -xzvf /media/cdrom/VMWareTools-10.3.21-14772444.tar.gz ~
```
On va dans le dossier extrait:
```
# cd vmware-tools-distrib
# ./vmaware-install.pl
```