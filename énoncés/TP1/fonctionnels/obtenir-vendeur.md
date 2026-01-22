[← Back](../README.md)

# Obtenir vendeur

## Description

En tant que vendeur, je peux visualiser mes informations personnelles.

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
    }
  ]
}
```

**Exemple : avec produit**

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
      "category": "beauty"
    }
  ]
}
```

**Exemple : sans produit**

```json
{
  "id": "abc",
  "createdAt": "2020-06-04T06:56:34.918Z",
  "name": "John Doe",
  "birthdate": "1968-09-12",
  "email": "john.doe123@gmail.com",
  "phoneNumber": "14181234567",
  "bio": "A simple man",
  "products": []
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