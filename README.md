
# Enterprise Stock & Invoicing System

A sophisticated, secure, and multi-tier Spring Boot application designed for comprehensive inventory control, client/supplier management, and automated financial reporting. This project demonstrates advanced backend patterns including JWT security, automated JasperReports generation, and a relational data model for complex business workflows.



## Core Features

### Inventory & Product Management
* **Hierarchical Organization:** Manage products categorized by business types with full CRUD capabilities.
* **Media Support:** Built-in file storage service to handle product images and documentation.
* **Stock Tracking:** Real-time visibility into product availability and category distribution.

### Automated Invoicing & Reporting
* **JasperReports Integration:** Dynamically generate professional PDF documents for:
    * **Customer Invoices:** Detailed financial breakdowns for sales.
    * **Supplier Commands:** Formal purchase orders.
    * **Inventory Summaries:** Comprehensive lists of current stock and product details.
* **Export Capabilities:** High-quality reporting ready for distribution or printing.

### Partner & Command Management
* **Dual Workflow:** Specialized logic for both Client (Sales) and Fournisseur (Procurement) pipelines.
* **Transaction Lifecycle:** Manage the entire flow from Command initiation to Line Items and final Facture (Invoice) generation.
* **Entity Mapping:** Robust relational links between Actors (Clients/Suppliers) and their respective financial records.

### Security & Access Control
* **JWT Authentication:** Stateless security implementation using JSON Web Tokens for API protection.
* **Role-Based Access (RBAC):** Defined permissions for `ADMIN` and `MANAGER` roles to ensure data integrity.
* **Session Safety:** Secure logout service with token blacklisting/revocation.
* **Swagger/OpenAPI:** Fully documented API endpoints for easy integration and testing.

## Technical Stack

| Category | Technology |
| :--- | :--- |
| **Framework** | Spring Boot 3.x (Java 17+) |
| **Security** | Spring Security, JWT (io.jsonwebtoken) |
| **Persistence** | Spring Data JPA, Hibernate |
| **Reporting** | JasperReports |
| **Documentation** | SpringDoc OpenAPI (Swagger) |
| **Tools** | Maven, Lombok |

## Project Structure

```text
src/main/java/ma/iticsolution/stock/
├── controller/          # REST Endpoints (Product, Client, Facture, etc.)
├── entities/            # JPA Models (Actor, Category, Product, Command)
├── repository/          # Data Access Layer (Spring Data JPA)
├── services/            # Business Logic Interfaces
│   └── serciceImpl/     # Implementation of core logic & PDF generation
└── security/            # JWT Configuration, Auth Services, and RBAC
    ├── config/          # JWT Filters and Security Config
    └── user/            # User, Role, and Permission definitions
```

## Installation & Setup

### 1. Prerequisites
* JDK 17 or higher.
* Maven 3.6+.
* A relational database (configured in `application.properties`).

### 2. Configuration
Update `src/main/resources/application.properties` with your database credentials and file storage paths:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/stock_db
spring.jpa.hibernate.ddl-auto=update
# JWT Secret and Expiration
application.security.jwt.secret-key=your_very_secret_key
```

### 3. Execution
```bash
# Clone the repository
git clone <repository-url>
# Build the project
mvn clean install
# Run the application
mvn spring-boot:run
```

## API Usage
1.  **Authenticate:** Send a POST request to `/api/v1/auth/register` or `/login` to receive a JWT.
2.  **Authorize:** Include the token in the `Authorization: Bearer <token>` header for all protected requests.
3.  **Docs:** Explore the full API surface via Swagger UI at `http://localhost:8080/swagger-ui.html`.

---
*Developed by Yousef ELHAID - GLSID Software Engineer.*
