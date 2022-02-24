# Gestion du reseau


## 1. La commande ip:

- Afficher l'adresse ip des cartes réseaux
```
# ip a 
# ip address 
```
- Afficher la route du réseau utilisée
```
# ip r
# ip route
```
- Afficher les cartes réseaux connectées à la machine:
```
# ip link
```

## 2. Changer le nom NETBios de la machine

Il faut éditer le fichier ``` /etc/hostname``` et le fichier ``` /etc/hosts``` en root.

- Manipulations détaillées:

1. On modifie le fichier hostname
```
sudo vi /etc/hostname 
```
Il faut remplacer la ligne du fichier par le nouveau nom de l'ordinateur puis enregistrer et quitter
2. On modifie le fichier hosts:
```
sudo vi /etc/hosts
```
Il faut modifier la ligne:
```
127.0.1.1   nomDeLaMachine
```
Par:
```
127.0.1.1   nouveauNomDeLaMachine
```

## 3. Configuration mannuelle de l'ip:
Il faut éditer le fichier : ``` /etc/network/interfaces ```

- Détails:  
  1. Il faut d'abord récupérer le nom de la carte réseau qui verra ses paramètres modifiés avec la commande:
    ```
    # ip link
    ```
    Exemple:
    ![](images/configuration%20reseau/1.iplink.png)

    > - La carte n° 1 est nommée lo, il s'agit d'une carte qui sert pour le loop et elle est préconfigurée dans le fichier interfaces.  
    > - Ici, il n'y a qu'une carte réseau sur la machine, il faudra configuré la carte nommée ens33.

  2. Il faut ensuite ouvrir et éditer le fichier interfaces:
    ```
    # sudo vi /etc/network/interfaces
    ```
    Ensuite, en fonction des paramètres souhaiter, on ajoute les lignes:  
    - Pour une adresse ip avec le DHCP:
    ```
     auto eth0
     allow-hotplug eth0
     iface eth0 inet dhcp    
    ```

    - Pour une adresse ip statique:
    ```
    auto eth0
    iface eth0 inet static
        address X.X.X.X/mask
        gateway X.X.X.X
    ```
  3. Il faut enfin redémarrer le service:
    ```
    # systemctl restart networking
    ```

## 4. Configuration des DNS 

Il faut editer le fichier: ``` /etc/resolv.conf```

```
# sudo vi /etc/resolv.conf
```
Ensuite, il faut ajouter/supprimer/modifier les lignes qui commencent par nameserver:
```
nameserver X.X.X.X
```


## 5. Sur les distributions autres que Debian
Sur CentOs, on peux utiliser les outils nmcli et nmtui pour configurer le réseau. nmtui permet d'avoir une configuration graphique depuis un terminal. 
Pour avoir nmtui sous Debian, il faut installer le paquet nmtui.





---

Pour plus d'informations sur les configurations réseaux:
https://wiki.debian.org/fr/NetworkConfiguration
