[← Back](../README.md)

# Création d'une offre

## Description

En tant qu'acheteur, je peux faire une offre sur un produit afin de montrer qu'il m'intéresse.

## Critères de succès

- Le montant minimal est le montant suggéré du produit.
- Le message est d'au moins **50 caractères**.
- Un acheteur peut faire seulement **1 offre** par produit.
- La nouvelle offre possède une date de création non-modifiable.
- La nouvelle offre est sauvegardée dans l'application.

## Requête

**Route**

`POST /products/{productId}/offers`

**Headers**

- `X-Buyer-Username: string` : Nom d'utilisateur de l'acheteur qui crée l'offre

**Body**

```ts
{
  amount: Amount,
  message: string
}
```

**Exemple**

```json
{
    "amount": 12.33,
    "message": "I need these because...+100"
}
```

## Réponse

**Status**

`201 CREATED`: succès

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

- `404 NOT FOUND`: le produit associé à `productId` n'existe pas.

  **Body**

  ```ts
  {
    error: "NOT_FOUND",
    description: string
  }
  ```

- `409 CONFLICT`: une offre de l'acheteur existe déjà sur ce produit.

  **Body**

  ```ts
  {
    error: "ALREADY_EXISTS",
    description: string
  }
  ```
