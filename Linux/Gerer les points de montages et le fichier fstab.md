# Gestion des points de montages et du fichier fstab

## 1. Déplacer un dossier système vers un autre volume / partition:

**NOTE:** Mes exemples utilisent le répertoire home  
**NOTE 2:** Pour sdXY: X=lettre du lecteur, Y = n°umero de la partition du lecteur  
**NOTE 3:** Même si j'utilise un lecteur (/dev/sdXY), on peux le faire de la même manière avec un volume via /dev/mapper/nomgrpvolume-volume ou /dev/groupevolume/volume  

1. Il faut commencer par passer en mode rescue avec la commande:
```
systemctl rescue
```
> Le mode rescue permet de bloquer un maximum d'accès en écriture sur les fichiers, ainsi on s'assure que rien ne sera modifier pendant nos manipulations.

2. On crée un répertoire qui servira à transférer les fichiers de leur emplacement actuel vers le nouveau volume de leur destination:
```
mkdir /tmphome
```

3. On monte le dossier vers le nouveau volume:
```
mount /dev/sdXY /newhome
```

4. On déplace les fichiers vers le répertoire temporaire:
```
mv /home/* /newhome
```

5. Ensuite on démonte le dossier temporaire puis on le remonte dans à son nouvel emplacement
```
umount /newhome
mount /dev/sdb1 /home
```

6. Pour finir, on modifie le fichier fstab:
> **IMPORTANT**
> Pensez à faire une sauvegarde de votre fichier fstab AVANT toutes modifications, il servira si le système ne redémarre pas correctement.
> 


```
vi /etc/fstab
```
Mettre un # devant la ligne qui pointe vers le /home 

Copier la ligne (ou la crée si répertoire non lié au système) et changer l'emplacement vers la nouvelle destination du dossier.
Pour l'exemple: ``` /dev/sdXY    /home    ext4  defaults    0     2 ```

> **NOTE IMPORTANTE**  
> Si le système ne redémarre pas correctement, il s'agit du fichier fstab qui a mal été modifié et qui empêche le système de redémarrer, le problème viens d'un espace en trop ou manquant, ou un problème dans les réglages.

## 2. Ajouter un dossier non système au fstab

**NOTE:** Il faut les droits root pour modifier le fichier fstab

1. Crée le dossier qui servira de point de montage
```
mkdir pointdemontage
```

2. On ouvre le fichier fstab puis on ajoute le point de montage:
```
vi /etc/fstab
```

Ajouter une ligne du type:

/dev/sdXY      /pointdemontage      ext4  defaults    0     2

> /dev/sdXY peux être remplacé par un volume


> Après cette manipulation, personne n'a l'autorisation d'écrire dans le dossier a part root
