[← Retour](../README.md)

# Offre sélectionnée

> **Note** : Le champ `selectedOffer` est ajouté **par produit** dans la liste `products`.
> Il est `null` si le produit n'est pas vendu, sinon il contient l'offre sélectionnée (acheteur + montant).

## Description

En tant que vendeur, je vois les informations de vente sur mes produits.

## Critères de succès

- Si un produit n'est pas vendu, aucune information sur la vente n'est visible pour ce produit (`selectedOffer = null`).
- Si un produit est vendu, l'offre sélectionnée est visible pour ce produit et contient le `username` et le `amount`.

## Requête

**Route**

`GET /sellers/{sellerId}`

## Réponse

**Body**

```ts
{
  ...,
  products: [
    {
      ..., 
      selectedOffer: null | {
        username: string,
        amount: Amount
      }
    }
  ]
}
```

**Exemple - vendu**

```json
{
  "...": "...",
  "products": [
    {
      "...": "...",
      "selectedOffer": {
        "username": "abc",
        "amount": 54.24
      }
    }
  ]
}
```

**Exemple - non vendu**

```json
{
  "...": "...",
  "products": [
    {
      "...": "...",
      "selectedOffer": null
    }
  ]
}
```
