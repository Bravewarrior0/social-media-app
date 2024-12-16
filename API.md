# Proposed API Endpoints Document

## Title: Social Media API Endpoints

### 1. User Endpoints

#### 1.1 Register a New User

- Endpoint: /api/register/
- Method: POST
- Description: Creates a new user account.
- Request Parameters:

```json
{
  "username": "string",
  "email": "string",
  "password": "string"
}
```

- Response (201 Created):

```json
{
  "id": 1,
  "username": "string",
  "email": "string",
  "token": "jwt-token"
}
```

#### 1.2 User Login

- Endpoint: /api/login/
- Method: POST
- Description: Authenticates a user and provides a JWT token.
- Request Parameters:

```json
{
  "email": "string",
  "password": "string"
}
```

- Response (200 OK):

``` json
{
  "token": "jwt-token"
}
```

#### 1.3 View User Profile

- Endpoint: /api/users/<id>/
- Method: GET
- Description: Fetches details of a specific user.
- Response (200 OK):

```json
{
  "id": 1,
  "username": "string",
  "email": "string",
  "bio": "string",
  "followers_count": 10,
  "following_count": 5
}
```

### 2. Post Endpoints

#### 2.1 Create a Post

- Endpoint: /api/posts/
- Method: POST
- Description: Allows a user to create a new post.
- Request Parameters:

```json
{
  "content": "string"
}
```

- Response (201 Created):

```json
{
  "id": 1,
  "user": 1,
  "content": "string",
  "created_at": "2024-12-16T12:00:00Z"
}
```

#### 2.2 View All Posts

- Endpoint: /api/posts/
- Method: GET
- Description: Fetches all posts.
- Response (200 OK):

```json
[
  {
    "id": 1,
    "user": 1,
    "content": "string",
    "created_at": "2024-12-16T12:00:00Z"
  }
]
```

#### 2.3 Update a Post

- Endpoint: /api/posts/<id>/
- Method: PUT or PATCH
- Description: Updates the content of a post.
- Request Parameters:

```json
{
  "content": "string"
}
```

- Response (200 OK):

```json
{
  "id": 1,
  "user": 1,
  "content": "updated content",
  "created_at": "2024-12-16T12:00:00Z"
}
```

#### 2.4 Delete a Post

- Endpoint: /api/posts/<id>/
- Method: DELETE
- Description: Deletes a specific post.
- Response (204 No Content):

```json
{}
```

### 3. Follow Endpoints

#### 3.1 Follow/Unfollow a User

- Endpoint: /api/follow/
- Method: POST
- Description: Toggles follow/unfollow status for a user.
- Request Parameters:

```json
{
  "user_id": 2
}
```

- Response (200 OK):

```json
{
  "follower_id": 1,
  "following_id": 2,
  "status": "followed" // or "unfollowed"
}
```

### 4. Feed Endpoint

#### 4.1 View User Feed

- Endpoint: /api/feed/
- Method: GET
- Description: Fetches posts from followed users in reverse chronological order.
- Response (200 OK):

```json
[
  {
    "id": 1,
    "user": {
      "id": 2,
      "username": "string"
    },
    "content": "string",
    "created_at": "2024-12-16T12:00:00Z"
  }
]
```
