# TP - Spark Streaming et Analyse de Données en Temps Réel

## Objectifs du TP
- Comprendre les bases du streaming de données avec Spark
- Implémenter un programme WordCount en streaming
- Apprendre à utiliser ncat pour la simulation de flux de données
- Explorer différentes options de sortie pour les données streamées

## Prérequis
- Environnement Docker en cours d'exécution
- Accès au notebook '01_reading_from_sockets.ipynb'

## Instructions

### 1. Configuration de l'Environnement

1. Accédez au conteneur Jupyter Lab :
```bash
docker exec -it ed-pyspark-jupyter-lab bash
```

2. Mettez à jour les paquets système :
```bash
sudo apt-get update
```

3. Installez ncat :
```bash
sudo apt-get install ncat
```

4. Vérifiez l'installation :
```bash
ncat -v
```

### 2. Configuration du Serveur de Stream

1. Démarrez un serveur TCP sur le port 9999 :
```bash
ncat -l 9999
```

### 3. Exécution du WordCount en Streaming

![alt text](../img/cours5/complete_mode.png)

1. Ouvrez le notebook '01_reading_from_sockets.ipynb'
2. Exécutez les cellules du notebook
3. Observez les résultats du WordCount dans la console Docker lorsque vous envoyez des messages via le serveur ncat

### 4. Options de Sortie Alternatives

Le streaming peut écrire vers différents endpoints :
- Fichiers Parquet (local ou HDFS)
- Mémoire (RAM)
- Topics Kafka
- Bases de données

Exemple d'écriture vers une base de données SQL :
```python
# Dans PySpark, pour écrire vers une base SQL
query = df.writeStream \
    .foreachBatch(lambda df, id: df.write \
        .format("jdbc") \
        .option("url", "jdbc:sqlserver://...") \
        .mode("append") \
        .save()) \
    .start()
```

## Notes
- Par défaut, ncat utilise le protocole TCP pour l'échange de données
- Les résultats du WordCount s'affichent en temps réel à mesure que les messages sont envoyés
- Il est possible de personnaliser les endpoints de sortie selon les besoins du projet


### 5. Connexion Kafka et Spark streaming
Pour cela lancer le notebook "03_reading_from_kafka.ipynb" et suivre les instructions