# Projet Floppa - TP4

- **📅 Fin : 24 avril 2026 - 23h59**
- **Tag : `remise4`**

## Requis fonctionnels

- [Vos stories](fonctionnels/story.md)

## Requis de processus

- [Rétrospective](processus/retrospective.md)
- [Planification](processus/planification.md)
- [Open Source](processus/open-source.md)

## Requis techniques

- [Outils d'analyse](techniques/analyse.md)
- [Architecture](techniques/architecture.md)
- [Déclaration IA](techniques/declaration-IA.md)
- [Monitoring d'erreurs](techniques/monitoring.md)
- [Sécurité](techniques/securite.md)

## Restrictions importantes

Pour assurer le bon fonctionnement des outils de correction automatisés, les éléments suivants doivent être respectés :

- **La route GET `/health`** : doit retourner `200 OK` lorsque l'application et la base de données sont fonctionnelles. Cette route est utilisée pour vérifier que votre serveur est prêt.
- **L'URL `0.0.0.0`** : votre serveur doit écouter sur cette adresse (notez que `localhost` ne fonctionne pas toujours).
- **Le port `8080`** : port par défaut si la variable d'environnement `PORT` n'est pas définie.

### Variables d'environnement et propriété système

Les outils de correction utilisent les éléments suivants pour démarrer et configurer votre application :

| Élément | Type | Description |
|---|---|---|
| `persistence` | Propriété système (`-D`) | `inmemory` (défaut) ou `mongo` |
| `PORT` | Variable d'environnement | Port d'écoute du serveur (défaut : `8080`) |
| `MONGO_CLUSTER_URL` | Variable d'environnement | URL de connexion MongoDB |
| `MONGO_DATABASE` | Variable d'environnement | Nom de la base de données |
| `SENTRY_DSN` | Variable d'environnement | DSN Sentry (optionnel — l'application doit démarrer normalement si absent) |

> ⚠️ Votre application **doit** lire et respecter ces valeurs. Les outils de correction y spécifieront leurs propres valeurs.
