# API Documentation

## Base URL

```
[https://api.example.com/v1 or http://localhost:3000/api]
```

## Authentication

[Describe auth method - Bearer token, API key, session, etc.]

```
Authorization: Bearer <token>
```

---

## Endpoints

### [Resource Name]

#### `GET /resource`

[One-sentence description]

**Headers:**
| Header | Required | Description |
|--------|----------|-------------|
| `Authorization` | Yes | Bearer token |

**Query Parameters:**
| Param | Type | Required | Description |
|-------|------|----------|-------------|
| `page` | integer | No | Page number (default: 1) |
| `limit` | integer | No | Items per page (default: 20) |

**Response: 200 OK**
```json
{
  "data": [],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 100
  }
}
```

**Errors:**
| Status | Description |
|--------|-------------|
| 401 | Unauthorized - invalid or missing token |
| 500 | Internal server error |

**Example:**
```bash
curl -H "Authorization: Bearer TOKEN" https://api.example.com/v1/resource
```

---

#### `POST /resource`

[One-sentence description]

**Request Body:**
```json
{
  "name": "string (required)",
  "description": "string (optional)"
}
```

**Response: 201 Created**
```json
{
  "id": "uuid",
  "name": "string",
  "createdAt": "ISO 8601"
}
```

**Errors:**
| Status | Description |
|--------|-------------|
| 400 | Bad request - validation error |
| 401 | Unauthorized |
| 409 | Conflict - resource already exists |
