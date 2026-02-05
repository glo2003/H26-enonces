[← Retour](../README.md)

# Requis architecturaux

## Respect des couches

Vous devez séparer clairement la couche de présentation (**API / Jersey**) de la couche logique (**domaine / services**).

- Les classes Jersey (ressources API) doivent contenir le minimum : gestion HTTP, validation API de base, appel à la 
logique et construction de la réponse.
- Toute logique métier (vérifications, règles, actions, orchestration) doit être extraite dans des classes des couches 
logiques (ex. services / use cases / domaine).

## Convertisseurs (mapping)

Pour relier l’API et la logique, utilisez des **convertisseurs** (*mappers*) :

- Ils transforment les objets API (ex. `CreateProductRequest`, `ProductResponse`) en objets logiques (ex. `Product`, `Seller`, etc.) **et vice-versa**.
- L’objectif est d’éviter que l’API expose directement vos objets du domaine ou que votre logique dépende de classes API/Jersey.

## Gestion des erreurs (Exception Mappers)

Pour garder les ressources Jersey simples et cohérentes, la gestion des erreurs doit être centralisée à l’aide d' 
**Exception Mappers** (Jersey).

- Les exceptions doivent être converties en réponses HTTP via des `ExceptionMapper`.
- Évitez les `try/catch` dans les ressources API, sauf si nécessaire.
- Les réponses d’erreur devraient être cohérentes (code HTTP + message clair).

**Important (correction automatique) :** les clés du JSON retourné doivent être **exactement** les mêmes que dans l’énoncé (error et description) :

```ts
{
  error: "ERROR_TYPE",
  description: string
}
```

## Packages

Afin de bien organiser les classes, vous devez choisir une **structure de packages** cohérente et la respecter.

Faites une courte recherche sur des stratégies existantes (ex. *vertical slicing* vs *horizontal slicing*). 

Voici quelques axes possibles :
- par **couches** (api, logique/domaine, persistence, etc.)
- par **modules/features** (product, seller, offer, etc.)
- par **type** (requests, converters, factories, repositories, etc.)

Certaines structures facilitent l’évolution du code plus que d’autres : discutez-en en équipe et assumez un choix clair.

Finalement, assurez-vous que les noms des packages suivent les conventions Java/Maven (minuscules, pas d’accents, pas d’underscore, etc.).

## Diagrammes d’architecture

**Veuillez répondre dans le fichier `exercices/tp2/tp2.md` de votre repo.**

Afin de visualiser les dépendances entre vos classes et vos couches, vous devez fournir un **diagramme d’architecture simplifié**.

### Directives

- Indiquez clairement la **couche** de chaque classe (ex. couleurs + légende).
- Pas besoin d’attributs ni de méthodes : seulement les **noms des classes**.
- Pas besoin des classes de bas niveau (ex. `Email`, `PhoneNumber`, `OwnerId`, etc.) sauf si vraiment pertinent.
- N’incluez **aucune** classe que vous **n’avez pas créée** (ex. librairie standard, Jakarta, frameworks).
- Pour chaque relation importante, ajoutez une flèche **étiquetée** (verbe général) :
    - **utilise** (*uses*)
    - **reçoit** (*receives*)
    - **crée** (*creates*)
    - **trouve / sauvegarde** (*finds / saves*)
    - **se transforme en** (*maps to*)
    - **valide** (*validates*)
    - **modifie** (*modifies*)
    - **implémente** (*implements*)

> Pensez à des actions générales (“valide”, “utilise”, “mappe vers”) plutôt qu’à des actions trop spécifiques comme (“modifie le nom”).

### Explication et Problèmes identifiés

Ajoutez une courte explication qui :

- décrit les rôles des classes principales
- explique vos choix d’architecture et de structure de packages
- identifie les relations “suspectes” (ex. dépendances inversées, logique dans l’API, cycles) **et** propose des pistes de correction

> **Important :** vous n’avez pas à avoir une architecture parfaite à ce stade.  
> Si vous **identifiez correctement** les problèmes (ou risques) de votre architecture et que vous proposez des 
> **correctifs concrets** à appliquer au prochain TP, vous pouvez **tout de même obtenir les points** pour cette section.

### Conseils

- Pas besoin d’annotations UML : boîtes + flèches suffisent.
- Outil suggéré : diagrams.net (**pas** Visual Paradigm).
- Assurez-vous que l’image est exportée avec une bonne résolution et que tout le texte est clairement lisible.

Exemple de diagramme (feature simple de gestion des utilisateurs, incomplet) :

<div align="center">
<img src="https://user-images.githubusercontent.com/32545895/218632494-9c417121-49c1-45c1-97a4-427a9450e965.png" width="600px" alt="Diagramme architecture simplifié">
</div>
