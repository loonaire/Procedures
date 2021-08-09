
# Partionnement des disque:

## 1. En commande

Obtenir des informations sur un disque:
```
# fdisk -l /dev/sdX
```
>**INFORMATIONS UTILES**  
> m affiche l'aide   
> p affiche les détailes des partitions crées

**Formater un disque:**
1. On entre dans fdisk:
```
# fdisk /dev/sdX
```
2. Dans fdisk, on appuie sur n pour crée une partition
3. Ensuite on choisi le type de partition: primaire (p) ou étendue (e)
4. On laisse le secteur de début de la partition par défaut (sauf si demandé à un endroit précis)
5. on indique la taille de la partition:
   1. laisser vide = taille par défaut = maximum de l'espace du disque
   2. +X = augmente la taille de X (on peux mettre M G T après la valeur pour simplifier la saisie en Mo ou Go ou To)
6. Avec t, on indique le type de partition de la partition (8e pour LVM Linux)
7. On répète avec le nombre de partition à faire
8. on appui sur w pour sauvegarde et quitter

**Formater une parition**
Pour formater une partition on utilise la commande mkfs:
```
# mkfs.SYSTEMEDEFICHIER /dev/sdXY
```
> SYSTEMDEFICHIER correspond au systèm de fichier à utiliser (ext4, xfs, fat32,...)  
> /dev/sdXY correspond au disque partionner à utiliser, X = lettre du lecteur, Y = numéro de la partition du lecteur  
> Le paramètre -L "nom du volume" permet de nommer le système de fichier