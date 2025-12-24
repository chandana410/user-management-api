# User Management API

![Java](https://img.shields.io/badge/Java-17-blue.svg)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0.1-brightgreen.svg)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

A comprehensive RESTful backend API for managing users with full CRUD operations. Built with Java Spring Boot, Spring Data JPA, and MySQL.

## Features

✅ **Complete CRUD Operations** - Create, Read, Update, and Delete users
✅ **RESTful API Design** - Clean and intuitive API endpoints
✅ **MySQL Database** - Persistent data storage with JPA/Hibernate
✅ **Email Validation** - Unique email constraint for user management
✅ **Timestamp Tracking** - Automatic creation and update timestamps
✅ **Active Status** - Track user status (active/inactive)
✅ **CORS Support** - Cross-Origin Resource Sharing enabled
✅ **Error Handling** - Comprehensive HTTP error responses

## Technologies Used

- **Language**: Java 17
- **Framework**: Spring Boot 4.0.1
- **ORM**: Spring Data JPA with Hibernate
- **Database**: MySQL 8.0
- **Build Tool**: Maven/Gradle
- **Additional Libraries**: Lombok (reducing boilerplate code)

## Project Structure

```
user-management-api/
├── src/main/java/com/usermanagement/user/management/api/
│   ├── model/
│   │   └── User.java                 # User Entity
│   ├── repository/
│   │   └── UserRepository.java       # JPA Repository
│   ├── controller/
│   │   └── UserController.java       # REST Controller
│   └── UserManagementApiApplication.java  # Main Application
├── src/main/resources/
│   └── application.properties        # Database Configuration
├── pom.xml                          # Maven Dependencies
└── README.md                        # Project Documentation
```

## API Endpoints

### 1. Get All Users
```http
GET /api/users
```
**Response**: List of all users in the system

### 2. Get User by ID
```http
GET /api/users/{id}
```
**Parameters**: 
- `id` (Path) - User ID

**Response**: User object with specified ID

### 3. Get User by Email
```http
GET /api/users/email/{email}
```
**Parameters**: 
- `email` (Path) - User email address

**Response**: User object with specified email

### 4. Create New User
```http
POST /api/users
Content-Type: application/json

{
  "email": "john@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "password": "secure_password"
}
```
**Response**: Created user object with generated ID

### 5. Update User
```http
PUT /api/users/{id}
Content-Type: application/json

{
  "firstName": "Jane",
  "lastName": "Smith",
  "password": "new_password",
  "isActive": true
}
```
**Response**: Updated user object

### 6. Delete User
```http
DELETE /api/users/{id}
```
**Response**: Success message

## Database Schema

```sql
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    email VARCHAR(255) UNIQUE NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    password VARCHAR(255) NOT NULL,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

## Installation & Setup

### Prerequisites
- Java 17 or higher
- MySQL 8.0
- Maven 3.6+

### Steps

1. **Clone the Repository**
```bash
git clone https://github.com/chandana410/user-management-api.git
cd user-management-api
```

2. **Create MySQL Database**
```sql
CREATE DATABASE user_management_db;
USE user_management_db;
```

3. **Configure Database Connection**
Edit `src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/user_management_db
spring.datasource.username=root
spring.datasource.password=your_password
```

4. **Build the Project**
```bash
mvn clean install
```

5. **Run the Application**
```bash
mvn spring-boot:run
```

The API will be available at `http://localhost:8080`

## Example Requests

### Create User
```bash
curl -X POST http://localhost:8080/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "firstName": "John",
    "lastName": "Doe",
    "password": "password123"
  }'
```

### Get All Users
```bash
curl http://localhost:8080/api/users
```

### Get User by ID
```bash
curl http://localhost:8080/api/users/1
```

### Get User by Email
```bash
curl http://localhost:8080/api/users/email/john@example.com
```

### Update User
```bash
curl -X PUT http://localhost:8080/api/users/1 \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Jane",
    "lastName": "Smith",
    "password": "newpassword123"
  }'
```

### Delete User
```bash
curl -X DELETE http://localhost:8080/api/users/1
```

## API Response Examples

### Success Response (200 OK)
```json
{
  "id": 1,
  "email": "john@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "password": "password123",
  "isActive": true,
  "createdAt": "2025-12-24T11:00:00",
  "updatedAt": "2025-12-24T11:00:00"
}
```

### Error Response (404 Not Found)
```json
"User not found with ID: 999"
```

### Error Response (400 Bad Request)
```json
"Email already exists"
```

## Features Implemented

- ✅ User Entity with JPA Annotations
- ✅ User Repository with Custom Queries
- ✅ REST Controller with All CRUD Operations
- ✅ Exception Handling & Error Messages
- ✅ Request Validation
- ✅ Timestamp Automation (Created At, Updated At)
- ✅ CORS Configuration
- ✅ Database Configuration

## Author

**Chandana Kota**
- GitHub: [@chandana410](https://github.com/chandana410)
- Email: chandana@example.com

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, issues, or suggestions, please open an issue on the GitHub repository.

---

**Last Updated**: December 24, 2025
**Version**: 1.0.0
