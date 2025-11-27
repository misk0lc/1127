# API Documentation -- reservationkisuj Copy

## Overview

This REST API collection supports basic authentication (registration,
login, logout) and full CRUD operations for **reservations**.\
The documentation below explains each endpoint, its method, required
headers, request body, and expected responses.

------------------------------------------------------------------------

## Base URL

    {{base_url}}

Default: `https://template.postman-echo.com`

------------------------------------------------------------------------

# Authentication Endpoints

------------------------------------------------------------------------

## 1. **Register**

**POST** `/register`

### Headers

    Accept: application/json
    Content-Type: application/json

### Body (JSON)

``` json
{
  "name": "Patrik",
  "email": "patrik@gmail.com",
  "password": "Nemtudom20",
  "password_confirmation": "Nemtudom20"
}
```

### Response

-   `201 Created` or `200 OK`\
    Returns user data and authentication token.

------------------------------------------------------------------------

## 2. **Login**

**POST** `/login`

### Headers

    Accept: application/json
    Content-Type: application/json

### Body

``` json
{
  "email": "patrik@gmail.com",
  "password": "Nemtudom20"
}
```

### Response

-   `200 OK`\
    Returns authentication token.

------------------------------------------------------------------------

## 3. **Logout**

**POST** `/logout`

### Headers

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Response

-   `200 OK`\
    User logged out.

------------------------------------------------------------------------

# Reservation Endpoints

------------------------------------------------------------------------

## 4. **List All Reservations**

**GET** `/reservations`

### Headers

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Response

-   `200 OK` Returns all reservations.

------------------------------------------------------------------------

## 5. **Get One Reservation**

**GET** `/reservations/{id}`

### Example

`/reservations/2`

### Headers

Same as above.

### Response

-   `200 OK`

------------------------------------------------------------------------

## 6. **Create New Reservation**

**POST** `/reservations`

### Headers

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Body

``` json
{
  "reservation_time": "2025-10-02 18:43:30",
  "guests": "4",
  "note": "valami de az nagyon"
}
```

### Response

-   `201 Created` or `200 OK`

------------------------------------------------------------------------

## 7. **Update Reservation (Full Update)**

**PUT** `/reservations/{id}`

### Example

`/reservations/11`

### Body

``` json
{
  "reservation_time": "2025-10-02 18:43:30",
  "guests": "4",
  "note": "valami de az asd"
}
```

### Response

-   `200 OK` / `204 No Content`

------------------------------------------------------------------------

## 8. **Update Reservation (Partial)**

**PATCH** `/reservations/{id}`

### Body

``` json
{
  "note": "valami de az igen"
}
```

------------------------------------------------------------------------

## 9. **Delete Reservation**

**DELETE** `/reservations/{id}`

### Response

-   `200 OK` / `204 No Content`

------------------------------------------------------------------------

# Variables

  Key          Value
  ------------ -------------------------------------
  `id`         `1`
  `base_url`   `https://template.postman-echo.com`

------------------------------------------------------------------------

# Notes

-   All reservation routes require a valid **Bearer token**.
-   Make sure to update Postman environment variables before sending
    requests.

------------------------------------------------------------------------

Generated automatically.
