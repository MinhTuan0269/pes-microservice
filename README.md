# PES Microservice Backend

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker)](https://www.docker.com/)
[![Architecture](https://img.shields.io/badge/Architecture-Microservices-FF9900)]()
[![Course](https://img.shields.io/badge/Course-PRM391-4CAF50)]()

> **Note:** This project is explicitly developed for educational and learning purposes as a requirement for the **PRM391** course. It serves as the backend infrastructure for our mobile application project.

## 📖 Overview

**PES Microservice** is a scalable backend system built on the **.NET 8** ecosystem, following a **Microservices Architecture**. It provides robust, secure, and independent APIs designed to support our mobile application (like Ameko). The system utilizes an API Gateway pattern to route traffic efficiently to corresponding downstream microservices.

## 🏗 Architecture & Services

The system is split into several independent microservices, connected behind an API Gateway:

- **Gateway.API**: Acts as the single entry point for all client requests using **YARP (Yet Another Reverse Proxy)**. It routes requests to the appropriate backend service.
- **AuthService.API**: Manages user authentication, authorization, and issues JSON Web Tokens (JWT) for secure API access.
- **ParentService.API**: Handles functionalities related to parent user profiles and data.
- **SyllabusService.API**: Manages educational syllabuses, courses, and related content.
- **TermAdmissionManagement.API**: Handles school terms, admission processes, and enrollments.

Each microservice is built using **Clean Architecture** principles (divided into `API`, `Application`, `Domain`, and `Infrastructure` / `Repositories` layers) to ensure separation of concerns and maintainability.

## 🛠 Technologies & Tools

- **Framework**: .NET 8.0 ASP.NET Core
- **API Gateway**: YARP (Yet Another Reverse Proxy)
- **Database ORM**: Entity Framework Core 9 (SQL Server)
- **Authentication**: JWT (JSON Web Tokens)
- **Object Mapping**: AutoMapper
- **Containerization**: Docker & Docker Compose
- **API Documentation**: Swagger / OpenAPI

## 🚀 Getting Started

### Prerequisites

To run this project locally, ensure you have the following installed:
- [.NET 8.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (for containerized execution)
- IDE (Visual Studio 2022, JetBrains Rider, or VS Code)

### Running the Application

**Option 1: Using Docker Compose (Recommended)**

The easiest way to run the entire microservices suite is via Docker Compose, which will spin up all the APIs and the Gateway together.

1. Open a terminal at the root of the project directory.
2. Run the following command:
   ```bash
   docker-compose up -d --build
   ```
3. Once the containers are running, you can access the **Gateway API** or individual Swagger UI pages to test the endpoints.

**Option 2: Running Locally via IDE**

1. Open the `pes-microservices.sln` solution file in Visual Studio.
2. Ensure that multiple startup projects are configured (Right-click Solution -> Set Startup Projects -> Multiple startup projects).
3. Set `Gateway.API`, `AuthService.API`, `ParentService.API`, `SyllabusService.API`, and `TermAdmissionManagement.API` to **Start**.
4. Press `F5` to run the services.

## 🔒 Authentication Flow

1. Clients send credentials to the `AuthService` (via the Gateway).
2. Upon successful authentication, a JWT is returned.
3. For subsequent requests to protected endpoints, clients must include the JWT in the `Authorization` header (`Bearer <token>`).
4. The API Gateway routes the request, and the specific microservice validates the token using the shared secret/configuration.

## 📚 Course Information

- **Course:** PRM391 (Mobile Cross-Platform Development)
- **Purpose:** Learning and demonstrating backend development, microservices architecture, and API integration for mobile clients.
