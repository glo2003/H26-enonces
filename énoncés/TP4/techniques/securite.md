[← Retour](../README.md)

# Sécurité logicielle

De nos jours, il est pratiquement impossible de développer un logiciel sans utiliser de **librairies externes**.

Ces morceaux de code préconstruits et souvent entièrement testés nous permettent de gagner du temps et d'éviter de
réinventer la roue. Cependant, chaque nouvelle dépendance ajoutée à notre produit peut introduire des **vulnérabilités**.

## Analyse de sécurité

Afin de garantir que votre code repose sur des **librairies sécurisées**, liez votre repository à un outil d'analyse de
sécurité du code. Cet outil doit :

- **Analyser** les dépendances et **détecter** d'éventuelles failles de sécurité.
  - En cas de faille, il doit fournir un lien vers l'analyse de la vulnérabilité **CVE** ou proposer une version corrigée.
- **Analyser** les [dépendances transitives](https://owasp.org/www-project-dependency-check/) de vos dépendances directes.
- **Analyser** votre propre code afin d'identifier des utilisations non sécurisées.
- **S'exécuter automatiquement à chaque commit**, au minimum sur la branche principale (idéalement sur toutes les branches).

> Exemples d'outils : Snyk, Dependabot, OWASP Dependency-Check, etc.

Incluez des captures d'écran de rapports de vulnérabilités, à la fois **sommaires** et **détaillés**, dans votre fichier `exercices/tp4/tp4.md`.

Vous n'êtes pas tenu de corriger les problèmes identifiés, sauf s'ils font partie des critères d'évaluation indiqués dans
les énoncés.

## Vers des pratiques plus sécures

Dans votre fichier `exercices/tp4/tp4.md`, identifiez et décrivez **trois pratiques** à intégrer dans un processus de
développement logiciel afin de **réduire les risques de vulnérabilités**. Vous pouvez vous inspirer des concepts suivants :

- DevSecOps
- SSDLC (Secure Software Development Life Cycle)
- Software Supply Chain Security
- CI/CD/CS (Continuous Integration / Continuous Deployment / Continuous Security)
