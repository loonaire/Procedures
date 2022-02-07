# Parametrage d'un switch cisco

Si le ping ne marche pas, vérifier le pare-feu.

## Afficher des informations

Afficher la configuration du switch:

```sh
Switch# show running-config
```

Afficher l'état des interfaces:

```sh
Switch# show interfaces
```

Afficher les vlan:

```sh
Switch# show vlan
Switch# show vlan brief
```

Afficher les informations de la configuration des ports:

```sh
Switch# show ip interfaces
Switch# show ip interfaces brief
```

Afficher les informations trunk:

```sh
Switch# show interfaces trunk
```

## Configurations sur un routeur

Assigner une adresse ip à une interfaces:

```sh
Routeur# conf t
Routeur(config)# int nom_interface
Routeur(config-if)# ip address [ip_address] [subnet mask]
Routeur(config-if)# no shutdown
Routeur(config-if)# exit
```

Définir la gateway :

```sh
Switch(conf)# ip default-gateway [ip]
```

## 1. Ajouter un vlan à un port

```sh
Switch# conf t  
Switch(config)# interface nom_interface  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan X  
Switch(config-if)#no shutdown  
Switch(config-if)#exit  
Switch# copy run start
```

## Mettre à jour un switch Cisco 2960

### 1. Télécharger l'image

Les images sont disponible sur le site de cisco, pour les versions de dev il faut un compte pour pouvoir les télécharger.

### 2. Mise à jour

- Prendre un serveur tftp (tftpd)
- Connecter un port réseau du switch à l'ordinateur

On copie l'image sur la partition flash du switch via tftp, en fonction de l'image le fichier peux être soit un fichier tar (pour la version de dev) ou un fichier bin (pour un fichier standard).

Dans le cas d'un fichier bin, on copie le fichier bin via tftp:

```sh
Switch#copy tftp://ipsrv/nomImage.bin flash:
```

Dans le cas d'un fichier tar, on extrait l'archive tout en l'uploadant sur le switch:

```sh
Switch#archive tar /xtract tftp://ipsrv/nomImage.bin flash:
```

Comme l'image a été copiée, on vérifie d'abord son intégrité:

```sh
Switch#verify flash:/nomImageAVerifier.bin
```

Ensuite, on indique au switch de démarrer sur la nouvelle image, pour cela, il faut passer en mode conf:

```sh
Switch#conf t
Switch(config)#boot system flash:/cheminverslefichierbin/image.bin
```

Avec la commande show boot on peux vérifier que l'image à bien été changé, il faut maintenant sauvegarder la configuration et relancer le switch avec les commandes:

```sh
Switch#copy running-config startup-config
Switch#reload
```

### Diverses commandes

- Affiche le contenu de la partition flash: :
  
```sh
Switch#show flash
```

- Affiche l'espace mémoire des partitions:

```sh
Switch#show file systems
```

- Supprimer un dossier et son contenu:

```sh
Switch#delete /recursive /force flash:/nomDuDossier
```

Pour plus d'infos sur les commandes de manipulation de la mémoire interne: [https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960xr/software/15-0_2_EX1/file_management/file_management/flash.html](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960xr/software/15-0_2_EX1/file_management/file_management/flash.html)

- Affiche la RAM utilisée:

```sh
Switch#show memory
```

- Se connecter a ssh sur un ancien switch (2960):

```sh
ssh user@ip -aes256-cbc
```

Le chiffrement à changer, il faut jsute préciser d'en utilisé un compatible avec le switch.

## Liens utiles

[Commandes des switch cisco: http://perso.univ-lyon1.fr/fabien.rico/site/_media/m1if15:lexique-de-commandes-cisco.pdf](http://perso.univ-lyon1.fr/fabien.rico/site/_media/m1if15:lexique-de-commandes-cisco.pdf)
[Configurer SSH](https://linux-note.com/cisco-configuration-de-ssh-sur-un-switch-catalyst-2960/)
[Configuration d'SSH détaillée](https://www.clemanet.com/activation-ssh.php)
[Diverses manipulations de base sur les appareils IOS Cisco](https://www.clemanet.com/configuration-base-switch.php)
[Configuration des VLAN](https://cisco.goffinet.org/ccna/vlans/configuration-vlan-cisco-ios/)
[Commandes en vrac](https://www.infotrucs.fr/quelques-commandes-cisco-ios-12-x/)
[Mettre en place telnet sur un apapreil Cisco IOS](https://www.ciscomadesimple.be/2009/08/06/cisco-configuration-dun-switch-via-telnet/)

[Gestion ACL](https://routeur.clemanet.com/acl-cisco.php)