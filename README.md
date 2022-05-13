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
  
Pour verifier notre base de données, on peut utiliser la commande **SHOW**  
```
SHOW DATABASES;
```  
Enfin pour pouvoir agir sur notre base de données(la selectionner), on utilisera la commande :
```SQL
USE mydatabase;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/useDatabase.png)  
------
## Création des tables  
Pour créer une table, il nous faudra taper la commande suivante en précisant entre parenthèses les champs et les types pour chaque colonnes : 
```SQL
CREATE TABLE user (
    id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nickname VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    adult BOOLEAN DEFAULT false
);
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/createTable.png)  
  
Pour verifier que la table s'est bien créer, on utilise la commande suivante : 
```SQL
SHOW TABLES;
```
 Pour verifier que le schéma s'est bien créer, on utilise la commande suivante : 
```SQL
SHOW COLUMNS FROM user;
```
 
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/showTable.png)  

### Les différents types pour creer une table  
Il existe plusieurs types que l'on peut integrer dans une table :   
| VARCHAR | INTEGER | BOOLEAN | FLOAT | DATE | TEXT |  
|---------|---------|---------|-------|------|------|  
| nb de caractere max | nb entier | true ou false | nb decimal | date | chaine de caracteres sans limites |  
------  
## Intéragir avec notre base de données  
Intéragir avec notre base de données nous permet de réaliser des opérations CRUD, l'acronyme CRUD qui signifie : 
**CREATE**, **READ**, **UPDATE**, **DELETE**.  
Toutes les commandes que nous allons voir sont dans la 
[documentation officielle](https://sql.sh/)
Commençons par insérer des objets uniques pour alimenter notre BDD;  
On utilisera la commande **INSERT INTO** qui prend en compte  
* les paramètres de la table dans laquelle on souhaite insérer l'objet  
* l'ordre des colonnes (caractéristiques) de l'objet  
* les valeurs correspondantes à chaque colonnes  
Voici un exemple pour ajouter un utilisateur dans la BDD :  
```SQL
INSERT INTO `user` (`nickname`, `email`, `adult`)
VALUES ('Tom', 'tom@gmail.com', true);
```
Nous allons insérer plusieurs utilisateurs à la fois : 
```SQL
INSERT INTO `user` (`nickname`, `email`, `adult`)
VALUES  ('Tom', 'tom@gmail.com', true),
        ('Toto', 'toto@gmail.com', true),
        ('Tata', 'tata@gmail.com', true);

```  
  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/insertInto.png)  

On utlisera la commande **SELECT FROM** qui prend en compte  
* le nom du champ  
* le nom de la table  
Voici un exemple de selection :  
```SQL
SELECT `nickname`
FROM `user`
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectFrom.png)    
  
Voici un exemple où je sélectionne tout les utilisateurs avec une contrainte de l'email finissant par 
gmail.com
 :  
```SQL
SELECT `email` FROM `user` 
WHERE `email` 
LIKE "%gmail.com";
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectCondition.png)  

Voici comment mettre une contrainte sur une chaine de caractère :  
![image Shell](https://github.com/Thomas17130/mySQL/blob/main/img/contrainte.png)    

Nous pouvons aussi ordonner nos objets grâce au mot clé **ORDER BY** :  
```SQL
SELECT * FROM `user` ORDER BY id DESC;
```  
![image Shell](https://github.com/Thomas17130/mySQL/blob/main/img/selectDesc.png)  
  
On utilisera la commande **UPDATE SET WHERE** qui permet  
* d'attribuer une nouvelle valeur à une colonne
* En prenant en compte les conditions indiquées par **WHERE**  
Voici un exemple de selection :  
```SQL
UPDATE user
SET `nickname` = 'Elwenn'
WHERE id = 2;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/update.png)  
  
On utilisera la commande **DELETE** qui permet de supprimer des lignes dans une table  
Voici un exemple de suppression :  
```SQL
DELETE FROM `user`
WHERE id = 3;
```
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/delete.png)  

