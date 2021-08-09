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