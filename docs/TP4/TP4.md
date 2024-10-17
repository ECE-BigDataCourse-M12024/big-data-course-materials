# TP - Analyse de données avec Power BI et PostgreSQL

## Objectifs du TP: Créer un rapport PowerBI en se connectant à une source de donnée PostgreSQL
- Utiliser Docker pour déployer une base de données PostgreSQL
- Exécuter des requêtes SQL pour préparer les données
- Connecter Power BI à une base de données PostgreSQL
- Effectuer des transformations de données dans Power BI
- Créer un rapport d'analyse dans Power BI

## Outils et Versions
* [Docker](https://www.docker.com/) 
* [PostgreSQL](https://www.postgresql.org/) (via Docker image)
* [Power BI Desktop](https://powerbi.microsoft.com/desktop/) Version *latest*

## Instructions

### 1. Préparation de l'environnement Docker

Créez un réseau Docker personnalisé pour notre application, pour cela ouvrir votre terminal et entrer la commande suivante :

```bash
docker network create --driver=bridge my_app_network
```

### 2. Déploiement de la base de données PostgreSQL

Exécutez la commande suivante pour télécharger et lancer la base de données PostgreSQL Dellstore :

```bash
docker run -itd --net=my_app_network -p 5432:5432 --name pg-ds-dellstore aa8y/postgres-dataset:dellstore
```

### 3. Accès à la base de données

Pour accéder à la base de données, exécutez :

```bash
docker exec -it pg-ds-dellstore psql -d dellstore
```

### 4. Exploration et préparation des données

1. Listez les tables disponibles :

```sql
\dt
```

2. Créez une nouvelle table en joignant les données des clients et des commandes :

```sql
CREATE TABLE customer_orders AS
SELECT 
    c.customerid,
    c.firstname,
    c.lastname,
    c.username,
    c.city,
    c.state,
    c.zip,
    c.country,
    c.age,
    c.gender,
    c.income,
    o.orderid,
    o.orderdate,
    o.netamount,
    o.tax,
    o.totalamount
FROM 
    customers c
JOIN 
    orders o ON c.customerid = o.customerid;
```

3. Vérifiez la nouvelle table :

```sql
SELECT * FROM customer_orders LIMIT 5;
```

### 5. Connexion de Power BI à PostgreSQL

1. Lancez Power BI Desktop
2. Cliquez sur "Obtenir des données" et sélectionnez "Base de données PostgreSQL"
3. Configurez la connexion :
   - Serveur : localhost
   - Base de données : dellstore
   - Mode de connectivité : Importer
4. Sélectionnez la table `public.customer_orders`

### 6. Transformation des données dans Power BI

1. Cliquez sur "Transformer les données"
2. Modifiez les types de données :
   - `customerid`, `zip`, `ordered`, `age` -> Type Texte
3. Remplacez les codes postaux '0' par 'N/A'
4. Cliquez sur "Fermer et appliquer" pour charger les données transformées

### 7. Création du rapport

Commencez à construire votre rapport en utilisant les données importées. Explorez les différentes visualisations et fonctionnalités de Power BI pour créer des insights pertinents sur les données client et commandes.
