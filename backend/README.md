[English version below](#buffet-api-template)

# Buffet API Šablona

Jednoduchá a přehledná šablona Java Spring Boot REST API navržená pro začínající vývojáře k učení a dalšímu rozšiřování. Tento projekt poskytuje základní CRUD (Vytvořit, Přečíst, Aktualizovat, Odstranit) funkcionalitu pro správu produktů v bufetu.

## 🚀 Použité technologie

- **Java 17**: Stabilní LTS verze jazyka Java.
- **Spring Boot 4**: Framework pro tvorbu aplikací připravených pro produkci.
- **Spring Data JPA**: Pro snadné databázové operace.
- **MySQL**: Spolehlivá relační databáze.
- **Lombok**: Pro snížení množství duplicitního kódu (gettery, settery atd.).
- **Docker**: Pro snadné nasazení a konzistenci prostředí.

## 📋 Požadavky

Než začnete, ujistěte se, že máte nainstalováno následující:
- **Java 17** (nebo kompatibilní JDK)
- **Docker & Docker Compose**

## 🛠️ Začínáme

### 🟢 Možnost 1: Lokální vývoj (Doporučeno)

Toto je preferovaný způsob pro vývojáře. Databázi spustíte v Dockeru a aplikaci lokálně na svém stroji pro rychlejší vývojové cykly.

1.  **Spuštění databáze**:
    - **IDEA**: Použijte spouštěcí konfiguraci **Docker DB**.
    - **Skript**: Spusťte `./start-db.sh` (Linux/macOS) nebo `start-db.bat` (Windows).
    - **Ručně**: `docker compose -f docker/compose.yaml up -d mysql`
2.  **Spuštění aplikace**:
    - **IDEA**: Použijte spouštěcí konfiguraci **BuffetApplication**.
    - **Skript**: Spusťte `./run-app.sh` (Linux/macOS) nebo `run-app.bat` (Windows).
    - **Ručně**: `./mvnw spring-boot:run`

> [!IMPORTANT]
> Tato šablona nepodporuje **live reload**. Pokud provedete změny v kódu, je nutné aplikaci restartovat (relaunch).

API bude dostupné na: `http://localhost:8080/api/product`

### 🐳 Možnost 2: Kompletní Docker prostředí

Toto spustí aplikaci i databázi v izolovaných kontejnerech.

1.  Otevřete terminál v kořenovém adresáři projektu.
2.  Spusťte:
    ```bash
    docker compose -f docker/compose.yaml up -d --build
    ```
3.  API bude dostupné na: `http://localhost:8080/api/product`

## 📂 Co je uvnitř?

- `src/main/java/com/example/buffet`
    - `product/web`: Obsahuje **Controller** (zpracovává příchozí HTTP požadavky).
    - `product/service`: Obsahuje **Service** (zpracovává obchodní logiku).
    - `product/repository`: Obsahuje **Repository** (komunikuje s databází).
    - `product/domain`: Obsahuje **Entity** (databázové modely) a **DTOs** (objekty pro přenos dat).
- `docker/`: Obsahuje všechny soubory související s Dockerem a inicializací databáze.
- `pom.xml`: Konfigurační soubor Maven, kde jsou definovány závislosti.

## 🔗 API Endpointy

Základní URL: `http://localhost:8080/api/product`

| Metoda | Endpoint | Popis |
| :--- | :--- | :--- |
| `GET` | `/` | Výpis všech produktů |
| `POST` | `/` | Přidání nového produktu |
| `PUT` | `/{id}` | Aktualizace produktu podle ID |
| `DELETE` | `/{id}` | Smazání produktu podle ID |

### Příklad těla požadavku (POST/PUT)
```json
{
  "name": "Pizza Slice",
  "cost": 30
}
```

### Příklad odpovědi při smazání
```json
{
  "message": "Product was deleted permanently from DB."
}
```

---
Ať se vám dobře kóduje! 🍕

---

# Buffet API Template

A simple and clean Java Spring Boot REST API template designed for new developers to learn and build upon. This project provides basic CRUD (Create, Read, Update, Delete) functionality for managing products in a buffet.

## 🚀 Technologies Used

- **Java 17**: Stable LTS release of the Java language.
- **Spring Boot 4**: Framework for building production-ready applications.
- **Spring Data JPA**: For easy database operations.
- **MySQL**: Reliable relational database.
- **Lombok**: To reduce boilerplate code (getters, setters, etc.).
- **Docker**: For easy deployment and environment consistency.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Java 17** (or compatible JDK)
- **Docker & Docker Compose**

## 🛠️ Getting Started

### 🟢 Option 1: Local Development (Recommended)

This is the preferred way for developers. You run the database in Docker and the application locally on your machine for faster development cycles.

1.  **Start the Database**:
    - **IDEA**: Use the **Docker DB** run configuration.
    - **Script**: Run `./start-db.sh` (Linux/macOS) or `start-db.bat` (Windows).
    - **Manual**: `docker compose -f docker/compose.yaml up -d mysql`
2.  **Run the Application**:
    - **IDEA**: Use the **BuffetApplication** run configuration.
    - **Script**: Run `./run-app.sh` (Linux/macOS) or `run-app.bat` (Windows).
    - **Manual**: `./mvnw spring-boot:run`

> [!IMPORTANT]
> This template does not support **live reload**. If you make changes to the code, you must restart the application (relaunch).

The API will be available at: `http://localhost:8080/api/product`

### 🐳 Option 2: Full Docker Environment

This starts both the application and the database in isolated containers.

1.  Open your terminal in the project root.
2.  Run:
    ```bash
    docker compose -f docker/compose.yaml up -d --build
    ```
3.  The API will be available at: `http://localhost:8080/api/product`

## 📂 What's Inside?

- `src/main/java/com/example/buffet`
    - `product/web`: Contains the **Controller** (handles incoming HTTP requests).
    - `product/service`: Contains the **Service** (handles business logic).
    - `product/repository`: Contains the **Repository** (talks to the database).
    - `product/domain`: Contains **Entities** (database models) and **DTOs** (data transfer objects).
- `docker/`: Contains all files related to Docker and database initialization.
- `pom.xml`: The Maven configuration file where dependencies are defined.

## 🔗 API Endpoints

Base URL: `http://localhost:8080/api/product`

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | List all products |
| `POST` | `/` | Add a new product |
| `PUT` | `/{id}` | Update a product by ID |
| `DELETE` | `/{id}` | Delete a product by ID |

### Example Request Body (POST/PUT)
```json
{
  "name": "Pizza Slice",
  "cost": 30
}
```

### Example Delete Response
```json
{
  "message": "Product was deleted permanently from DB."
}
```

---
Happy coding! 🍕
