[← Retour](../README.md)

# Déploiement continu (CD)

Vous devez *packager* votre application et la téléverser dans un registre afin de pouvoir facilement, uniformément et
rapidement utiliser votre application dans n'importe quel environnement.

## Variables d'environnement

Lors du déploiement, il est impossible de prédire à l’avance sur quel port l’application pourra s’exécuter.
Cette valeur est souvent déterminée dynamiquement par le *runner* (serveur hôte) en fonction des autres applications
déjà en cours d’exécution. Vous devez donc récupérer la variable d’environnement `PORT` et démarrer l’application sur
ce port. Si cette variable n’est pas définie, utilisez la valeur `8080` par défaut. Pour l’adresse `host`, utilisez toujours `0.0.0.0`.

## *Packaging* avec Docker

En Java, il existe plusieurs façons de *packager* et distribuer une application. La méthode classique consiste à générer
un fichier `.jar`, qui correspond à une archive précompilée du code. Ce fichier est ensuite interprétable sous différents
environnements Java. Cependant, les étapes pour construire un JAR sont souvent obscures et les dépendances ne sont pas
toujours bien liées. De plus, les nouvelles versions majeures de Java sont de plus en plus courantes et même si la
majorité du code reste *backward-compatible*, ce n'est pas toujours le cas.

Ainsi, afin de mieux assurer le comportement de l'application, vous la déploierez dans une image Docker.

> ⚠️ Le fichier de configuration `Dockerfile` vous est déjà fourni. **Vous devez vous assurer qu'il est exactement
> comme ceci** (copié-collé) :

```
FROM maven:3-amazoncorretto-21

WORKDIR /app

COPY pom.xml .
RUN mvn --batch-mode exec:java || exit 0

COPY . .
RUN mvn --batch-mode compiler:compile

CMD ["mvn", "--batch-mode", "--offline", "exec:java"]
```

> L'option `--batch-mode` rend les logs plus lisibles en désactivant le suivi de progression de Maven.

## Déploiement (GitHub Actions)

La construction et le déploiement de votre image Docker doivent se faire à l'aide d'un pipeline automatisé avec
**GitHub Actions**. Votre déploiement doit s'effectuer :

- À chaque nouveau commit sur votre branche principale
- À chaque nouveau tag
- Manuellement (déploie le dernier commit)

### Exigences du registre et du nom de l'image

Votre image Docker doit être publiée dans le registre GitHub Container Registry (**GHCR**), dont le domaine est `ghcr.io`.

Concrètement, le nom complet de l'image doit suivre ce format : `ghcr.io/<owner>/<repository>`

- `<owner>` : votre nom d’organisation GitHub
- `<repository>` : le nom exact de votre dépôt GitHub **en minuscules**

### Exigences des tags de l'image

À chaque déploiement, vous devez publier l'image avec :

1. **Le hash du commit** (obligatoire)
    - Tag = le SHA du commit
2. **Le nom du tag Git** (`remise3`)
    - Si le déploiement est déclenché par un tag Git, vous devez aussi publier l'image avec ce tag

> **Exemple :**
>
> Sur un commit :
> ```
> ghcr.io/<owner>/<repository>:a1b2c3d
> ```
>
> Sur un tag `remise3` :
> ```
> ghcr.io/<owner>/<repository>:a1b2c3d
> ghcr.io/<owner>/<repository>:remise3
> ```

Voici une ressource qui pourrait vous aider : <https://docs.github.com/en/actions/publishing-packages/publishing-docker-images>.
