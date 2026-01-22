[← Back](../README.md)

# Création vendeur

## Description

En tant que vendeur, je peux me créer un compte afin d'accéder aux fonctionnalités de l'application.

## Critères de succès

- Les champs `name`, `email`, `phoneNumber` et `bio` sont obligatoires et ne sont pas vides.
- Le vendeur a 18 ans ou plus (au moment de la création).
- Le nouveau vendeur est sauvegardé dans l'application.
- Le nouveau vendeur possède un identifiant **unique**.
- Le nouveau vendeur possède une date de création non-modifiable.

## Requête

**Route**

`POST /sellers`

**Body**

```ts
{
  name: string,
  birthdate: Date,
  email: Email,
  phoneNumber: PhoneNumber,
  bio: string
}
```

**Exemple**

```json
{
  "name": "John Doe",
  "birthdate": "1968-09-12",
  "email": "john.doe123@gmail.com",
  "phoneNumber": "14181234567",
  "bio": "A simple man."
}
```

## Réponse

**Status**

`201 CREATED`: succès

**Headers**

- `Location: string` : URI du nouveau vendeur
  - format : `<baseUrl>/sellers/<sellerId>`
  - exemple : `http://localhost:8080/sellers/12345`

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
