---
title: Authentication
description: JWT-based authentication for the Convergio AI API.
---

# Authentication

Convergio AI uses JWT (JSON Web Tokens) with database-backed sessions for authentication.

## Endpoints

### Register

```
POST /api/auth/register
```

Create a new user account.

=== "Request"

    ```json
    {
      "email": "user@example.com",
      "password": "securepassword",
      "name": "John Doe"
    }
    ```

=== "Response (201)"

    ```json
    {
      "token": "eyJhbGciOi...",
      "user": {
        "id": 1,
        "email": "user@example.com",
        "name": "John Doe"
      }
    }
    ```

### Login

```
POST /api/auth/login
```

Authenticate with email and password. Returns a JWT and refresh token.

=== "Request"

    ```json
    {
      "email": "user@example.com",
      "password": "securepassword"
    }
    ```

=== "Response (200)"

    ```json
    {
      "token": "eyJhbGciOi...",
      "refreshToken": "eyJhbGciOi...",
      "user": {
        "id": 1,
        "email": "user@example.com",
        "name": "John Doe"
      }
    }
    ```

### Refresh token

```
POST /api/auth/refresh
```

Exchange a refresh token for a new access token.

### Logout

```
POST /api/auth/logout
```

Destroy the current session. Requires JWT.

### Get current user

```
GET /api/auth/me
```

Returns the authenticated user's profile. Requires JWT.

## Using the token

Include the JWT in the `Authorization` header:

```
Authorization: Bearer eyJhbGciOi...
```

## Security model

- JWT + database session double-check (valid JWT AND active session)
- Session revocation is instant (delete session record)
- Refresh tokens for seamless token renewal
- Password hashing with bcrypt (cost factor 10)
- Optional 2FA via TOTP with backup codes
