# Gestion de paquets avec apt

> Pour plus d'info sur apt et apt-get:  
> https://itsfoss.com/apt-vs-apt-get-difference/  
> https://www.malekal.com/apt-installer-mise-a-jour-paquet-distribution-debian-ubuntu-mint/ 

## 1. Désactiver les dépots de sources cdrom:
**En mode root**
```
> vi -c "%s/^deb cdrom/#deb cdrom/" /etc/apt/sources.list
```

Sinon, on peux ouvrir directement le fichier sources.list avec la commande:
```
> apt edit-sources
```
sources.list sera ouvert avec l'editeur de texte par défaut, il restera juste à mettre un # devant les lignes qui commences par deb cdrom





## 2. Mettre à jour les paquets:
**En mode root**
Mettre à jour les version la liste des paquets disponible dans les dépots:
```
# apt update
```
Ensuite on peux mettre à jour les paquets:
```
# apt upgrade
```
Pour chercher un paquet:
```
# apt search "terme à chercher"
```
> **NOTE**  
> Ajouter -n après le mot search permet de filtrer pour que le résultat de la recherche ne soit que dans les noms de paquets
Pour installer un paquet:
```
# apt install "nom du paquet"
```
Pour desinstaller un paquet:
```
# apt remove "nom du paquet"
```
Pour supprimer un paquet ainsi que ses fichiers de configuration:
```
# apt purge "nom du paquet"
```

Pour supprimer un paquet et retirer toutes ses dépendances:
```
# apt autoremove --purge "nom du paquet"
```

Télécharger seulement le paquet, sans l'installer:
```
# apt download "nom du paquet"
```
> Pour installer le paquet il l'installer avec dpkg:
> ```
> dpkg -i "nom du paquet"
> ```  
> Note: il faudra aller chercher le paquet avec la commande find.


Pour mettre à niveau toute la distribution linux:
```
# apt full-upgrade
```


# 3. Supplément dpkg

dpkg est un outil comme apt sauf qu'il est local à l'ordinateur, pour installer un logiciel il faut utiliser la commande:
```
# dpkg -i "nom du paquet.deb"
```