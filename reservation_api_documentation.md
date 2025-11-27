# API Dokumentáció -- reservationkisuj

## Áttekintés

Ez a REST API gyűjtemény támogatja az alapvető autentikációs
folyamatokat (regisztráció, bejelentkezés, kijelentkezés), valamint a
**foglalások (reservations)** teljes CRUD kezelését.

Az alábbi dokumentáció ismerteti az összes végpontot, a szükséges HTTP
metódusokat, headereket, kérés törzsét és a várható válaszokat.

------------------------------------------------------------------------

## Alap URL

    {{base_url}}

Alapértelmezett: `https://template.postman-echo.com`

------------------------------------------------------------------------

# Autentikációs végpontok

------------------------------------------------------------------------

## 1. **Regisztráció**

**POST** `/register`

### Headerek

    Accept: application/json
    Content-Type: application/json

### Törzs (JSON)

``` json
{
  "name": "Mihály",
  "email": "mihaly@gmail.com",
  "password": "Jelszo12",
  "password_confirmation": "Jelszo12"
}
```

### Válasz

-   `201 Created` vagy `200 OK`\
    A felhasználót és az auth tokent adja vissza.

------------------------------------------------------------------------

## 2. **Bejelentkezés**

**POST** `/login`

### Headerek

    Accept: application/json
    Content-Type: application/json

### Törzs

``` json
{
  "email": "mihaly@gmail.com",
  "password": "Jelszo12"
}
```

### Válasz

-   `200 OK`\
    Tokennel tér vissza.

------------------------------------------------------------------------

## 3. **Kijelentkezés**

**POST** `/logout`

### Headerek

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Válasz

-   `200 OK`\
    Sikeres kijelentkezés.

------------------------------------------------------------------------

# Foglalások végpontjai

------------------------------------------------------------------------

## 4. **Összes foglalás lekérése**

**GET** `/reservations`

### Headerek

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Válasz

-   `200 OK`\
    Visszaadja az összes foglalást.

------------------------------------------------------------------------

## 5. **Egy foglalás lekérése**

**GET** `/reservations/{id}`

### Példa

`/reservations/2`

### Headerek

Ugyanaz mint fent.

### Válasz

-   `200 OK`

------------------------------------------------------------------------

## 6. **Új foglalás létrehozása**

**POST** `/reservations`

### Headerek

    Accept: application/json
    Content-Type: application/json
    Authorization: Bearer <token>

### Törzs

``` json
{
  "reservation_time": "2025-10-02 18:43:30",
  "guests": "4",
  "note": "Születésnapi tortát hozunk, hűtést igényel."
}
```

### Válasz

-   `201 Created` vagy `200 OK`

------------------------------------------------------------------------

## 7. **Foglalás módosítása (teljes frissítés)**

**PUT** `/reservations/{id}`

### Példa

`/reservations/11`

### Törzs

``` json
{
  "reservation_time": "2025-10-02 18:43:30",
  "guests": "4",
  "note": "Születésnapi tortát hozunk, hűtést igényel."
}
```

### Válasz

-   `200 OK` / `204 No Content`

------------------------------------------------------------------------

## 8. **Foglalás részleges módosítása**

**PATCH** `/reservations/{id}`

### Törzs

``` json
{
  "note": "Születésnapi tortát hozunk, hűtést igényel."
}
```

------------------------------------------------------------------------

## 9. **Foglalás törlése**

**DELETE** `/reservations/{id}`

### Válasz

-   `200 OK` / `204 No Content`

------------------------------------------------------------------------

# Postman változók

  Kulcs        Érték
  ------------ -------------------------------------
  `id`         `1`
  `base_url`   `https://template.postman-echo.com`

------------------------------------------------------------------------

# Megjegyzések

-   A foglalási végpontok mindegyike érvényes **Bearer tokent** igényel.
-   Frissítsd a Postman környezeti változókat a megfelelő működéshez.

------------------------------------------------------------------------
