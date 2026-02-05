[← Back](../README.md)

# Obtention des produits filtrés

## Description

En tant qu'utilisateur, je peux filtrer les produits afin de trouver ceux qui m'intéressent.

## Critères de succès

- Je vois les informations de base du vendeur de chaque produit.
- Je vois quelques statistiques sur les offres.
- Les produits retournés satisfont tous les filtres.
- Le filtre de titre est inclusif et insensible à la case. Ex: le produit avec titre "sOmEtHiNg" est retourné si le filtre de titre "eth" est appliqué.
- Les filtres de prix sont inclusifs.
- Si un filtre n'est pas présent, alors il est ignoré.
- La moyenne des montants des offres est `null` s'il n'y a pas d'offres.

## Requête

**Route**

`GET /products`

**Query params**

- `sellerId` (`string`) : id du vendeur vendant le produit
- `title` (`string`) : titre du produit
- `category` (`ProductCategory`) : catégorie du produit
  > Les valeurs minimales permises pour `ProductCategory` sont : `beauty`, `electronics`, `sports`, `apparel` et `housing`. Votre implémentation doit **au minimum** supporter ces valeurs, mais vous pouvez en ajouter d'autres si vous le souhaitez.
- `minPrice` (`Amount`) : prix suggéré minimum du produit (inclusif)
- `maxPrice` (`Amount`) : prix suggéré maximum du produit (inclusif)

**Exemples**

- `GET /products` : Retourne tous les produits, non filtrés.
- `GET /products?minPrice=10&title=brush` : Retourne les produits au prix minimal de 10$ et contenant le mot *brush* dans le titre.

## Réponse

**Status**

`200 OK`: succès

**Body**

```ts
{
  products: [
    {
      id: string,
      createdAt: DateTime,
      title: string,
      description: string,
      suggestedPrice: Amount,
      category: ProductCategory,
      seller: {
        id: string,
        name: string,
      },
      offers: {
        count: number,
        avgAmount: Amount | null,
      }
    }
  ]
}
```

**Exemple**

```json
{
  "products": [
    {
      "id": "123",
      "createdAt": "2020-06-30T23:54:23.382Z",
      "title": "Nice hairbrush",
      "description": "Pink and all.",
      "suggestedPrice": 34.21,
      "category": "beauty",
      "seller": {
        "id": "abc",
        "name": "John Doe"
      },
      "offers": {
        "count": 2,
        "avgAmount": 36.43
      }
    },
    {
      "id": "456",
      "createdAt": "2020-06-30T22:54:23.382Z",
      "title": "Left shoe",
      "description": "The right one is missing.",
      "suggestedPrice": 54.12,
      "category": "apparel",
      "seller": {
        "id": "abc",
        "name": "John Doe"
      },
      "offers": {
        "count": 0,
        "avgAmount": null
      }
    }
  ]
}
```

**Exemple - aucun produit correspondant**

```json
{
  "products" : []
}
```

## Exceptions

- `400 BAD REQUEST`: un des paramètres n'est pas valide

**Body**

```ts
{
  error: "INVALID_PARAMETER",
  description: string
}
```
