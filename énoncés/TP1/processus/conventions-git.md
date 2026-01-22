[← Retour](../README.md)

# Conventions Git

Vous commencez un nouveau projet, il est donc impératif de mettre en place des bonnes conventions en équipe.

1. [**Fichier .gitignore**](#fichiers-ignorés)
2. [**Nommage des commits**](#nommage-des-commits)
3. [**Stratégie de branchage**](#stratégie-de-branchage)
4. [**Arbres de commits**](#arbre-de-commits)

## Fichiers ignorés

Ajoutez un fichier `.gitignore` à la racine de votre projet. Ce dernier **doit** suivre les meilleures pratiques en terme 
de fichiers ignorés. Vous trouverez beaucoup d'information sur le Web à ce sujet. On veut notamment ignorer :

- Les configurations *personnelles* (mais pas celles d'équipe!)
- Les fichiers contenant des *path* personnels (Ex: `/User/Steph/Documents/glo2003/le_projet`)
- Les fichiers auto-générés
- Les fichiers contenant des *secrets* (mots de passes, clés, etc.)
- Les *builds* (fichiers compilés)

Certaines configurations standards sont disponibles sur le Web, mais vous **devez** vous assurer de bien l'adapter à 
votre projet et de **citer vos sources!**.

> **Important — synchronisation avec le dépôt :**
> Si un fichier (ou dossier) a déjà été **commité** dans le dépôt, l’ajouter ensuite au `.gitignore` ne suffit pas.
> Vous devez aussi le **retirer de l’index Git** (sans le supprimer de votre machine), sinon Git continuera de le suivre
> malgré le `.gitignore`.

## Nommage des commits

Vous devez suivre une convention pour l'écriture et le contenu des commits. Vous pouvez vous inspirer de pratiques 
populaires existantes si vous le désirez. On vous demande de **décrire votre convention de commits** dans le fichier 
`exercices/tp1/tp1.md`. Assurez-vous d'**indiquer vos sources** si vous vous inspirez d'ailleurs. On cherche notamment à savoir :

1. Comment nommer les commits selon leur type/section/grosseur/acteur/etc.
2. Quoi et quand commiter?

Vous n'êtes pas obligé de suivre un standard, mais vos méthodes *doivent* être **cohérentes**.

## Stratégie de branchage

Vous devez établir une convention pour la gestion et le nommage des branches. Vous pouvez vous inspirer de pratiques 
populaires existantes si vous le désirez. On vous demande de **décrire votre stratégie de branchage** dans le fichier 
`exercices/tp1/tp1.md`. Assurez-vous d'**indiquer vos sources** si vous vous inspirez d'ailleurs. On cherche notamment à savoir :

1. Quelles sont les branches *de base* (qui sont communes et qui existeront toujours) et quels sont leurs rôles (chacune)?
2. Quelle branche est *LA* branche principale (contenant le code officiellement intégré et pouvant être remis)?
3. Quand créer une nouvelle branche?
4. Quand faire une demande de changement / d'intégration (pull request / merge request) et sur quelle branche la faire?

Voici quelques exemples de stratégies que vous pouvez utiliser ou pour vous inspirer :
- [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- [Github Flow](https://githubflow.github.io/)
- [Gitlab Flow](https://about.gitlab.com/topics/version-control/what-is-gitlab-flow/)
- Trunk based ([1](https://dora.dev/capabilities/trunk-based-development/) et [2](https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development))

Vous n'êtes pas obligé de suivre un standard, mais vos méthodes *doivent* être **cohérentes**.

## Arbre de commits

#### Critères (ce que l’on s’attend à voir)

- **Conformité** : les messages de commit respectent votre convention de commits (format et contenu).
- **Historique lisible** : commits compréhensibles (pas "fix", "test" à répétition) et progression cohérente.
- **Branches visibles** : si vous utilisez des branches, on doit les voir (si elles n’ont pas été supprimées).

#### Screenshots

- **1 screenshot** pour votre **arbre de commits et de branches** (montrez les branches si elles n'ont pas été supprimées
  et au moins 10 commits visibles, incluant les noms)
