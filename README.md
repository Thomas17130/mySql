# MySQL monitor  
------
Dans ce tutoriel, nous allons voir comment utiliser MySQL dans un command prompt  
------
 Ouvrir le CMD  

## Pour ouvrir le CMD, il faut taper simultanement sur les touches :  
<kdb>windows</kdb> + <kdb>r</kdb>  
Ceci nous ouvrira le Shell dans lequel on va taper *cmd* , ce qui nous permettra d'ouvrir le command prompt.  

![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/cmd.png)  

Une fois le *cmd* ouvert, il va falloir nous placer dans __MySQL__ en suivant le chemin 'C:\wamp64\bin\mysql\mysql5.7.36\bin', pour cela dans notre *cmd* il faudra ecrire :   
```
set PATH=%PATH%; C:\wamp64\bin\mysql\mysql5.7.36\bin
```  
un autre moyen d'aller directment dans le fichier avec *cmd* et d'ouvrir le fichier est de taper *cmd* dans l'url.  
  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/Animation.gif)  
------
## Ouvrir MySQL dans *cmd*
Taper la ligne de commande suivante : 'mysql -u root -p' 
Si vous n'avez pas de mot de passe , alors tapez entrer lors de la demande mot de passe 
------
## Les bases de données  
Une basse de données c'est un espace de stockage sous forme de tableau depuis lequel une application va pouvoir effectuer des actions.  
Une base de données contient des objets  
dans une base de données un objet équivaut à une table, par exemple dans une base de données qui rescence des véhicules la table **voiture** vaut l'objet *voiture*  
Pour reprendre notre exemple, une **Audi** ou une **BMW** sont chacunes une instance de l'objet *voiture*.  

>:warning: Lorque l'on nomme les bases de données ou les tables on ne doit pas utiliser de caractères spéciaux ou d'espaces.  
>Par convention, les objets (nom des tables) sont au singulier.  
  
* Les objets sont catégorisés par leur nom  
* Les types representent les champs  
* Les caractéristiques des champs sont le typage de chaques champs (ex: integer)  
* Le schéma d'une table est un tableau récapitulant les caractéristiques des champs des objets  
------
## Création de la base de données  
Pour créer une base de données, il nous faudra taper la commande suivante : 
```SQL
CREATE DATABASE mydatabase;
```  
un petit message apparaît pour verifier que la base à bien été créer : 
  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/createDatabase.png)
