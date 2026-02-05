# Projet Floppa - TP2

- **📅 Fin: 3 mars 2026 à 23:59**
- **Tag: `remise2`**

## Requis fonctionnels (features)

- [Créer une offre](fonctionnels/creer-offre.md)
- [Filtrer les produits](fonctionnels/filtrer-produits.md)
- [Obtenir un produit](fonctionnels/obtenir-produit.md)
- [Obtenir un vendeur V2](fonctionnels/obtenir-vendeur-v2.md)

## Requis de processus

- [CI](processus/ci.md)
- [Planification](processus/planification.md)
- [Retrospective](processus/retrospective.md)

## Requis techniques

- [Architecture](techniques/architecture.md)
- [Clean Code](techniques/clean-code.md)
- [Déclaration utilisation IA](techniques/declaration-IA.md)
- [Tests](techniques/tests.md)

## Restrictions importantes

Pour assurer le bon fonctionnement des outils de correction automatisés, vous **ne devez pas modifier** les éléments suivants :

- **La route GET `/health`** : Cette route est utilisée pour vérifier si votre serveur démarre correctement.
- **L'URL `0.0.0.0`** : Cela rend votre serveur accessible sur un réseau local (notez que `localhost` ne fonctionne pas toujours).
- **Le port `8080`** : Utilisez ce port pour votre serveur.
- **Le fichier `Dockerfile`** : Ce fichier est essentiel pour démarrer votre serveur.

## Critère d'évaluation et pondération

### Section Qualité technique

| Critère        | Pondération | Note     | Note Pondérée |
|----------------|-------------|----------|---------------|
| Processus      | 35%         | 100.00%  | 35.00%        |
| Clean code     | 25%         | 100.00%  | 25.00%        |
| Architecture   | 15%         | 100.00%  | 15.00%        |
| Tests          | 20%         | 100.00%  | 20.00%        |
| CI             | 5%          | 100.00%  | 5.00%         |
| **SOUS-TOTAL** |             |          | **100.00%**   |

---

### Résumé

| Section           | Pondération | Note     | Note Pondérée |
|-------------------|-------------|----------|---------------|
| Qualité technique | 80%         | 100.00%  | 80.00%        |
| Features          | 20%         | 100.00%  | 20.00%        |
| Pénalités         |             | 0.00%    | 0.00%         |
| **TOTAL**         |             |          | **100.00%**   |
