## Overview of GeoStem System

GeoStem is a comprehensive bunker procurement platform designed to simplify and automate the fuel acquisition process for ships. It streamlines the coordination between customers, executives, and fuel sellers, ensuring efficient communication, smooth workflows, and accurate financial management. The system is divided into four key modules: Inquiry, Claims, Invoice, and Report and Analytics.

**Inquiry**: Create, send, and manage fuel inquiries with sellers.

**Claims:** Handle and resolve fuel quality or quantity discrepancies.

**Invoice:** Manage invoice approvals, generation, and payment tracking.

**Report and Analytics:** Provide insights and reports for better decision-making.

## GeoStem Modules

### 1. Inquiry Module
- The Inquiry Module manages the process of creating and handling fuel requests.

### How It Works:
  **1. Customer Request:**

- Customers communicate with executives to request fuel for a specific ship.

### Key details collected:
   -  Ship Name
      
   - Port where fuel is required
     
   - Date of delivery

    
**2. Inquiry Creation:**

- The executive creates an inquiry in the GeoStem system with the collected details.

**3. Sending Inquiry to Sellers:**

   - The system identifies fuel sellers connected to the requested port.
    
   - An email or notification is sent to these sellers, providing details of the fuel inquiry.

**4. Receiving Offers:**
  - Sellers respond to the inquiry with their offer price, fuel quality, and delivery terms.

**5. Seller Nomination:**
   - Executives evaluate all offers and select the seller with the best price and terms.
     
   - The nominated seller is finalized in the system.

**6. Confirmation to Customer:**
   - A confirmation is sent to the customer with the nominated seller's details, including price and delivery information.

### 2. Claims Module

  - The Claims Module handles any discrepancies or issues that arise after the fuel is delivered.

**How It Works:**
**1. Receive Post Bunker Details:**

- After the fuel is delivered, sellers provide documentation, such as:
  
   - Delivery Note
  
   - Fuel Quality Report
  
**2.  Check for Claims:**

- Executives review the delivery documentation and check for claims, such as:
  
   - Fuel Quality Issues: Incorrect specifications.
  
   - Fuel Quantity Issues: Shortage in delivery.
  
   - Other fuel-related discrepancies.

**3. Settlement of Claims:**

- Claims are resolved with the sellers, ensuring adjustments or compensations where necessary.

 ### 3. Invoice Module
- The Invoice Module focuses on the financial aspects of fuel procurement, ensuring seamless invoice management and payment tracking.

**How It Works:**
**1. Receive Invoice from Seller:**

- Sellers submit their invoices for the delivered fuel.
  
**2. Seller Invoice Approval:**

- Executives verify the seller's invoice for accuracy and approve it.
  
**3. Create Invoice for Customers:**

- The system generates an invoice for the customer based on the approved seller invoice.
  
**4. Customer Invoice Approval:**

- The generated invoice is shared with the customer for verification and approval.
  
**5. Payment Acknowledgement:**

- Once payment is received from the customer, a payment acknowledgment is issued.

 ### 4. Report and Analytics Module
- The Report and Analytics Module provides insights and performance tracking across the procurement process.

**How It Works:**
- Generates detailed **reports** on:
  
   - Inquiry volumes and response rates.
     
   - Claims resolution efficiency.
     
   - Invoice approvals and payment statuses.
     
   - Provides analytics to help executives and management make data-driven decisions.

GeoStem simplifies the end-to-end fuel procurement workflow, enabling seamless collaboration between customers, executives, and sellers.


## GeoStem on ABP FrameWork
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




















