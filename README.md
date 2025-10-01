
# 🏥 Patient & Auth Service (Spring Boot + Docker + PostgreSQL)

🚀 This project is a **microservice-based application** built with **Spring Boot**, **PostgreSQL**, **Docker**, and **JWT Security**.

It was designed to manage **patients** 🧑‍⚕️ and **users (authentication/authorization)** 🔐 in a clean, modern backend architecture.

---

## ✨ Features

✅ **Authentication Service**

* User entity with `id`, `email`, `password`, `role`
* Passwords stored securely with **BCrypt hashing** 🔒
* JWT-based authentication & authorization

✅ **Patient Service**

* CRUD operations for patients (Create, Read, Update, Delete) 🏥
* RESTful API with JSON responses
* PostgreSQL persistence with **Spring Data JPA**

✅ **Security**

* Role-based access control (`ADMIN`, `USER`)
* Token validation middleware

✅ **Documentation**

* Integrated with **Swagger UI** via `springdoc-openapi` 📖

---

## 🛠️ Tech Stack

* **Java 21** ☕
* **Spring Boot 3** 🌱
* **Spring Security** 🔐
* **Spring Data JPA** 💾
* **PostgreSQL** 🐘
* **H2 (for testing)** 🧪
* **JWT (JSON Web Tokens)** 🎫
* **Docker** 🐳 (containerized build + run)
* **Maven** 📦

---

## 📂 Project Structure

```
patient-auth-project/
│── auth-service/         # 🔐 Authentication & User management
│   ├── model/            # User entity (UUID, email, password, role)
│   ├── repository/       # JPA repository for User
│   ├── security/         # JWT configs, filters, utils
│   └── controller/       # Auth endpoints (login, register)
│
│── patient-service/      # 🏥 Patient management
│   ├── model/            # Patient entity
│   ├── repository/       # Patient repository
│   ├── controller/       # Patient API endpoints
│   └── service/          # Business logic
│
│── docker-compose.yml    # Runs PostgreSQL + services together
│── README.md             # 📖 This documentation
```

---

## 🐳 Running with Docker

1️⃣ Build the JARs

```bash
mvn clean package
```

2️⃣ Build Docker images

```bash
docker build -t auth-service ./auth-service
docker build -t patient-service ./patient-service
```

3️⃣ Start everything with Docker Compose

```bash
docker-compose up
```

4️⃣ Access services:

* Auth Service → `http://localhost:4001`
* Patient Service → `http://localhost:4000`
* Swagger Docs → `http://localhost:4000/swagger-ui.html`

---

## 🔑 Example User (Seeder)

When the DB starts, an **admin user** is inserted:

```sql
INSERT INTO "users" (id, email, password, role)
VALUES ('223e4567-e89b-12d3-a456-426614174006', 'testuser@test.com',
        '$2b$12$7hoRZfJrRKD2nIm2vHLs7OBETy.LWenXXMLKf99W8M4PUwO6KB7fu', 'ADMIN');
```

➡️ Password is **BCrypt-hashed**
➡️ Login with:

* **Email:** `testuser@test.com`
* **Password:** `password123` (example)

---

## 🌍 API Endpoints

### Auth Service

* `POST /auth/register` → Register new user
* `POST /auth/login` → Login & get JWT token

### Patient Service

* `GET /api/patients` → List all patients
* `POST /api/patients` → Add new patient
* `PUT /api/patients/{id}` → Update patient
* `DELETE /api/patients/{id}` → Delete patient

---

## 💡 Why This Project Matters

* Shows **real-world backend skills** 🌍
* Demonstrates **secure authentication with JWT** 🔐
* Uses **microservices + Docker** 🐳 (a must for modern devs)
* Includes **database migrations & seed data** 📦
* Recruiters: It highlights ability to **design scalable, secure systems** ⚡

---

## 🎉 Fun Extras for Recruiters

* 💬 Built with **clean code practices** (layered architecture)
* 🧑‍💻 Easily extendable (add new services or roles)
* 🛠️ Uses industry-standard libraries (Spring Boot, JPA, JWT)
* 🚀 Shows DevOps familiarity (Docker + Compose)

---

## 🚀 Next Steps (if I continued)

* Add frontend (React/Angular) 🎨
* Integrate CI/CD pipeline with GitHub Actions ⚙️
* Add monitoring (Prometheus + Grafana) 📊
* Deploy to cloud (AWS/GCP/Azure) ☁️
