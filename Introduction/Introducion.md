## Overview of GeoStem System

GeoStem is a comprehensive bunker procurement platform designed to simplify and automate the fuel acquisition process for ships. It streamlines the coordination between customers, executives, and fuel sellers, ensuring efficient communication, smooth workflows, and accurate financial management. The system is divided into four key modules: Inquiry, Claims, Invoice, and Report and Analytics.

**Inquiry**: Create, send, and manage fuel inquiries with sellers.

**Claims:** Handle and resolve fuel quality or quantity discrepancies.

**Invoice:** Manage invoice approvals, generation, and payment tracking.

**Report and Analytics:** Provide insights and reports for better decision-making.
GeoStem simplifies the end-to-end fuel procurement workflow, enabling seamless collaboration between customers, executives, and sellers.

## Introduction
The **GEOSTEM** project is built on the **ABP (ASP.NET Boilerplate Platform)**. ABP is an open-source application framework built on top of .NET. ABP enforces a layered architecture including Application, Domain, Infrastructure, and Presentation layers promoting clean separation of concerns and making it easier to manage dependencies and maintain code. It supports **Domain-Driven Design (DDD)** principles and offers guidance for defining entities, value objects, and domain services. . ABP allows to develop applications as a collection of independent modules, which makes it easy to add, replace, or extend functionality. Modules can be reused across multiple projects, and ABP provides a set of pre-built modules to accelerate development.

 The  **GEOSTEM** project consists of two key components: a backend API developed with **ASP.NET-Core** and a front-end UI developed with **Angular**. Both components are built on the **ABP Framework**. 
 
![image](https://github.com/user-attachments/assets/2b07911f-5a46-4136-aad4-695b0dd2b12a)

### Backend: ASP.NET Core Structure

![image](https://github.com/user-attachments/assets/29dd8edd-baac-41f1-ac24-04a30556c0af)

**Application:** The Application Layer is one of the core architectural layers. This layer serves as the primary bridge between the Presentation Layer (UI) and the Domain Layer.

**Application Contracts:** Application Contracts are a layer that defines the structure and data types for communication between the Application Layer and external consumers. It is essentially an interface layer containing definitions and data transfer objects (DTOs) that specify the methods, parameters, and results of application services.

**DbMigrator:** The DbMigrator is a tool or utility used for applying database schema migrations and seeding initial data. It ensures that the database structure is up to date with the latest changes in the application's model, based on migrations defined in the code. This is essential for keeping the database schema in sync with the application's evolving business logic.

**Domain:** This layer is crucial for implementing the business logic, rules, and constraints that make up the application's core functionality. It encapsulates entities, value objects, aggregates, and domain services, focusing on the problem the application is solving rather than technical details.  

**Domain Shared:** This Layer  contains code shared across all modules and layers in the solution.

**Entity Framework Core:** This layer used as an ORM (Object-Relational Mapper) to interact with databases. It integrates seamlessly with ABP, enabling developers to define database entities, repositories, and services easily.

**HttpApi:**  This layer is responsible for exposing the application’s services and functionality over HTTP  enabling clients (such as web, mobile, or other microservices) to interact with the backend.

**HttpApi.Client:** It acts as a client-side HTTP library, allowing other services or applications to access API endpoints defined in the ABP HttpApi layer in a strongly typed and consistent way.

**HttpApi.Host:** . It serves as the main entry point for handling HTTP requests, hosting controllers to handle client requests and interact with the application layer.




















