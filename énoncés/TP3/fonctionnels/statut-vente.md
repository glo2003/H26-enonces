[← Retour](../README.md)

# Statut de vente

> **Note** : `GET /sellers/{sellerId}`, `GET /products` et `GET /products/{productId}` incluent maintenant
> le champ `saleStatus` pour indiquer si un produit est en cours de vente (`ongoing`) ou vendu (`sold`).

## Description

En tant qu'utilisateur, je peux voir le statut de vente des produits.

## Critères de succès

- Le statut est `ongoing` lorsque le produit est créé.
- Le statut est `sold` lorsque le produit est vendu.

## Requête

**Routes**

- `GET /sellers/{sellerId}`
- `GET /products`
- `GET /products/{productId}`

## Réponse

**Body** (par produit)

```ts
{
  ...,
  saleStatus: SaleStatus // "ongoing" | "sold"
}
```

**Exemple — `GET /products/{productId}`**

```json
{
  "...": "...",
  "saleStatus": "ongoing"
}
```

**Exemple — `GET /products` ou `GET /sellers/{sellerId}`**

```json
{
  "products": [
    {
      "...": "...",
      "saleStatus": "ongoing"
    }
  ]
}
```
