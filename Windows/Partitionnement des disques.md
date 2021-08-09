# Partitionnement des disques
 
## 1. En ligne de commande

**Dans une invite de commande en mode administrateur**
```
>diskpart
```
Pour afficher les disque ou les volumes ou les partitions:
```
list disk
```
Pour selectionner un disque/volume/partition:
```
select disk
```

Pour crée une partition (il faut d'abord avoir fait un select disk sur le disque souhaiter):
```
create partition [Type] [Size]
```
> Type est le type de la partition (EFI, EXTENDED, LOGICAL, PRIMARY)  
> Size est la taille de la partition en Mo

Ensuite on formate la partition:
> la commande format va crée un volume puis luis donner le type du système de fichier souhaité  
```
format fs=systemedefichier LABEL="nomdelapartition"
```
> Le systemedefichier correspond au système de fichier de la partition (FAT32 ou NTFS pour windows)
> nomdelapartition correspond au nom que le volume aura pour l'ordinateur

Pour assigner une lettre à un volume:
```
assign letter=lettre
```

Pour étendre un volume il faut utiliser:
```
extend size=Taille disk=Disqueselectionner
```
> Taille correspond à la taille en Mo qui va être ajoutée au volume  
>  Disqueselectionner correspond au disque sur lequel la taille ajoutée sera utilisée.


## 2. En interface graphique

Il faut aller dans l'outil Gestion des des disques.

TODO Faire cette partie avec des images....


