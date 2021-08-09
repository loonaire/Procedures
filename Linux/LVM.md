# LVM

Note: les commandes sont a peu près les mêmes, en dehors du début qui est : pv, vg ou lv
vgdisplay, lvdisplay, pvdisplay

## 1. Etendre un volume
On utilise la commande lvextend. Pour voir les groupes de volumes et les volumes, on utilise vgdisplay et lvdisplay.

Pour étendre un volume:
```
lvextend /dev/nomgroupevolume/volume [-L X]
```
> l'option peux prendre en paramètre -L:  
> si X = valeur: le volume prendra la taille indiquée par X  
> si X = +valeur : la taille du volume sera augmentée de valeur  
> On peux utiliser les alias de taille M G T  
> si -L n'est pas précisé, prend toute la place disponible


---
## 2. Gérer les volumes
1. On commence par verifier dans /dev que notre disque est présent avec ls /dev
2. faire un fdisk /dev/sdX
   1. appuyer sur n puis choisir le type de partition (primaire ou étendue)
   2. appuyer sur t puis choisir le type voulu (8e pour LVM Linux)
   3. appuyer sur w pour sauvegarder et quitter

3. Integrer une partition à un groupe de volume
```
vgextend nomGrpVol /dev/sdXY
```
> X est la lettre du disque  
> Y est la numero de la partition du disque  

4. Crée un volume 
```
lvcreate -n nomDuVolume -L size nomGrpVol
```
> size = taille du volume souhaité, M G T pour mettre en mega, giga, tera  

5. Le formater
Il faut utiliser la commande:
```
mkfs.nomDuSystèmeDeFichier /dev/nomGrpVol/nomVol -L NomDuSystèmeDeFichierFormaté
```
