[← Retour](../README.md)

# Tests

## Tests unitaires

Afin d’assurer le bon fonctionnement de chaque partie du code, vous devez tester
unitairement **toutes les méthodes de toutes vos classes**. Toutefois, en pratique,
on ne teste pas souvent les éléments suivants :

- Les constructeurs (**sauf** pour les validations)
- Les classes de type ressources/api (seront testées par intégration)
- Le “contexte” (`Main`, préparation et enregistrement des resources, etc.)
- Les méthodes de type `get` (souvent testées indirectement)

Afin de pouvoir facilement tester des comportements unitaires, vous devrez créer plus
de classes que simplement celles des ressources. Par exemple, vous devez créer :

- des *factories* pour la création des objets (avec validations)
- des classes pour la sauvegarde et la recherche/obtention (ex. repositories)
- des *assembleurs/mappers* pour la conversion logique ↔ représentation

## Tests d'intégration d'API (Jersey)

Pour être certain que votre logiciel soit bien intégré à Jersey, vous devez effectuer
des tests d’intégration pour les routes suivantes :

- `POST /products`
- `POST /sellers`
- `GET /sellers/{sellerId}`

Pour chaque route, vous devez couvrir :

- **1 cas de succès**
- **au moins 1 cas** pour **chaque type d’erreur** mentionné dans les features

Pour chaque test, assurez-vous de vérifier :

- le **status** de retour
- les **headers** attendus (lorsque applicable, ex. `Location`)
- le contenu du **body**

La librairie **JerseyTest** permet de démarrer automatiquement un serveur Jersey (sur un
port aléatoire) pour exécuter vos tests avec JUnit. JerseyTest offre également des
fonctionnalités pour appeler votre serveur et valider les réponses.

> **Note importante (tests d’intégration, pas E2E)**  
> Les tests d’intégration Jersey visent à valider l’intégration **entre vos routes et Jersey**
> (routing, sérialisation/désérialisation, status HTTP, headers, etc.), **sans** dépendre de
> l’infrastructure complète.
>
> Pour cette raison, vous devez **mocker les dépendances** derrière vos ressources (ex. services,
> repositories, etc.).

## Clean code

L’ensemble de vos tests doit respecter les meilleures pratiques en matière de *Clean Code*.
Vous devez donc vous assurer de :

- Donner un nom représentant clairement les 3 étapes du test (**arrange / act / assert**)
- Avoir un contenu qui reflète clairement ces 3 étapes
- Garder un contenu clair et précis, sans préparation excessive qui viendrait “bruiter” le test
- Découper le code en sous-fonctions et sous-classes lorsque nécessaire
- Préférer l’utilisation de variables pour éviter les *valeurs magiques*
