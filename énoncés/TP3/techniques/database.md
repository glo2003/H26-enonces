[← Retour](../README.md)

# Connexion à une base de données externe

## Description

Pour stocker les informations sur le long terme, il est nécessaire de se connecter à une base de données externe. Dans
ce cadre, l'intégration avec une base de données [MongoDB](https://www.mongodb.com/) est requise. L'utilisation de l'ODM
(Object Document Mapper) [Morphia](https://morphia.dev/landing/index.html) facilitera et automatisera plusieurs tâches
liées à l'interaction avec cette base de données.

## Configuration de l'application

### Propriété système : sélection de la persistance

Au démarrage de l'application, la **propriété système** (*system property*) `persistence` permet de sélectionner le type
de persistance à utiliser. Vous devez donc développer deux implémentations pour chaque fonction de persistance : une pour
la persistance en mémoire et une autre pour MongoDB.

Les valeurs possibles sont :

| Valeur     | Description              |
|------------|--------------------------|
| `inmemory` | Persistance en mémoire (par défaut) |
| `mongo`    | Persistance MongoDB      |

Si la propriété n'est pas spécifiée, vous devez utiliser la version `inmemory`.

Exemple de démarrage avec Maven :

```bash
mvn exec:java -Dpersistence=mongo
```

### Variables d'environnement

> ⚠️ Ces variables d'environnement sont **requises** lorsque `persistence=mongo` et seront utilisées lors de la
> correction automatique. Votre application **doit** lire ces variables au démarrage et les utiliser pour se connecter
> à MongoDB. On doit pouvoir y spécifier n'importe quelle valeur.

| Variable             | Description                                                                                                                                                          |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MONGO_CLUSTER_URL`  | URL complet utilisé pour la connexion au cluster de bases de données. Contient le protocole, le *username*, le *password*, le *host*, le *port* et possiblement les options. |
| `MONGO_DATABASE`     | Nom de la base de données à laquelle se connecter.                                                                                                                    |

Exemple de démarrage complet :

```bash
export MONGO_CLUSTER_URL="mongodb://root:example@localhost:27017"
export MONGO_DATABASE="floppa"
mvn exec:java -Dpersistence=mongo
```

## Installation de MongoDB

Vous devez choisir entre installer une instance locale de MongoDB directement sur votre ordinateur ou utiliser une
version conteneurisée via Docker et `docker compose`.

### Option 1 : Instance locale

Pour ce faire, vous devez [installer MongoDB](https://www.mongodb.com/try/download/community) localement. Nous utiliserons
la dernière version à jour (8+) pour le projet.

### Option 2 (préférable) : Version conteneurisée (Docker)

Pour ce faire, vous devrez d'abord installer [Docker](https://www.docker.com/products/docker-desktop/). Utilisez ensuite
cette [configuration docker-compose](./docker-compose.yml) afin de démarrer une version conteneurisée de MongoDB.
Vous aurez simplement à exécuter `docker compose up` dans un terminal pour démarrer le serveur (ajoutez `-d` pour que
l'exécution soit en arrière-plan).

Avec cette configuration, l'URL de connexion est `mongodb://root:example@localhost:27017`.
Vous pouvez spécifier n'importe quelle valeur pour `MONGO_DATABASE`, la base de données sera automatiquement créée.

## Connexion

La connexion au cluster MongoDB nécessite d'abord la création d'un client Mongo (`com.mongodb.client.MongoClients`),
suivie de la création d'un datastore Morphia (`dev.morphia.Datastore`). Les documentations suivantes fournissent les
informations nécessaires à cette configuration :

- Documentation [MongoDB Java Driver](https://www.mongodb.com/docs/drivers/java/sync/current/fundamentals/connection/connect/)
- Documentation [Morphia - Quick Tour](https://morphia.dev/morphia/2.5/quicktour.html)

## Morphia

Morphia permet de *mapper* vos classes Java vers des objets représentatifs simples ("documents") pour la base de données.
Il sera donc primordial de respecter le même principe que pour vos réponses du UI, c'est-à-dire de créer des classes
propres aux documents MongoDB qui contiendront des champs de **primitives seulement** ainsi que les annotations Morphia.
La [documentation Morphia](https://morphia.dev/morphia/2.5/) contient beaucoup d'informations pertinentes.
