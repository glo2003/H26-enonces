[← Retour](../README.md)

# Planification du travail

L'ensemble de votre travail doit être documenté et planifié sur GitHub en respectant les meilleures pratiques de
développement et de processus logiciel. Vous devez donc créer et maintenir à jour :

1. Un [**GitHub Project**](#github-project)
2. Un [**milestone**](#milestone) pour le TP2
3. Des [**issues**](#issues-3)
4. Des [**Pull Requests**](#pull-requests-3) (PR)
5. Un [**arbre de commits**](#arbre-de-commits)

> **⚠️ Important :** on demande toujours l'arbre de commits, mais celui-ci est demandé dans ce fichier
> plutôt que dans l'énoncé `conventions-git.md` du TP1.

Afin de vous évaluer, vous devrez fournir des **captures d'écran** dans le fichier d'exercice
`exercices/tp2/tp2.md`.

### Consignes pour les captures d’écran

- Toutes les captures d’écran doivent être **commitées dans le dépôt** (pas de lien externe).
- Placez toutes les images dans le dossier : **`exercices/tp2/images/`**
- Référencez chaque image directement dans `exercices/tp2/tp2.md` avec un lien relatif Markdown :

```md
![Description](./images/nom-image.png)
```

### Conseils de qualité

- Assurez-vous que le texte est lisible.
- Le screenshot doit inclure tous les éléments demandés.
- Nommez vos fichiers de façon claire : tp2-project.png, tp2-milestone.png, tp2-issue-1.png, tp2-pr-1.png, tp2-commit-tree.png, etc.

## Github Project

#### Critères (ce que l’on s’attend à voir)

- **Workflow clair** : colonnes de type Kanban représentant des étapes compréhensibles.
- **Traçabilité** : les issues du TP2 apparaissent dans le Project.
- **Cohérence du statut** : le placement des issues dans les colonnes reflète leur état (ex. une issue fermée ne devrait pas être “En cours”).

#### Screenshots

- **1 screenshot** comprenant les colonnes et les issues visibles.

## Milestone

#### Critères (ce que l’on s’attend à voir)

- **Milestone TP2 existant** : titre clair et description (si pertinente).
- **Date de fin** correspondant à l’échéance du TP.
- **Couverture** : les issues du TP2 sont associées à ce milestone.

#### Screenshots

- **1 screenshot** comprenant le titre, la description (si présente), la date de fin et les issues associées.

## Issues (3)

#### Critères (ce que l’on s’attend à voir)

- **Découpage du travail** : les issues représentent des tâches de taille raisonnable (ni “fourre-tout”, ni micro-tâches inutiles).
- **Titre informatif** : on comprend l’objectif sans devoir lire tout le contexte.
- **Description utile** : attentes claires (quoi faire), critères de succès / idées / notes techniques si nécessaire.
- **Métadonnées complètes** :
    - au moins 1 label ou type
    - le milestone TP2
    - le GitHub Project
    - assignée à au moins 1 membre

#### Screenshots

- **3 screenshots** (1 screenshot par issue) où l’on voit clairement :
    - le titre et la description
    - le/les labels ou le type
    - le milestone
    - l’assigné
    - l’association au GitHub Project

## Pull requests (3)

#### Critères (ce que l’on s’attend à voir)

- **Quantité de changements** : PRs de taille raisonnable et bien séparées (scope clair).
- **Titre informatif et description** qui résume l’intention et ce qui a changé.
- **Revue** : au moins 1 review par un membre de l’équipe.
- **Qualité de la revue** : au moins 1 commentaire de code review pertinent et constructif (ex. suggestion, question technique, amélioration).
- **Métadonnées complètes** :
    - **Lien au GitHub Project** : la PR est associée au GitHub Project.
    - **Lien au milestone** : la PR est associée au milestone.
    - **Assignation** : PR assignée à au moins 1 membre.

#### Screenshots

- **3 screenshots** (1 à 2 screenshot par PR)
    - 1 capture par PR montrant le titre, la description, l’association à une issue, l’assigné et la section de review.
    - 1 capture de plus (au besoin) montrant une partie du code review (commentaire pertinent) si ce n’est pas lisible sur la première.

## Arbre de commits

#### Critères (ce que l’on s’attend à voir)

- **Conformité** : les messages de commit respectent votre convention de commits (format et contenu).
- **Historique lisible** : commits compréhensibles (pas "fix", "test" à répétition) et progression cohérente.
- **Branches visibles** : si vous utilisez des branches, on doit les voir (si elles n’ont pas été supprimées).

#### Screenshots

- **1 screenshot** pour votre **arbre de commits et de branches** (montrez les branches si elles n'ont pas été supprimées
  et au moins 10 commits visibles, incluant les noms)
