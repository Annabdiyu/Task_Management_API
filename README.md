Here is a README file based on your HTML structure for the Task Management API:

---

# Task Management API

This API allows users to manage tasks, categories, and user accounts efficiently through a RESTful service. It supports features such as task creation, updating, deletion, and categorization, alongside user account management like login, registration, and password reset.

## Base URL
The base URL for all API endpoints is:

```
http://127.0.0.1:8000/api/
```

## Authentication
This API uses token-based authentication. Users must log in to obtain a token, which is then included in the headers of subsequent requests.

### Authentication Endpoints

#### Login
- **Endpoint**: `/accounts/login/`
- **Method**: `POST`
- **Request Body**:
    ```json
    {
        "username": "new_user",
        "password": "your_password"
    }
    ```
- **Response**:
    ```json
    {
        "token": "your_token_here"
    }
    ```

#### Register
- **Endpoint**: `/register/`
- **Method**: `POST`
- **Request Body**:
    ```json
    {
        "username": "new_user",
        "email": "user@example.com",
        "password": "your_password"
    }
    ```
- **Response**:
    ```json
    {
        "id": 1,
        "username": "new_user",
        "email": "user@example.com"
    }
    ```

#### Logout
- **Endpoint**: `/logout/`
- **Method**: `POST`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Response**: `204 No Content`

#### Password Reset Request
- **Endpoint**: `/password-reset/`
- **Method**: `POST`
- **Request Body**:
    ```json
    {
        "email": "user@example.com"
    }
    ```
- **Response**:
    ```json
    {
        "message": "If an account with that email exists, a password reset link has been sent."
    }
    ```

#### Password Reset Confirmation
- **Endpoint**: `/password-reset-confirm/`
- **Method**: `POST`
- **Request Body**:
    ```json
    {
        "Uidb64": "NQ",
        "Token": "reset_token",
        "new_password": "new_password"
    }
    ```
- **Response**:
    ```json
    {
        "message": "Password has been reset."
    }
    ```

---

## Task Management Endpoints

### List All Tasks
- **Endpoint**: `/tasks/list/`
- **Method**: `GET`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Response**:
    ```json
    [
        {
            "id": 12,
            "title": "Complete project",
            "description": "Finalize and submit the project.",
            "due_date": "2025-01-15T12:00:00Z",
            "priority": "High",
            "status": "Pending",
            "completed_at": null,
            "user": 14,
            "category": null
        }
    ]
    ```

### Create a New Task
- **Endpoint**: `/tasks/create/`
- **Method**: `POST`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Request Body**:
    ```json
    {
        "user": "2",
        "title": "Complete project",
        "description": "Finalize and submit the project.",
        "due_date": "2025-01-15T12:00:00Z",
        "priority": "High",
        "status": "Pending"
    }
    ```
- **Response**:
    ```json
    {
        "id": 11,
        "title": "Complete project",
        "description": "Finalize and submit the project.",
        "due_date": "2025-01-15T12:00:00Z",
        "priority": "High",
        "status": "Pending",
        "completed_at": null,
        "user": 5,
        "category": null
    }
    ```

### Update a Specific Task
- **Endpoint**: `/tasks/{id}/`
- **Method**: `PUT`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Request Body**:
    ```json
    {
        "title": "Updated Task",
        "description": "Updated description",
        "due_date": "2025-10-11T00:00:00Z",
        "priority": "Low",
        "status": "Pending",
        "category": null,
        "recurrence": "None"
    }
    ```
- **Response**:
    ```json
    {
        "id": 1,
        "title": "Updated Task",
        "description": "Updated description",
        "due_date": "2024-10-01T00:00:00Z",
        "priority": "Low",
        "status": "Pending",
        "category": null,
        "recurrence": "None"
    }
    ```

### Delete a Specific Task
- **Endpoint**: `/tasks/{id}/`
- **Method**: `DELETE`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Response**: `204 No Content`

---

## Category Management Endpoints

### List All Categories
- **Endpoint**: `/categories/list/`
- **Method**: `GET`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Response**:
    ```json
    [
        {
            "id": 5,
            "name": "Electronics"
        }
    ]
    ```

### Create a New Category
- **Endpoint**: `/categories/create/`
- **Method**: `POST`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Request Body**:
    ```json
    {
        "name": "Electronics"
    }
    ```
- **Response**:
    ```json
    {
        "id": 5,
        "name": "Electronics"
    }
    ```

### Update a Specific Category
- **Endpoint**: `/categories/{id}/`
- **Method**: `PUT`
- **Headers**:
    ```text
    Authorization: Token your_token_here
    ```
- **Request Body**:
    ```json
    {
        "name": "Updated Category"
    }
    ```
- **Response**:
    ```json
    {
        "id": 5,
        "name": "Updated Category"
    }
    ```

---

## Conclusion
This API provides an efficient way to manage tasks and categories, supporting a variety of operations for users and administrators. It uses token-based authentication to secure access and provide a seamless user experience.

---

