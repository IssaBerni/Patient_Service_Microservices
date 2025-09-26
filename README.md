📖 Patient Management Microservices – Documentation
🚀 Overview

This project is a microservices-based patient management system designed to demonstrate the integration of Spring Boot, gRPC, Kafka, PostgreSQL, and API Gateway.

The goal was to build a modular system where services communicate via synchronous (gRPC) and asynchronous (Kafka) channels, providing a scalable foundation for healthcare or analytics platforms.

🏗️ Architecture
Services:

Patient Service

Core service handling patient CRUD operations.

Communicates with Billing Service via gRPC.

Publishes PatientEvents to Kafka (patient topic).

Billing Service

Listens for gRPC requests from the Patient Service.

Manages billing accounts tied to patients.

Analytics Service

Kafka consumer that listens to patient events.

Deserializes Protobuf messages and logs them for analysis.

Auth Service

Handles user authentication and authorization.

Uses Spring Security + JWT.

Stores users in PostgreSQL.

API Gateway

Routes requests to backend services.

Provides a single entry point for clients.

⚙️ Technologies

Spring Boot – Core framework

Spring Security + JWT – Authentication & Authorization

Spring Data JPA – Database interaction

PostgreSQL – Persistent storage

Kafka – Event streaming

gRPC (Protobuf) – Inter-service communication

Docker & Docker Compose – Containerization and orchestration

Springdoc OpenAPI – API documentation (Swagger UI)

📂 Project Structure
