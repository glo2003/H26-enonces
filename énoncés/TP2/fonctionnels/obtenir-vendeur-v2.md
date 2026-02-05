[← Back](../README.md)

# Obtention vendeur - V2

> **Note** : Cette route est une évolution de **"obtenir-vendeur"** (TP1).
> La route est la même (`GET /sellers/{sellerId}`), mais la réponse est enrichie
> afin d’inclure les détails et statistiques des offres pour chacun des produits.

## Description

En tant que vendeur, je peux voir les détails des offres sur mes produits.

## Critères de succès

- Je vois les montants moyens, minimaux et maximums des offres.
- Je vois la liste des offres.
- Si un produit ne contient pas d'offres, les montants moyens, minimums et maximums sont `null` et la liste est vide.

## Requête

**Route**

`GET /sellers/{sellerId}`

## Réponse

**Status**

`200 OK`: succès

**Body**

```ts
{
  id: string,
  createdAt: DateTime,
  name: string,
  birthdate: Date,
  email: Email,
  phoneNumber: PhoneNumber,
  bio: string,
  products: [
    {
      id: string,
      createdAt: DateTime,
      title: string,
      description: string,
      suggestedPrice: Amount,
      category: ProductCategory,
      offers: { // NOUVEAU
        count: number,
        avgAmount: Amount | null,
        minAmount: Amount | null,
        maxAmount: Amount | null,
        items: [
          {
            username: string,
            createdAt: DateTime,
            amount: Amount,
            message: string,
          }
        ]
      }
    }
  ]
}
```

**Exemple : avec offres**

```json
{
  "id": "abc",
  "createdAt": "2020-06-04T06:56:34.918Z",
  "name": "John Doe",
  "birthdate": "1968-09-12",
  "email": "john.doe123@gmail.com",
  "phoneNumber": "14181234567",
  "bio": "A simple man",
  "products": [
    {
      "id": "123",
      "createdAt": "2020-06-30T23:54:23.382Z",
      "title": "Nice hairbrush",
      "description": "Pink and all.",
      "suggestedPrice": 34.21,
      "category": "beauty",
      "offers": {
        "count": 2,
        "avgAmount": 34.23,
        "minAmount": 34.22,
        "maxAmount": 34.24,
        "items": [
          {
            "username": "johnny123",
            "createdAt": "2020-07-30T23:54:23.382Z",
            "amount": 34.22,
            "message": "Thank you for...+100"
          },
          {
            "username": "sammy456",
            "createdAt": "2020-07-30T23:54:23.382Z",
            "amount": 34.24,
            "message": "I like your...+100"
          }
        ]
      }
    }
  ]
}
```

**Exemple : sans offre**

```json
{
  "id": "abc",
  "createdAt": "2020-06-04T06:56:34.918Z",
  "name": "John Doe",
  "birthdate": "1968-09-12",
  "email": "john.doe123@gmail.com",
  "phoneNumber": "14181234567",
  "bio": "A simple man",
  "products": [
    {
      "id": "123",
      "createdAt": "2020-06-30T23:54:23.382Z",
      "title": "Nice hairbrush",
      "description": "Pink and all.",
      "suggestedPrice": 34.21,
      "category": "beauty",
      "offers": {
        "count": 0,
        "avgAmount": null,
        "minAmount": null,
        "maxAmount": null,
        "items": []
      }
    }
  ]
}
```

## Exceptions

- `404 NOT FOUND`: le vendeur associé à `sellerId` n'existe pas.

**Body**

```ts
{
  error: "NOT_FOUND",
  description: string
}
```
