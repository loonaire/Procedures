# Gestions des sauvegardes


Il faut utiliser la commande:
```
# crontab -e [-u "nom utilisateur"]
```
> L'option -u permet de gerer les taches d'un utilisateur particulier.

#### 6.1.1.2 Sauvegarde au niveau du système
il faut éditer, en mode root le fichier ```/etc/crontab```
![](images/sauvegardeOS/1-crontab.png)

> **NOTE**
> On peux répéter une tache tout les X temps
> */2 permet de répéter toutes les 2min/2h/2jours/2mois
Il faut indiquer les heures, les jours, les mois et les jours de la semaine