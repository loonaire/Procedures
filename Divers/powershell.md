# Powershell

Un site qui document en partie les fonctions powershell: https://ss64.com/

## **Afficher la version de powershell**
On peux l'afficher en affichant la variable:
```
> $PSVersionTable
```
Afficher cette variable permet d'avoir également les versions compatibles de powershell et d'autres éléments potentiellement utile.
<br><br>
On peux également affiche la version en utilisant la commande:
```powershell
> Get-Host
```
Cette commande affiche encore d'autres informations sur powershell


Enfin, si l'on souhaite seulement la version, on peux utiliser directement la commande:
```powershell
> Get-Host | Select Version
```


## **Mettre à jour l'aide**

> Cette étape est obligatoire pour pouvoir utiliser la commande get-help

> **IMPORTANT** Il faut être en mode administrateur pour pouvoir mettre à jour l'aide


```powershell
> Update-Help
```

Par défaut, la commande met à jour avec la langue locale de windows, pour installer une autre langue (ici, installe l'aide en anglais):
```powershell
> Update-Help -UICulture en-US
```


## **Afficher l'aide**
Pour afficher l'aide d'une il faut utiliser la commande:
```powershell
> Get-Help
```

## **Afficher l'aide d'une commande**
Pour afficher l'aide d'une commande, il faut utiliser la commande:
```powershell
> Get-Help <Nom de la commande>
```

On peux également afficher l'aide qui renvoi sur le site de la doc de microsoft:
```powershell
> Get-Help <Nom de la commande> -Online
```

## **Afficher les membres d'une commande**

Il faut ajouter | get-member après la commande
```powershell
> Get-<commande a utiliser> | Get-Member
```


## **Afficher les propriétés des membres d'une commande**

Afficher toutes les propriétés:
```powershell
> Get-<commande à utiliser> | Select *
```

On peux aussi afficher un choix:
```powershell
> Get-<commande à utiliser> | Select <col1>,<col2>,...
```

On peux également formater la sorte avec des commandes du type Format-Table

## **Filtrer les informations à afficher**
On peux filtrer le résultat d'une commande qui commande par Get.

```powershell
> Get-<commande> | Where {$_.<colonne> -eq "chaine ou valeur à comparer"}
```
> $_ correspond à ce qui est retourner par Get-< commande >  
> -eq peux être remplacer par -like, -gt (greater than), -lt (lesser than), ...   
> **IMPORTANT** Pour la chaine à comparer, il faut absolument la mettre entre guillemets.  
> On peux également ajouter des éléments avec -or ou -and



## **Les modules**
On peux importer des modules pour avoir des nouvelles commandes.
> **IMPORTANT**  
> Depuis powershell 6, powershell est devenu multi plateforme. Il faut donc importer certains modules présents nativemant dans les versions précédentes de powershell.

Afficher les modules disponibles:
```powershell
> Get-Module 
```
Pour afficher tout les modules disponibles:
```powershell
> Get-Module -ListAvailable
```

Importer un module:
```powershell
> Import-Module -Name <Nom du module>
```

Afficher tout les modules chargés:
```powershell
> Get-Module -All
```

Importer une version minimum d'un module:
```powershell
> Import-Module -Name <Nom du module> -MinimumVersion <version minimum>
```

Importer une version précise d'un module:
```powershell
> Import-Module -Name <Nom du module> -RequiredVersion <version>
```

## **Connaitres les commandes disponible avec Get-Command**

On peux afficher toutes les commandes disponible avec la commande:
```powershell
> Get-Command
```

Chercher une commande:
```powershell
> Get-Command -Name "terme à chercher"
```
> On peux utiliser un bout de text et utiliser le caractère * pour cherche plus simplement, ne pas hésiter a utiliser: \*termeAChercher\*




<br><br>
Par défaut, affiche les alias, les fonctions ainsi que les cmdlet. On peux afficher seulement un type avec la commande:
```powershell
> Get-Command -CommandType <CommandType>
```

Afficher les alias:
```powershell
> Get-Command -CommandType Alias
```
Afficher les commandes powershell:
```powershell
> Get-Command -CommandType Cmdlet
```
Affiche les fonctions powershell:
```powershell
> Get-Command -CommandType Function
```
Affiche les commandes "classiques" disponible:
```powershell
> Get-Command -CommandType Application
```

Affiche tout les types de commande type disponible:
```powershell
> Get-Command -CommandType All
```

<br><br>
On peux également afficher toutes les commandes d'un module:
```powershell
> Get-Command -Module <Nom du module>
```








