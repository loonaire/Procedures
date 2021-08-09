# Gestion des utilisateurs

## En ligne de commande

> **INFO IMPORTANTE** Il faut être root pour utiliser les commandes suivantes

Pour ajouter un utilisateur: 
```
# useradd -m "nomutilisateur" [-G "groupeprincipal(nom ou GID)"] [-g "groupe secondaire(nom ou GID)] [-s "emplacement du shell a utiliser"] 
```
> -m sert a crée le dossier de l'utilisateur dans /home à la création de l'utilisateur  
> -s permet de definir quel shell utilisera l'utilisateur  
> -N ne crée pas de groupe avec le nom de l'utilisateur  
> -n crée un groupe avec le nom de l'utilisateur  

Pour modifier un utilisateur:
```
# usermod "nom utilisateur" 
```
> -e permet de definir une date d'expiration (1 = desactive instantanément le compte)

> **IMPORTANT**  
> Pour le mot de passe, il faut ensuite execute la commande:
> ```
> # passwd "nomutilisateur"
> ```
> Cette méthode est la plus simple sans utiliser de script,
> l'argument -e permet de gerer l'expiration du mot de passe


Pour crée un groupe:
```
# groupadd "nomdugroupe"
```
> les GID apparaissent dans /etc/gshadow

Ajouter un membre à un groupe:
```
# adduser "nom du groupe" "nom utilisateur"
```
> On peux ajouter plusieurs membres en même temps



Pour plus d'information, voir: [lien de la documentation debian](https://wiki.debian-fr.xyz/Commandes_utilisateurs_et_groupes).