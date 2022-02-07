# Le calcul de masque de sous réseaux

## 1. Calcul pour le cas ou on veux juste le nombre de sous réseaux

A partir d'une adresse IP: XXX.XXX.XXX.XXX/YY où YY est le CIDR du réseau.
Ensuite on prend la puissance de 2 supérieur à YY la plus proche, à partir de cette puissance de 2, on ajoute la puissance de 2 à YY.  

## 2. Calcul pour le cas ou l'on veux un masque de sous réseaux avec un nombre d'hotes

A partir d'une adresse IP XXX.XXX.XXX.XXX/YY et d'un nombre d'hote ainsi qu'un nombre de sous réseaux définis.  
On obtiens le masque d'un sous réseau en faisant: 32 - (puissance de 2 supérieure au nombre d'hote la plus proche)  
Pour obtenir le masque du réseau, on fait: 32 - (puissande de 2 supérieure au nombre d'hote * nombre sous réseaux la plus proche)  

## 3. Calcul de la valeur d'un sous réseau

Prend l'octet du masque qui n'est pas a 255 puis pour chaque bit de l'octet qui est a 0, on ajoute la valeur correspondante a la puissance de 2 du nombre de bit a 0

Autre méthode:  
On prend le masque puis on soustrait le nombre d'octet supérieur au masque (par exemple pour 19, on prend 24-19 = 5)
Ensuite, on prend la puissance de la valeur obtenue pour connaitre le saut d'adresse (par exemple: 2^5 = 32 donc les plages iront de 32 en 32)


## 3. Liens utiles

[https://www.faidherbe.org/tutoriel/ip.htm](https://www.faidherbe.org/tutoriel/ip.htm)
[https://www.sebastienadam.be/ipcalculator/](https://www.sebastienadam.be/ipcalculator/)