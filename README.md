# smart-grocery-system

# Smart Grocery Management System

This project consists of two Spring Boot-based microservices: `user-service` and `inventory-service`. It demonstrates the use of Docker and Kubernetes (Minikube) for containerization and orchestration, with MySQL as the database for each service.

## 🧱 Microservices Overview

### 1. User-Service
Handles all operations related to users in the system.

#### Exposed APIs
- `POST /users/addNewUser` - Add a new user
- `GET /users/getAllUsers` - Fetch all users
- `GET /users/getUser/{userId}` - Get user by ID
- `DELETE /users/deleteUser/{userId}` - Delete user by ID

### 2. Inventory-Service
Manages inventory items, updates, and records.

#### Exposed APIs
- `GET /inventory/getAllItems` - Fetch all inventory items
- `POST /inventory/addItem` - Add a new inventory item
- `PUT /inventory/updateItem/{id}` - Update item by ID
- `DELETE /inventory/deleteItem/{id}` - Delete item by ID

## 🛠️ Technologies Used

| Component              | Technology/Tool       |
|------------------------|------------------------|
| Language               | Java (JDK 17)          |
| Framework              | Spring Boot            |
| Build Tool             | Maven                  |
| Databases              | MySQL (Dockerized)     |
| API Testing            | Postman                |
| Containerization       | Docker                 |
| Orchestration          | Kubernetes (Minikube)  |
| IDE / Code Editor      | IntelliJ IDEA / VS Code|
| Version Control        | Git & GitHub           |

## 🚀 Running the Services with Docker

### Docker Build Commands

```bash
docker build -t user-service:latest 
docker build -t inventory-service:latest

Docker Network Creation
docker network create smartgrocery-net
Run Containers
# User MySQL DB
docker run --name user-mysql-db --network smartgrocery-net -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_DATABASE=userdb -p 3308:3306 -d mysql:8.0

# Inventory MySQL DB
docker run --name inventory-mysql-db --network smartgrocery-net -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_DATABASE=inventorydb -p 3306:3306 -d mysql:8.0

# User Service
docker run --name user-service --network smartgrocery-net -p 8082:8082 user-service:latest

# Inventory Service
docker run --name inventory-service --network smartgrocery-net -p 8083:8083 inventory-service:latest

