
# Changer l'éditeur de texte par défaut et gestion des programmes par défaut

## Valide pour les distributions Debian et dérivées

http://manpages.ubuntu.com/manpages/trusty/fr/man8/update-alternatives.8.html


update-alternatives permet d'acceder aux liens du système


Afficher les éditeurs disponibles:
```
# update-alternatives --list editor
```

modifier l'éditeur par défaut:
```
# update-alternatives --config editor
```


---
## Valide pour tous les systèmes linux

On peux également changer l'editeur par défaut en passant par la variable $EDITOR, il suffit de remplacer le dernier mot par le nom de l'editeur que l'on veux utiliser.
```
# EDITOR = "chemin de l'editeur a utiliser"
```
