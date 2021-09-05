# Activer le Vérouillage numérique au démarrage de l'ordinateur

Dans certains cas ainsi que sur les machines virtuelles, le vérouillage numérique ne s'allume pas automatiquement au démarrage de windows.
Il suffit de modifier 2 clés de registre.
La première dans:
```
[HKEY_USERS\.DEFAULT\Control Panel\Keyboard]
```
Il faut mettre la clé "InitialKeyboardIndicators" comme valeur "2"

Il faut faire pareil avec la même clé qui se trouve dans:
```
[HKEY_CURRENT_USER\Control Panel\Keyboard]
```


Un fichier reg qui patch directement le registre est disponible au téléchargement [ici](https://raw.githubusercontent.com/loonaire/TSSR-procedures/main/Windows/verrnum.reg)
