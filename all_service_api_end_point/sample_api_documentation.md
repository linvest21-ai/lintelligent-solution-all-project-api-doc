# Sample API Documentation

## Overview
This is a sample API documentation file demonstrating the structure for API endpoints.

## Base URL
```
https://api.lintelligent-solution.com/v1
```

## Authentication
All API requests require authentication using Bearer tokens.

```
Authorization: Bearer <your-token>
```

## Endpoints

### 1. Get User Information
**Endpoint:** `GET /users/{userId}`

**Description:** Retrieves information about a specific user.

**Parameters:**
- `userId` (path, required): The unique identifier of the user

**Request Example:**
```bash
curl -X GET "https://api.lintelligent-solution.com/v1/users/123" \
  -H "Authorization: Bearer your-token-here"
```

**Response Example:**
```json
{
  "id": "123",
  "name": "John Doe",
  "email": "john.doe@example.com",
  "created_at": "2024-01-15T10:30:00Z",
  "status": "active"
}
```

**Status Codes:**
- `200 OK`: User found and returned
- `404 Not Found`: User not found
- `401 Unauthorized`: Invalid or missing token

### 2. Create New Resource
**Endpoint:** `POST /resources`

**Description:** Creates a new resource in the system.

**Request Body:**
```json
{
  "name": "Resource Name",
  "type": "document",
  "metadata": {
    "description": "Resource description",
    "tags": ["tag1", "tag2"]
  }
}
```

**Response Example:**
```json
{
  "id": "resource-456",
  "name": "Resource Name",
  "type": "document",
  "created_at": "2024-09-02T14:45:00Z",
  "status": "created"
}
```

**Status Codes:**
- `201 Created`: Resource successfully created
- `400 Bad Request`: Invalid request body
- `401 Unauthorized`: Invalid or missing token

### 3. List All Services
**Endpoint:** `GET /services`

**Description:** Returns a list of all available services.

**Query Parameters:**
- `page` (optional): Page number for pagination (default: 1)
- `limit` (optional): Number of items per page (default: 20)
- `sort` (optional): Sort order (asc/desc)

**Response Example:**
```json
{
  "services": [
    {
      "id": "service-001",
      "name": "Data Processing Service",
      "status": "active",
      "endpoint": "/services/data-processing"
    },
    {
      "id": "service-002",
      "name": "Analytics Service",
      "status": "active",
      "endpoint": "/services/analytics"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 2,
    "pages": 1
  }
}
```

## Error Handling

All errors follow a consistent format:

```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "details": {
      "field": "Additional error context"
    }
  }
}
```

## Rate Limiting

API requests are limited to:
- 1000 requests per hour for standard users
- 5000 requests per hour for premium users

Rate limit information is included in response headers:
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1693660800
```

## Versioning

The API version is included in the URL path. The current version is `v1`.

## Support

For API support, please contact:
- Email: api-support@lintelligent-solution.com
- Documentation: https://docs.lintelligent-solution.com