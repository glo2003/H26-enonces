# Projet Floppa - TP3

- **📅 Fin : 31 mars 2026 - 23h59**
- **Tag : `remise3`**

## Requis fonctionnels (features)

- [Offre sélectionnée](./fonctionnels/offre-selectionnee.md)
- [Statut de vente](./fonctionnels/statut-vente.md)
- [Vendre un produit](./fonctionnels/vente-produit.md)

## Requis de processus

- [Déploiement continu (CD)](./processus/cd.md)
- [Planification GitHub](./processus/planification.md)
- [Rétrospective](./processus/retrospective.md)
- [Stories](./processus/stories.md)

## Requis techniques

- [Architecture](./techniques/architecture.md)
- [Base de données MongoDB](./techniques/database.md)
- [Déclaration d'utilisation de l'IA](./techniques/declaration-IA.md)
- [Tests](./techniques/tests.md)

## Restrictions importantes

Pour assurer le bon fonctionnement des outils de correction automatisés, les éléments suivants doivent être respectés :

- **La route GET `/health`** : doit retourner `200 OK` lorsque l'application et la base de données sont fonctionnelles. Cette route est utilisée pour vérifier que votre serveur est prêt.
- **L'URL `0.0.0.0`** : votre serveur doit écouter sur cette adresse (notez que `localhost` ne fonctionne pas toujours).
- **Le port `8080`** : port par défaut si la variable d'environnement `PORT` n'est pas définie.
- **Le fichier `Dockerfile`** : doit être exactement celui fourni dans l'énoncé (voir [CD](./processus/cd.md)).

### Variables d'environnement et propriété système

Les outils de correction utilisent les éléments suivants pour démarrer et configurer votre application :

| Élément | Type | Description |
|---|---|---|
| `persistence` | Propriété système (`-D`) | `inmemory` (défaut) ou `mongo` |
| `PORT` | Variable d'environnement | Port d'écoute du serveur (défaut : `8080`) |
| `MONGO_CLUSTER_URL` | Variable d'environnement | URL de connexion MongoDB |
| `MONGO_DATABASE` | Variable d'environnement | Nom de la base de données |

> ⚠️ Votre application **doit** lire et respecter ces valeurs. Les outils de correction y spécifieront leurs propres valeurs.

## Critère d'évaluation et pondération

### Section Qualité

| Critère        | Pondération | Note     | Note Pondérée |
|----------------|-------------|----------|---------------|
| Processus      | 20%         | 100.00%  | 20.00%        |
| Clean code     | 30%         | 100.00%  | 30.00%        |
| Architecture   | 20%         | 100.00%  | 20.00%        |
| Tests          | 30%         | 100.00%  | 30.00%        |
| **SOUS-TOTAL** |             |          | **100.00%**   |

---

### Résumé

| Section    | Pondération | Note     | Note Pondérée |
|------------|-------------|----------|---------------|
| Qualité technique    | 80%         | 100.00%  | 80.00%        |
| Features   | 20%         | 100.00%  | 20.00%        |
| Pénalités  |             | 0.00%    | 0.00%         |
| **TOTAL**  |             |          | **100.00%**   |
