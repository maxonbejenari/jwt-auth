WT Authentication with Spring Security
This project demonstrates how to implement an authentication system using JWT (JSON Web Tokens) with Spring Security, Spring Boot, and PostgreSQL. It provides a secure way to authenticate and authorize users for a web application while using JWT for stateless sessions.

Technologies Used
Spring Boot: The backend framework to build and run the application.
Spring Security: To secure the application and manage authentication and authorization.
JWT (JSON Web Tokens): Used for stateless authentication.
PostgreSQL: A relational database for storing user information and roles.
Lombok: To simplify code by automatically generating getters, setters, builders, etc.
Spring WebSocket & STOMP: For real-time messaging between clients and the server (optional feature).
SockJS: Provides WebSocket fallback support to ensure cross-browser compatibility.
Features
Authentication System
JWT Authentication: The backend uses JWT to authenticate users. Upon successful login, the user receives a token that must be included in the Authorization header for every subsequent request.
Spring Security Integration: Security is managed through Spring Security, with specific filters that validate JWT tokens and manage user access control.
Role-based Authorization: Users have roles (e.g., USER, ADMIN) stored in PostgreSQL, which can be used to control access to certain endpoints.
Real-Time Messaging (Optional)
WebSocket Communication: Real-time messaging is implemented using WebSockets with STOMP. Users can subscribe to topics and receive real-time notifications when other users send messages or join/leave the chat.
Session Management: The application tracks WebSocket sessions to manage user connections and handle disconnects.
Project Setup
Prerequisites
JDK 11 or higher
PostgreSQL database
Maven or Gradle (for managing dependencies)
Any IDE (e.g., IntelliJ IDEA, Eclipse)
Clone the Repository
bash
git clone https://github.com/your-username/jwt-auth-spring.git
cd jwt-auth-spring
Database Configuration
Install and run PostgreSQL.
Create a new database (e.g., jwt_auth).
Configure the PostgreSQL connection in application.properties (or application.yml).
properties
spring.datasource.url=jdbc:postgresql://localhost:5432/jwt_auth
spring.datasource.username=your-username
spring.datasource.password=your-password
spring.jpa.hibernate.ddl-auto=update
spring.datasource.driverClassName=org.postgresql.Driver
Dependencies
Make sure to add these dependencies to your pom.xml (for Maven) or build.gradle (for Gradle):

Maven
xml
<dependencies>
    <!-- Spring Boot & Security -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- PostgreSQL Database -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
    </dependency>

    <!-- JWT -->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt</artifactId>
        <version>0.11.5</version>
    </dependency>

    <!-- Lombok -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <scope>provided</scope>
    </dependency>

    <!-- Spring WebSocket (optional) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-websocket</artifactId>
    </dependency>
</dependencies>
Gradle
gradle
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-security'
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'org.postgresql:postgresql'
    implementation 'io.jsonwebtoken:jjwt:0.11.5'
    implementation 'org.projectlombok:lombok'
    implementation 'org.springframework.boot:spring-boot-starter-websocket' // optional
}
Running the Application
Build the application:

For Maven:

bash
mvn clean install
For Gradle:

bash
Копировать код
gradle build
Run the application:

bash
Копировать код
mvn spring-boot:run
Or, if using Gradle:

bash
gradle bootRun
Using the API
Register a User
Send a POST request to register a new user:

http
POST http://localhost:8080/api/auth/register
Content-Type: application/json

{
    "username": "john_doe",
    "password": "securepassword"
}
Login
Send a POST request to log in and get the JWT token:

http
POST http://localhost:8080/api/auth/login
Content-Type: application/json

{
    "username": "john_doe",
    "password": "securepassword"
}
The response will contain the JWT token:

json
{
    "token": "your-jwt-token"
}
Access a Secure Endpoint
Use the JWT token to access a secure endpoint:

http
GET http://localhost:8080/api/secure
Authorization: Bearer your-jwt-token
