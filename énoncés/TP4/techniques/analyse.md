[← Retour](../README.md)

# Outils d'analyse de code

Bien que vous effectuiez des revues de code, il est pratiquement impossible de garantir la qualité de l'ensemble d'un
logiciel. Pour y remédier, plusieurs outils permettent d'analyser automatiquement et en continu le code afin de détecter
d'éventuels problèmes.

Intégrez un ou plusieurs outils d'analyse de code permettant d'évaluer :

1. La **qualité** du code (clean code, bogues potentiels, optimisations, bonnes pratiques, etc.)
2. La **couverture** des tests

> Exemples d'outils : SonarCloud, CodeClimate, Codacy, etc.

Ces outils doivent être intégrés à votre pipeline d'intégration continue (CI) afin de s'exécuter automatiquement à
chaque modification de votre repository, **au minimum sur la branche principale**.

Pour l'analyse de **sécurité**, référez-vous à [Sécurité logicielle](./securite.md).

Ajoutez dans votre fichier `exercices/tp4/tp4.md` des captures d'écran montrant une analyse sommaire ainsi qu'une analyse
détaillée. Vous n'avez pas à corriger les problèmes identifiés, sauf s'ils font partie des critères d'évaluation indiqués
dans les énoncés.
