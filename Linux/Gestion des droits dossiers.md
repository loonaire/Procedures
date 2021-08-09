
Gérer les accès aux dossiers

Les n° de droit linux:
| r | w | x | valeur |
|:-:|:-:|:-:|:-:|
| _ | _ | x | 1 |
| _ | w | _ | 2 |
| _ | w | x | 3 |
| r | _ | _ | 4 |
| r | _ | x | 5 |
| r | w | _ | 6 |
| r | w | x | 7 |

Droits spéciaux:  
4 = SetUID =  execute un fichier avec les droits du propriétaire

2 = SetGID = execution avec les droits du groupe, il permet l'héritage des droits lors de la création de fichiers et dossiers

1 = Sticky bit = empeche le fichier d'être supprimer par quelqu'un d'autre que son propriétaire ou root

**La commande chmod:**  
Modifier les droits d'un dossier/fichier:
```
chmod SXYZ "nom du dossier/fichier"
```
> S = octet optionnel de droit spéciaux, généralement 2 ou non présent  
> X = octet de droit par le propriétaire du fichier ou dossier (compris entre 1 et 7, voir tableau au dessus)  
> Y = octet de droit par le groupe du propriétaire du fichier ou dossier (compris entre 1 et 7, voir tableau au dessus)  
> Z = octet de droit pour tous les utilisateurs qui ne sont ni le propriétaire, ni appartiennent au groupe du propriétaire du fichier ou dossier (compris entre 1 et 7, voir tableau au dessus)  
> L'option -R permet d'executer la commande de manière recursive sur l'arborescence


**La commande chown:**  
Permet de modifier le propriétaire ou le groupe propriétaire d'un fichier ou dossier.  
```
chown utilisateur:groupe répertoireOuFichier
```
Peux aussi s'utiliser seulement pour un groupe ou un utilisateur:
```
chown utilisateur répertoireOuFichier # pour un utilisateur
chown :groupe répertoireOuFichier # pour un groupe
```


**Exemple d'utilisation:**  
Supposons un dossier présent avec l'arborescence /services/commercial et on veux le rendre seulement disponible en lecture/écriture pour le groupe Commercial, le dossier a été crée par root:

1. On modifie le groupe propriétaire du dossier:
```
chown :Commercial /services/commercial 
```
2. On rend le dossier seulement accessible à root 
```
chmod -R 2770 /services/commercial
```

> Le 2 permet de rendre le dossier disponible au groupe Commercial et son héritage héritera de ses propriétés.  
> 770, on laisse l'accès en lecture / ecriture à root, on permet au groupe Commercial de tout faire sur le dossier et tout les autres utilisateurs ne pourront plus accéder au dossier.