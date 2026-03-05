[← Retour](../README.md)

# Vente de produit

## Description

En tant que vendeur, je peux vendre un produit à un acheteur en sélectionnant l'offre qui me convient.

## Critères de succès

- Le nom d'utilisateur de l'acheteur est spécifié pour la sélection.
- L'acheteur choisi a bel et bien fait une offre sur le produit.
- Aucune offre ne peut être faite sur un produit vendu.
- Le produit passe au statut `sold` et l'offre sélectionnée devient l'offre de vente du produit.

## Requête

**Route**

`POST /products/{productId}/sell`

**Headers**

- `X-Seller-Id: string` : ID du vendeur qui vend le produit

**Body**

```ts
{
  username: string
}
```

**Exemple**

```json
{
  "username": "abc"
}
```

## Réponse

**Status**

`200 OK`: succès

## Exceptions

- `400 BAD REQUEST`: un des paramètres obligatoires est manquant.

**Body**

```ts
{
  error: "MISSING_PARAMETER",
  description: string
}
```

- `400 BAD REQUEST`: un des paramètres n'est pas valide.

**Body**

```ts
{
  error: "INVALID_PARAMETER",
  description: string
}
```

- `404 NOT FOUND`: un élément requis n'existe pas.
  - le vendeur associé à `X-Seller-Id` n'existe pas
  - le produit associé à `productId` n'existe pas
  - aucune offre avec `username` n'existe sur le produit

**Body**

```ts
{
  error: "NOT_FOUND",
  description: string
}
```

- `409 CONFLICT`: le produit est déjà vendu (vente déjà effectuée).

**Body**

```ts
{
  error: "NOT_PERMITTED",
  description: string
}
```

## Impact sur `POST /products/{productId}/offers`

Lorsqu'un produit est vendu, toute tentative de création d'offre (`POST /products/{productId}/offers`) doit retourner :

- `409 CONFLICT`

**Body**

```ts
{
  error: "NOT_PERMITTED",
  description: string
}
```
