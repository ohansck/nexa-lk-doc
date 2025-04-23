# User Service Lambda

A simple AWS Lambda + DynamoDB service for managing user records.

## 📦 Features

- Create, update, fetch by ID
- Query by GSI (email, channel, createdAt)
- Paginated list of all users
- Delete user
- Automatic country detection via CloudFront header

## 🚀 Prerequisites

- Node.js ≥ 14
- AWS account & IAM user with DynamoDB and Lambda permissions
- Serverless Framework or AWS SAM (optional)

## 🔧 Environment Variables

- **USERS_TABLE**: DynamoDB table name for user records


## 📡 API Endpoints

**Base URL:** `https://{api-id}.execute-api.{region}.amazonaws.com/{stage}`

| Method | Path               | Description                     | Body / Query                                                   |
| ------ | ------------------ | ------------------------------- | -------------------------------------------------------------- |
| POST   | `/users/create`    | Create a new user               | JSON with `fullName`, `email`, `linkedinUrl`, `slackUsername?`, `channel` |
| PUT    | `/users/update`    | Update an existing user         | JSON with `id`, `fullName?`, `email?`, `linkedinUrl?`          |
| GET    | `/users`           | Get user by ID                  | Query: `?id={userId}`                                          |
| GET    | `/users/by-index`  | Query users by GSI              | Query: `?index={email|channel|createdAt}&value={searchValue}`  |
| POST   | `/users/all`       | Paginated scan of all users     | JSON: `{ limit?: number, lastEvaluatedKey?: object }`          |
| DELETE | `/users`           | Delete by ID                    | Query: `?id={userId}`                                          |

## 📝 Data Model

DynamoDB item in **USERS_TABLE**:

```json
{
  "id": "uuid",
  "fullName": "string",
  "email": "string",
  "linkedinUrl": "string",
  "slackUsername": "string",
  "channel": "string",
  "country": "string",
  "comments": "string",
  "createdAt": "ISO8601 timestamp",
  "updatedAt": "ISO8601 timestamp"
}
```


## 🐛 Troubleshooting

- **400**: Bad request (missing/invalid parameters)
- **404**: Not found (e.g., user ID does not exist)
- **500**: Internal server error (check CloudWatch logs)

