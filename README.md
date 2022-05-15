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

---------- 

## Les fonctions SQL d'agrégation  

 

Les fonctions d’agrégation sont des fonctions idéales pour effectuer quelques statistiques de bases sur des tables. Les principales fonctions sont les suivantes :  

 

* AVG() pour calculer la moyenne sur un ensemble d’enregistrement

* COUNT() pour compter le nombre d’enregistrement sur une table ou une colonne distincte

* MAX() pour récupérer la valeur maximum d’une colonne sur un ensemble de ligne. Cela s’applique à la fois pour des données numériques ou alphanumérique

* MIN() pour récupérer la valeur minimum de la même manière que MAX()

* SUM() pour calculer la somme sur un ensemble d’enregistrement  

 

### La fonction AVG()  

 

La fonction d’agrégation AVG() dans le langage SQL permet de calculer une valeur moyenne sur un ensemble d’enregistrement de type numérique et non nul.  

 

On utlisera la commande suivante :

```SQL

SELECT AVG(nom_colonne) FROM nom_table

```  

Cela permet de calculer la moyenne d'une colonne dans une table.  

Il est possible de filtrer ce que l'on veut faire grâce à la commande **WHERE**.  

Il est également possible de regrouper les données en utilisant la commande **GROUP BY**.

 

Voici un exemple d'utilisation :

 

```SQL

SELECT AVG(`city_consumation`) FROM car;

```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectAVG.png)  
  
### La fonction COUNT  
  
La fonction permet de compter le nombre d’enregistrement dans une table. Connaître le nombre de lignes dans une table est très pratique dans de nombreux cas, par exemple pour savoir combien d’utilisateurs sont présents dans une table ou pour connaître le nombre de commentaires sur un articles.  
  
On utilisera la fonction suivante : 

```SQL
SELECT COUNT(*) FROM car;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectCount.png)  
  
Utilisation de COUNT(*) avec WHERE

Pour compter le nombre d’utilisateur qui ont effectué au moins un achat, il suffit de faire la même chose mais en filtrant les enregistrements avec WHERE :  
```SQL
SELECT COUNT(*) FROM car WHERE city_consumation;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectCountCondition.png)  

  
### La fonction Max  
  
La fonction MAX() permet de retourner la valeur maximale d’une colonne dans un set d’enregistrement. La fonction peut s’appliquer à des données numériques ou alphanumériques. Il est par exemple possible de rechercher le produit le plus cher dans une table d’une boutique en ligne.  
  
On utilisera la fonction suivante :  
  
```SQL
SELECT MAX(`city_consumation`)FROM car;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectMax.png)  

### La fonction Min  

La fonction MIN() permet de retourner la valeur minimale d’une colonne dans un set d’enregistrement. La fonction peut s’appliquer à des données numériques ou alphanumériques. Il est par exemple possible de rechercher le produit le moins cher dans une table d’une boutique en ligne.  
  
On utilisera la fonction suivante :  
  
```SQL
SELECT MIN(`city_consumation`)FROM car;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectMin.png)  

### La fonction SUM  
  
Dans le langage SQL, la fonction SUM() permet de calculer la somme totale d'une collonne contenant des valeurs numériques. Cette fonction ne fonctionne que sur des colonnes de types numériques (INT, FLOAT...) et n'additionne pas les valeurs NULL.  
  
On utilisera la fonction suivante :  
  
```SQL
SELECT SUM(city_consumation) FROM car;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectSum.png)  
  
On peut également rajouter une condition en utilisant **WHERE** : 
```SQL
SELECT SUM(price) FROM car WHERE id = 1;
```  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/selectSumCondition.png)  

------- 
## La fonction SQL ALTER TABLE



On utilisera la commande ALTER TABLE pour lier plusieurs tables entre-elles, en effet cela nous permet d'établir une relation à double sens:  
```SQL
ALTER TABLE `car` ADD FOREIGN KEY (`brand_id`) REFERENCES brand(id) ON DELETE CASCADE;
```
  
En effet nous pouvons avoir du Many to One ou One to Many car la relation est bi-drectionnelles.  
  

PAr exemple notre table **BRAND** incluant le champ *NAME* en l'occurence *BMW* peut avoir plusieurs modèles soit *brand_id* de notre table **CAR** donc une BMW peut être une BMW 325TDS, une BMW 330TDS, ou une BMW M3.    
  
Voici comment nous procédons concrètement :

![img shell](https://github.com/Thomas17130/mySQL/blob/main/img/alterTable.PNG)  

## La fonction SQL INNER JOIN  
  
La commande **INNER JOIN** est un type de jointure très commune pour lier plusieurs tables entres elles. cette commande retourne les enregistrements lorsqu'il y a au moins une ligne dans chaque colonne qui correspond à la condition.  
  
On utilisera la commande suivante :  
```SQL
SELECT * FROM user INNER JOIN car ON user.id = car.id;
```  
  
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/innerJoin.png)  
  







 