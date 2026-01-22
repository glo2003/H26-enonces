[← Back](../README.md)

# Création produit

## Description

En tant que vendeur, j'aimerais pouvoir mettre mes produits en vente.

## Critères de succès

- Le titre n'est pas vide.
- La description n'est pas vide.
- Le produit est associé à une catégorie.
- Le prix suggéré minimum est 1$ (inclusif).
- Le nouveau produit possède un identifiant **unique**.
- Le nouveau produit possède une date de création non-modifiable.
- Le nouveau produit est sauvegardé dans l'application.

## Requête

**Route**

`POST /products`

**Headers**

- `X-Seller-Id: string` : ID du vendeur qui crée le produit

**Body**

```ts
{
  title: string,
  description: string,
  suggestedPrice: Amount,
  category: ProductCategory
}
```

**Exemple**

```json
{
  "title": "Nice hairbrush",
  "description": "Pink and all.",
  "suggestedPrice": 34.21,
  "category": "beauty"
}
```

## Réponse

**Status**

`201 CREATED`: succès

**Headers**

- `Location: string` : URI du nouveau produit
  - format : `<baseUrl>/products/<productId>`
  - exemple : `http://localhost:8080/products/12345`

## Exceptions

- `400 BAD REQUEST`: un des paramètres obligatoires est manquant

  **Body**

  ```ts
  {
    error: "MISSING_PARAMETER",
    description: string
  }
  ```

- `400 BAD REQUEST`: un des paramètres n'est pas valide

  **Body**

  ```ts
  {
    error: "INVALID_PARAMETER",
    description: string
  }
  ```

- `404 NOT FOUND`: le vendeur associé à `X-Seller-Id` n'existe pas.

  **Body**

  ```ts
  {
    error: "NOT_FOUND",
    description: string
  }
  ```
