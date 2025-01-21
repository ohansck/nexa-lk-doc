# User Management API Documentation

## Base URL

```
https://your-api-domain.com
```

## Endpoints

### 1. Register a User

**Endpoint:**

```
POST /users
```

**Description:**
Registers a new user in the system.

**Request Headers:**

```json
{
  "Content-Type": "application/json"
}
```

**Request Body:**

```json
{
  "fullName": "John Doe",
  "email": "john.doe@example.com",
  "linkedinUrl": "https://linkedin.com/in/johndoe",
  "channel": "cloud",
  "comments": "Interested in DevOps",
  "slackUsername": "johndoe123"
}
```

**Response:**

```json
{
  "message": "User registered successfully"
}
```

---

### 2. Update a User

**Endpoint:**

```
PUT /users
```

**Description:**
Updates an existing user's details.

**Request Body:**

```json
{
  "id": "123e4567-e89b-12d3-a456-426614174000",
  "fullName": "John Updated",
  "email": "john.updated@example.com"
}
```

**Response:**

```json
{
  "message": "User updated successfully"
}
```

---

### 3. Get All Users (Paginated)

**Endpoint:**

```
GET /users
```

**Query Parameters:**

```
?lastEvaluatedKey=<key>
```

**Response:**

```json
{
  "Items": [
    {
      "id": "123e4567-e89b-12d3-a456-426614174000",
      "fullName": "John Doe",
      "email": "john.doe@example.com"
    }
  ],
  "LastEvaluatedKey": "abc123"
}
```

---

### 4. Get Users by GSI

**Endpoint:**

```
GET /user
```

**Query Parameters:**

```
?key=EmailIndex&value=john.doe@example.com
```

**Response:**

```json
[
  {
    "id": "123e4567-e89b-12d3-a456-426614174000",
    "fullName": "John Doe",
    "email": "john.doe@example.com"
  }
]
```

---

### 5. Delete a User

**Endpoint:**

```
DELETE /users
```

**Query Parameters:**

```
?id=123e4567-e89b-12d3-a456-426614174000
```

**Response:**

```json
{
  "message": "User deleted successfully"
}
```

---

## Error Responses

### Common Error Response Format

```json
{
  "message": "Error message",
  "error": "Detailed error information"
}
```

**Example:**

```json
{
  "message": "Failed to register user",
  "error": "Email already exists"
}
```

---

## Notes

- All API responses follow JSON format.
- Pagination is supported for listing users.
- Ensure `Content-Type: application/json` is included in the request headers.
- GSIs supported: `EmailIndex`, `CreatedAtIndex`, and `ChannelIndex`.
