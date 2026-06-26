# API Endpoints & Payloads

## Authentication Module

### Login User
* **URL:** `/api/v1/auth/login`
* **Method:** `POST`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "SecurePassword123"
}