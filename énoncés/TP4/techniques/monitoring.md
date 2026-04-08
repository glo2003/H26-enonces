[← Retour](../README.md)

# Monitoring d'erreurs

Bien que des [outils d'analyses](./analyse.md) et des tests aient été mis en place, des bogues peuvent toujours survenir.
De plus, en pratique, les applications s'exécutent sur des serveurs distants où l'accès aux logs et aux débogueurs
n'est pas toujours possible. Pour pallier ce problème, vous devez mettre en place [Sentry](https://sentry.io/), un outil
permettant de détecter, rapporter et notifier les erreurs en production.

> Sentry offre un [plan Developer gratuit](https://sentry.io/pricing/) suffisant pour le projet.

**Critères**

1. Doit rapporter **toutes** les erreurs **non gérées** de votre code, sauf celles générées automatiquement par Jersey (ex: 404 pour une route inexistante, 405 pour une méthode non supportée).
L'utilisation d'un *exception mapper* pourrait grandement vous aider.
2. Utilisez la variable d'environnement `SENTRY_DSN` pour la valeur du DSN, puisqu'il s'agit d'une **donnée sensible**.
Si la variable n'est pas définie, l'application doit démarrer normalement sans Sentry (la correction automatique ne fournit pas cette variable).
3. Ne **pas** utiliser le plugin `sentry-maven-plugin`, car il pourrait bloquer la correction automatique (nécessite une clé d'API).
Utilisez plutôt la dépendance `sentry` directement dans votre code.

Incluez des captures d'écran de rapports d'erreurs, à la fois **sommaires** et **détaillés**, dans votre fichier `exercices/tp4/tp4.md`.

Vous n'êtes pas tenu de corriger les problèmes identifiés, sauf s'ils font partie des critères d'évaluation indiqués dans
les énoncés.
