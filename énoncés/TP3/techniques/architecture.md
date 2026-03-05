[← Retour](../README.md)

# Requis architecturaux

## Rappel

Les requis architecturaux du TP2 s'appliquent toujours :

- **Séparation API / Domaine** : les ressources Jersey restent minces (gestion HTTP, appel à la logique, construction de la réponse).
- **Convertisseurs (mappers)** : les objets API (`Request`, `Response`) ne doivent pas traverser la couche domaine.
- **Exception Mappers** : la gestion des erreurs reste centralisée.
- **Structure de packages** : votre organisation de packages doit rester cohérente.

## Nouvelle couche : persistance

Avec l'ajout de MongoDB, votre architecture comporte maintenant **trois couches** :

```
API (Jersey)  →  Domaine (logique métier)  →  Persistance (MongoDB / mémoire)
```

La couche **domaine** ne doit jamais dépendre directement de la couche **persistance**. Pour y arriver, appliquez le
pattern **Repository** :

- Définissez une **interface** (ex. `SellerRepository`) dans la couche domaine.
- Créez **deux implémentations** : une en mémoire (`InMemorySellerRepository`) et une pour MongoDB (`MongoSellerRepository`).
- La couche domaine utilise l'interface sans savoir quelle implémentation est active.

Au démarrage, la propriété système `persistence` (voir [database.md](./database.md)) détermine quelle implémentation
est injectée.

### Documents Morphia vs objets domaine

Le même principe que pour les convertisseurs API s'applique vers le bas :

- Les **classes annotées Morphia** (documents MongoDB) sont des objets propres à la couche persistance.
- Elles ne doivent pas être vos objets du domaine.
- Créez des convertisseurs pour transformer vos objets domaine en documents Morphia **et vice-versa**.

## Diagramme d'architecture

**Veuillez répondre dans le fichier `exercices/tp3/tp3.md` de votre repo.**

Refaites l'exercice du diagramme d'architecture du TP2. Cette fois-ci, votre diagramme doit inclure la **couche de
persistance** en plus des couches API et domaine.

Assurez-vous qu'aucun problème de séparation des couches ne soit présent. Référez-vous aux directives du TP2 pour
le format du diagramme.

## Clean Code

Votre code doit continuer à respecter les meilleures pratiques en matière de **Clean Code**. Portez une attention
particulière à :

- **Pas de duplication** entre les implémentations `InMemory` et `Mongo` (la logique métier reste dans le domaine).
- **Nommage clair** : distinguez bien les classes domaine, API et persistance.
- **Responsabilité unique** : un repository ne fait que persister/retrouver, il ne contient pas de logique métier.
