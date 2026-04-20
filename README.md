# 🛒 Achat — Purchase Management API

A RESTful backend for purchase and inventory management, built with **Spring Boot 2.5.3** and **Java 8**.  
Developed as part of the **DevOps** module at ESPRIT.

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Swagger UI](#swagger-ui)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

- 📦 **Product management** — CRUD operations and stock assignment
- 🗂️ **Product category management**
- 🏭 **Supplier (Fournisseur) management** — with sector of activity assignment
- 🧾 **Invoice (Facture) management** — creation, cancellation, operator assignment, and recovery rate calculation
- 💰 **Payment (Reglement) management** — with revenue calculation between two dates
- 📊 **Stock management** — CRUD and product-to-stock assignment
- 👤 **Operator management** — CRUD for internal users
- 🏢 **Sector of Activity management**
- 📖 **Swagger UI** — auto-generated interactive API documentation

---

## 🛠️ Tech Stack

| Technology | Version |
|---|---|
| Java | 1.8 |
| Spring Boot | 2.5.3 |
| Spring Data JPA | - |
| Hibernate | - |
| MySQL | - |
| Lombok | - |
| Springfox Swagger | 3.0.0 |
| Maven | 3.8+ |

---

## 🚀 Getting Started

### Prerequisites

- Java 8+
- Maven 3.8+
- MySQL running locally

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/achat.git
cd achat

# Build the project
mvn clean install

# Run the application
mvn spring-boot:run
```

The API will be available at: `http://localhost:8089/SpringMVC`

---

## ⚙️ Configuration

Edit `src/main/resources/application.properties`:

```properties
# Server
server.port=8089
server.servlet.context-path=/SpringMVC

# Database
spring.datasource.url=jdbc:mysql://localhost:3306/achat_db
spring.datasource.username=root
spring.datasource.password=your_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA / Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

---

## 📡 API Endpoints

Base URL: `http://localhost:8089/SpringMVC`

### 📦 Products — `/produit`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/produit/retrieve-all-produits` | List all products |
| `GET` | `/produit/retrieve-produit/{produit-id}` | Get a product by ID |
| `POST` | `/produit/add-produit` | Add a new product |
| `PUT` | `/produit/modify-produit` | Update a product |
| `DELETE` | `/produit/remove-produit/{produit-id}` | Delete a product |
| `PUT` | `/produit/assignProduitToStock/{idProduit}/{idStock}` | Assign a product to a stock |

### 🗂️ Product Categories — `/categorieProduit`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/categorieProduit/retrieve-all-categorieProduit` | List all product categories |
| `GET` | `/categorieProduit/retrieve-categorieProduit/{id}` | Get a category by ID |
| `POST` | `/categorieProduit/add-categorieProduit` | Add a new category |
| `PUT` | `/categorieProduit/modify-categorieProduit` | Update a category |
| `DELETE` | `/categorieProduit/remove-categorieProduit/{id}` | Delete a category |

### 🏭 Suppliers — `/fournisseur`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/fournisseur/retrieve-all-fournisseurs` | List all suppliers |
| `GET` | `/fournisseur/retrieve-fournisseur/{id}` | Get a supplier by ID |
| `POST` | `/fournisseur/add-fournisseur` | Add a new supplier |
| `PUT` | `/fournisseur/modify-fournisseur` | Update a supplier |
| `DELETE` | `/fournisseur/remove-fournisseur/{id}` | Delete a supplier |
| `PUT` | `/fournisseur/assignSecteurActiviteToFournisseur/{idSecteur}/{idFournisseur}` | Assign a sector to a supplier |

### 🧾 Invoices — `/facture`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/facture/retrieve-all-factures` | List all invoices |
| `GET` | `/facture/retrieve-facture/{id}` | Get an invoice by ID |
| `POST` | `/facture/add-facture` | Add a new invoice |
| `PUT` | `/facture/cancel-facture/{id}` | Cancel an invoice |
| `GET` | `/facture/getFactureByFournisseur/{id}` | Get invoices by supplier |
| `PUT` | `/facture/assignOperateurToFacture/{idOperateur}/{idFacture}` | Assign an operator to an invoice |
| `GET` | `/facture/pourcentageRecouvrement/{startDate}/{endDate}` | Get recovery rate between two dates |

### 💰 Payments — `/reglement`

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/reglement/add-reglement` | Add a new payment |
| `GET` | `/reglement/retrieve-all-reglements` | List all payments |
| `GET` | `/reglement/retrieve-reglement/{id}` | Get a payment by ID |
| `GET` | `/reglement/retrieveReglementByFacture/{facture-id}` | Get payments by invoice |
| `GET` | `/reglement/getChiffreAffaireEntreDeuxDate/{startDate}/{endDate}` | Get revenue between two dates |

### 📊 Stock — `/stock`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/stock/retrieve-all-stocks` | List all stocks |
| `GET` | `/stock/retrieve-stock/{id}` | Get a stock by ID |
| `POST` | `/stock/add-stock` | Add a new stock |
| `PUT` | `/stock/modify-stock` | Update a stock |
| `DELETE` | `/stock/remove-stock/{id}` | Delete a stock |

### 👤 Operators — `/operateur`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/operateur/retrieve-all-operateurs` | List all operators |
| `GET` | `/operateur/retrieve-operateur/{id}` | Get an operator by ID |
| `POST` | `/operateur/add-operateur` | Add a new operator |
| `PUT` | `/operateur/modify-operateur` | Update an operator |
| `DELETE` | `/operateur/remove-operateur/{id}` | Delete an operator |

### 🏢 Sectors of Activity — `/secteurActivite`

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/secteurActivite/retrieve-all-secteurActivite` | List all sectors |
| `GET` | `/secteurActivite/retrieve-secteurActivite/{id}` | Get a sector by ID |
| `POST` | `/secteurActivite/add-secteurActivite` | Add a new sector |
| `PUT` | `/secteurActivite/modify-secteurActivite` | Update a sector |
| `DELETE` | `/secteurActivite/remove-secteurActivite/{id}` | Delete a sector |

---

## 📁 Project Structure

```
src/
└── main/
    ├── java/
    │   └── tn/esprit/rh/achat/
    │       ├── controllers/
    │       │   ├── CategorieProduitController.java
    │       │   ├── FactureRestController.java
    │       │   ├── FournisseurRestController.java
    │       │   ├── OperateurController.java
    │       │   ├── ProduitRestController.java
    │       │   ├── ReglementRestController.java
    │       │   ├── SecteurActiviteController.java
    │       │   └── StockRestController.java
    │       ├── entities/
    │       │   ├── CategorieProduit.java
    │       │   ├── CategorieFournisseur.java
    │       │   ├── DetailFacture.java
    │       │   ├── DetailFournisseur.java
    │       │   ├── Facture.java
    │       │   ├── Fournisseur.java
    │       │   ├── Operateur.java
    │       │   ├── Produit.java
    │       │   ├── Reglement.java
    │       │   ├── SecteurActivite.java
    │       │   └── Stock.java
    │       ├── repositories/
    │       ├── services/
    │       └── AchatApplication.java
    └── resources/
        └── application.properties
```

---

## 📖 Swagger UI

Once the application is running, access the interactive API documentation at:

```
http://localhost:8089/SpringMVC/swagger-ui/index.html
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the project
2. Create your branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add my feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

> 🎓 Developed at **ESPRIT** — School of Private Engineering and Technology, Tunisia.
