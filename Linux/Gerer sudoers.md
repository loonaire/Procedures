# Afficher et gérer la liste des utilisateurs qui peuvent passer en root

Pour afficher le dossier qui gère les sudoers, il faut taper la commande:
```
visudo
```
> Cette commande ouvre la configuration du fichier avec l'éditeur par défaut choisi par l'utilisateur

Pour ajouter un utilisateur, ajouter une ligne du type:
```
utilisateur    ALL=(ALL) ALL
```
On peux faire la même chose avec un groupe:
```
%nomgroupe ALL=(ALL) ALL
```

On peux ajouter des lignes de ce genre dans la zone avec les ligne qui commencent par defaults:
```
# Pour utiliser le mot de passe root au lieu du mot de passe de l'utilisateur
Defaults rootpw 

# Autoriser un utilisateur a passer en root sans utiliser de mot de passe (A EVITER D'UTILISER AILLEURS QUE SUR DES MACHINES PERSONNELLES)
Defaults:nomutilisateur !authenticate
```




https://www.linuxtricks.fr/wiki/sudo-utiliser-et-parametrer-sudoers  
https://www.security-helpzone.com/2019/09/21/linux-ajouter-un-utilisateur-dans-le-fichier-sudoers/