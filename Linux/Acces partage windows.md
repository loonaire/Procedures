# Accéder à un partage de fichier windows depuis Debian 10


[Lien vers le wiki ubuntu](https://doc.ubuntu-fr.org/tutoriel/monterpartagewindows)


1. Il faut commencer par installer les paquets cifs et samba avec apt:
```
# apt install cifs-utils samba
```

2. On verifie que l'on pourra correctement accéder à la ressource distante:
```
# mkdir /media/Partage
# mount -t cifs -o username=NOMUTILISATEUR,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 //IPDISTANTE/CHEMINDUPARTAGE /CHEMINDEMONTAGEDUPARTAGA
```

On crée ensuite le fichier .smbcredentials dans le home de l'utilisateur qui utilisera le partage.  
Voici le contenu du fichier:  
```
username=USERNAMEWINDOWS
password=PASSWORDUSERNAMEWINDOWS
domain=DOMAINE
```

> Il est preferable de modifier les accès au fichier .smbcredentials pour que personne ne puisse récuperer le mot de passe, il faut utiliser la commande:
> ```
> # chmod 600 ~/.smbcredentials
> ```


On edite ensuite le fichier fstab:  
```
# vim /etc/fstab
```
On ajouter la ligne:
```
//IP/CHEMINDUPARTAGE   /CHEMINDUMONTAGEDUPARTAGE cifs  uid=NOMUTILISATEURLINUX,dir_mode=0777,file_mode=0777,credentials=/root/.smbcredentials,iocharset=utf8 0 0
```
> Dans le cas ou il y a un espace dans le chemin, il faut utiliser \040 (espace en octal) au lieu du caractère espace

> **ATTENTION**  
> Veiller à bien penser aux autorisations lectures/écritures pour l'utilisateur windows