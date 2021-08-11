# Modifier le GRUB

Pour modifier les informations du grub, il faut éditer (en mode root), le fichier /etc/default/grub

> On peux modifier plusieurs paramètres, je vais détailler pour le temps d'affichage du grub au démarrage:  
> ```
> GRUB_TIMEOUT=5
> ```
> Par défaut, la valeur est à 5.  
> 0 = passe directement sur le démarrage du système  
> -1 = il n'y a aucune limite de temps  

Il faut ensuite regénerer le fichier grub.cfg dans /boot avec la commande:
```
# grub-mkconfig -o /boot/grub/grub.cfg
```
---

On peux cacher le grub au démarrage en ajoutant (ou modifiant sur certains système) la ligne:
```
GRUB_TIMEOUT_STYLE=hidden
```
> Le mot hidden peux être remplacer par countdown 

> Commenter la ligne permet de réafficher le GRUB

Ensuite, il faut mettre à jour le GRUB avec la commande en mode root:
```
update-grub
```
