# Secured RESTful User Management API
## Getting Started

### 1. Clone the Repository
git clone https://github.com/JuanGonzalezCuadros/user-management-api.git

cd user-management-api

### 2. Create a MySQL database
CREATE DATABASE user_management;

### 3. Configure application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/user_management

spring.datasource.username=your_username

spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true

spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

### 4. Build and Run
./mvnw spring-boot:run


### API Endpoints
### Register a New User
POST /auth/register

{
"username": "johndoe",
"password": "password123"
}

Response: "User registered successfully"

### Login (Authenticate)
POST /auth/login

{
"username": "johndoe",
"password": "password123"
}

Response: {"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."}

### User Endpoints

All secured endpoints require the Authorization header:

Authorization: Bearer <your-jwt-token>

GET /users/me

Role Required: USER or ADMIN

Response: {
"id": 1,
"username": "johndoe",
"role": "USER"
}

### Get User Info
GET /users/me

Role Required: USER or ADMIN

Response: {
"id": 1,
"username": "johndoe",
"role": "USER"
}

### Update User Info
PUT /users/update

{
"username": "john_updated",
"password": "newpass456"
}

### Delete Account (Admin Only)
DELETE /users/delete/{id}

Role Required: ADMIN