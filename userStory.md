# User Story: User Management

## Title

As a user, I want to manage my profile so that I can keep my information up to date.

## Acceptance Criteria

### 1. Register a User

- **Endpoint:** `POST /users`
- **Request:**
  - Full name, email, LinkedIn URL, channel, comments, and Slack username.
- **Response:**
  - Success message upon successful registration.
  - Error message if registration fails.

### 2. Update User Information

- **Endpoint:** `PUT /users`
- **Request:**
  - User ID and updated fields (full name, email, etc.).
- **Response:**
  - Success message on update.
  - Error message if update fails.

### 3. Get All Users (Paginated)

- **Endpoint:** `GET /users`
- **Request:**
  - Optional `lastEvaluatedKey` for pagination.
- **Response:**
  - List of users with pagination support.

### 4. Get Users by Attribute

- **Endpoint:** `GET /user`
- **Request:**
  - Query by email, createdAt, or channel.
- **Response:**
  - List of matching users.

### 5. Delete a User

- **Endpoint:** `DELETE /users`
- **Request:**
  - User ID as a query parameter.
- **Response:**
  - Success message on deletion.
  - Error message if deletion fails.

## Notes

- All requests and responses must be in JSON format.
- Ensure proper error handling and validations on the frontend.
- Use provided API documentation for detailed field descriptions.
