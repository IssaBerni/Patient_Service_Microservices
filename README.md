# 🏥 Patient Management Microservices

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.0-green)
![Kafka](https://img.shields.io/badge/Kafka-Event--Streaming-black)
![gRPC](https://img.shields.io/badge/gRPC-Protobuf-blue)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791)

## 📖 Overview
This project is a **microservices-based Patient Management System** that demonstrates how to integrate **Spring Boot, Kafka, gRPC, PostgreSQL, API Gateway, and JWT authentication** in a distributed architecture.  

It was designed as a practical example for building **scalable, event-driven, and secure microservices**.

---

## 🏗️ Architecture

### Services
- **Patient Service**
  - Handles patient CRUD operations.
  - Publishes `PatientEvent` messages to Kafka (`patient` topic).
  - Calls **Billing Service** via gRPC to create billing accounts.

- **Billing Service**
  - Receives gRPC requests from the Patient Service.
  - Manages billing accounts for patients.

- **Analytics Service**
  - Consumes Kafka `PatientEvent` messages.
  - Deserializes Protobuf payloads and logs for analytics.

- **Auth Service**
  - Manages users, authentication, and authorization.
  - Uses **Spring Security + JWT**.
  - Stores users in PostgreSQL.

- **API Gateway**
  - Routes client requests to the appropriate microservice.
  - Exposes a single entry point for the system.

---

## ⚙️ Technologies Used
- **Spring Boot** → Core framework for microservices  
- **Spring Security + JWT** → Authentication & Authorization  
- **Spring Data JPA** → Database access  
- **PostgreSQL** → Relational database  
- **Kafka** → Event streaming  
- **gRPC with Protobuf** → High-performance service-to-service communication  
- **Docker & Docker Compose** → Containerization & orchestration  
- **Springdoc OpenAPI** → REST API documentation (Swagger UI)  

---

## 📂 Project Structure

/auth-service
├── model/User.java
├── repository/UserRepository.java
├── security/JwtUtils.java
├── controller/AuthController.java
└── resources/schema.sql

/patient-service
├── model/Patient.java
├── dto/PatientRequestDTO.java
├── dto/PatientResponseDTO.java
├── service/PatientService.java
├── kafka/KafkaProducer.java
└── grpc/BillingServiceGrpcClient.java

/billing-service
├── grpc/BillingServiceImpl.java
└── resources/application.yml

/analytics-service
├── kafka/KafkaConsumer.java
└── resources/application.yml

/api-gateway
└── resources/application.yml

/protos
└── patient_service.proto


---

## 🔗 Communication Flow

1. Client sends a **REST request** → API Gateway.  
2. Gateway routes the request → **Patient Service**.  
3. Patient Service:
   - Saves patient info into **PostgreSQL**.
   - Calls **Billing Service** via gRPC to create billing account.
   - Publishes a **PatientEvent** to Kafka.  
4. **Analytics Service** consumes the Kafka event and logs it.  
5. **Auth Service** ensures security for protected endpoints.

---

## 🗄️ Database Schema

### Auth Service (`users` table)
```sql
CREATE TABLE IF NOT EXISTS "users" (
    id UUID PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role VARCHAR(50) NOT NULL
);


CREATE TABLE IF NOT EXISTS patients (
    id UUID PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255) UNIQUE NOT NULL,
    address TEXT,
    date_of_birth DATE
);


🛠️ How to Run
Prerequisites

-Docker & Docker Compose installed

-Maven installed (optional for manual builds)

Steps
Clone the repository:
git clone <repo-url>
cd patient-management

Build & start all services:
docker-compose up --build


