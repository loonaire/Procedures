
# La date et heure du système

Pour connaitre la date de l'heure de la machine:  
```
# timedatectl
```

Pour activer le ntp:
```
# timedatectl set-ntp true
```

---

Pour afficher l'heure et la date de l'horloge matérielle
```
# hwlock
```
Pour le synchroniser: 
```
hwlock--systohc
```

---
Pour Afficher l'heure du système:
```
# date
```