# API Documentation

## Description
This API is used to check if a Free Fire account is banned or not. Designed for developers and community admins, it offers easy and quick integration to monitor the status of Free Fire accounts. Developed with FastAPI and deployed on Vercel, this API is powerful, reliable, and ready to use.

## 🪪 Account Information

### Endpoint: `/check_ban/uid=`  
**Method**: `GET`

**Description**:  
This endpoint retrieves account information based on the specified region and user ID. It checks whether a player is banned or not, and if so, the period of the ban.

### ☑️ Query Parameters

| Parameter | Type   | Required | Description     |
|-----------|--------|----------|-----------------|
| `uid`     | int    | Yes      | The user ID.    |

### 📨 Request Example

```bash
GET https://api.paulalfredo.me/check_ban/uid=305000592
```
This request checks whether the account with UID 305000592 is banned or not.


## Points d'API

### `GET /check_ban/uid={uid}`

Verifies if a user with the given UID is banned.

#### Parameters
- `uid`  (required): The unique identifier of the user. This parameter must contain only numeric characters.

#### Responses

##### Success (ID found and ban status)
When the account is banned:
```json
{
  "error": false,
  "status": 200,
  "msg": "id_found",
  "data": {
    "is_banned": 1,
    "id": "2953958574",
    "period": 3
  }
}

```
is_banned: 1 indicates the user is banned. 0 means the user is not banned.

Exemple lorsque le compte n'est pas banni
```json
{
  "error": false,
  "status": 200,
  "msg": "id_found",
  "data": {
    "is_banned": 0,
    "id": "305000592",
    "period": 0
  }
}
```
is_banned: 0 indicates the user is not banned.*

ID Not Found
```json

{
  "error": false,
  "status": 204,
  "msg": "no_content",
  "data": {
    "id": "2953958574"
  }
}
```
msg: no_content means the requested ID does not exist in the database

Error Responses
Possible Error Responses
UID is empty: 
```json
{
  "error": true,
  "status": 400,
  "msg": "invalid_uid",
  "details": "The uid parameter is empty."
}
```
Invalid UID Format:
```json
{
  "error": true,
  "status": 400,
  "msg": "invalid_uid_format",
  "details": "The uid parameter must contain only numeric characters."
}

```
Internal Server Error:

```json
{
  "error": true,
  "status": 500,
  "msg": "internal_server_error",
  "details": "An unexpected error occurred on the server. Please try again later."
}
```
ID Not Found in the Database:
```json
{
  "error": true,
  "status": 404,
  "msg": "id_not_found",
  "details": "The requested ID does not exist in our database."
}
```

This project is licensed under the MIT License. See the LICENSE file for details.



