# TP3 - Pypsark, Jupyter Notebook & Databricks

Dans l'archive TP3.zip vous trouverez l'ensemble des éléments nécessaires pour ce TP. 

- un fichier 'wordcount-pyspark.py' qui comme son nom l'indique va nous servir à faire un comptage de mot à partir du fichier purchases.txt utilisé lors des TPs précédents.
- un fichier '0-pyspark-understanding-sc-sessions.ipynb' qui est un notebook jupyter qui va nous permettre de comprendre les notions de spark context et spark sessions un peu plus en détail.
- un fichier '1-hands-on-pyspark-introduction-101.ipynb' qui est un notebook jupyter qui va nous permettre de voir les principales fonctions permettant de charger, traiter et sauvegarder des données via pyspark. 
- un répertoire input qui contient l'ensemble des données utilisées par les différents scripts. 


### wordcount-pyspark

Nous utiliserons le fichier python de l'archive TP3.zip nommé 'wordcount-pyspark.py'

Passons maintenant en revue les différentes méthodes pour exécuter ce script PySpark :

1. Via spark-submit:
   C'est la façon la plus courante (et recommandée) d'exécuter des scripts PySpark.

   a. Ouvrez un terminal et naviguez jusqu'au répertoire contenant le script
   b. Exécutez la commande suivante:
      ```
      spark-submit wordcount-pyspark.py
      ```

   Si Spark n'est pas dans votre PATH, vous devrez peut-être utiliser le chemin complet :
   ```
   /path/to/spark/bin/spark-submit wordcount-pyspark.py
   ```

Nb: Vous pouvez passer des configurations Spark directement dans la commande spark-submit, comme :
  ```
  spark-submit --master local[4] --executor-memory 4G simple_app.py
  ```


2. Via la commande 'pyspark':
   Cette méthode lance un shell interactif PySpark et exécute votre script.

   a. Exécutez:
      ```
      pyspark -i wordcount-pyspark.py
      ```

3. Directement depuis vottre IDE (VS Code ou PyCharm par exemple):
   a. Configurer votre IDE avec PySpark (cela implique généralement de configurer le PYTHONPATH)
   b. Ouvrez votre script dans l'IDE
   c. Exécuter le script en utilisant la commande run de l'IDE
