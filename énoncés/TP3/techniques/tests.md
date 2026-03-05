[← Retour](../README.md)

# Tests

## Tests unitaires

Vous devez continuer à effectuer des tests unitaires pour l'ensemble de la logique de votre code.

## Tests d’intégration de persistance

Vous devez tester **toutes** vos fonctions de persistance, de la sauvegarde aux requêtes de filtrage. Afin de garantir
que vos implémentations *Mongo* et *in-memory* respectent les mêmes exigences, vous pouvez vous inspirer de la technique
des tests abstraits, qui sera présentée dans un laboratoire. Cette méthode nécessite que les classes testées implémentent
une même interface, permettant ainsi de définir l’ensemble des tests une seule fois, peu importe les implémentations.

### Librairie TestContainers

Pour éviter d’avoir à installer et à supprimer manuellement la base de données entre chaque test, vous utiliserez la
librairie [TestContainers](https://java.testcontainers.org/). Celle-ci utilise Docker pour démarrer automatiquement
des versions conteneurisées de Mongo pour chaque test.

### Librairies autorisées

Vous pouvez utiliser la librairie de votre choix, mais ça doit être en Java. Vous devez demander la permission si vous
utilisez une librairie autre que : assertj, google-truth, junit, rest-assured, jersey-client, jersey-test
ou testcontainers.

## Clean Code

L’ensemble de vos tests doit continuer à respecter les meilleures pratiques en matière de **Clean Code** :

- Donner un nom représentant clairement les 3 étapes du test (**arrange / act / assert**)
- Avoir un contenu qui reflète clairement ces 3 étapes
- Garder un contenu clair et précis, sans préparation excessive
- Préférer l’utilisation de variables pour éviter les *valeurs magiques*
