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
