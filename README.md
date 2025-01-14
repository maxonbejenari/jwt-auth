# Spring JWT Authentication Project

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup and Installation](#setup-and-installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Endpoints](#endpoints)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project is a Spring Boot application that demonstrates JWT (JSON Web Token) based authentication. It uses PostgreSQL for database management, Lombok to reduce boilerplate code, and Spring Security for securing the application.

## Features
- User registration and login
- JWT token generation and validation
- Role-based access control
- Secure APIs with Spring Security
- PostgreSQL database integration

## Technologies Used
- **Spring Boot**: Framework for building the application
- **JWT (JSON Web Token)**: For secure token-based authentication
- **PostgreSQL**: Relational database management system
- **Lombok**: For reducing boilerplate code in Java
- **Spring Security**: For securing the application’s APIs

## Setup and Installation
1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/your-repo-name.git
    cd your-repo-name
    ```

2. **Configure the database**:
    Make sure you have a PostgreSQL database running and update the `application.properties` or `application.yml` file with your database details.

3. **Build the project**:
    ```bash
    ./mvnw clean install
    ```

4. **Run the application**:
    ```bash
    ./mvnw spring-boot:run
    ```

## Configuration
Update your `application.properties` or `application.yml` file with the following properties:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/your-database-name
spring.datasource.username=your-username
spring.datasource.password=your-password
jwt.secret=your-secret-key

