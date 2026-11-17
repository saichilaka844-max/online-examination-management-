# Online Exam System

A web-based online examination management system built with Spring Boot, Thymeleaf, Spring Security and MySQL.

## Features
- Role-based access (Admin / Student) with registration and login
- Admin: manage subjects, question bank, exams and users; view results and attempt details
- Exam scheduling with availability modes and time limits
- Students: take timed exams, automatic evaluation, view results
- Server-side handling of expired attempts

## Tech Stack
Java 21 · Spring Boot 4.1.1 · Spring Security · Spring Data JPA · Thymeleaf · MySQL · Maven

## Getting Started

### Prerequisites
- JDK 21
- MySQL 8+ running locally (tables are auto-created via `ddl-auto=update`; create the `online_exam_db` database first)

### Configuration
Settings are read from environment variables (see `.env.example`):

| Variable | Purpose | Default |
|---|---|---|
| `DB_URL` | JDBC URL | `jdbc:mysql://localhost:3306/online_exam_db?...` |
| `DB_USERNAME` | DB user | `root` |
| `DB_PASSWORD` | DB password | *(empty)* |
| `APP_ADMIN_USERNAME` | Initial admin username | `admin` |
| `APP_ADMIN_PASSWORD` | Initial admin password (admin is only created when set) | *(none)* |
| `SPRING_PROFILES_ACTIVE` | Set to `dev` to seed demo data | *(none)* |

### Run
```bash
# Linux / macOS
export DB_PASSWORD=your_mysql_password
export APP_ADMIN_PASSWORD=choose_a_strong_password
./mvnw spring-boot:run

# Windows (PowerShell)
$env:DB_PASSWORD="your_mysql_password"
$env:APP_ADMIN_PASSWORD="choose_a_strong_password"
.\mvnw.cmd spring-boot:run
```
Open http://localhost:8080 and log in with the admin account.

### Tests
```bash
./mvnw test
```

## Project Structure
```
src/main/java/com/example/online_exam
├── config/       # Admin + dev data initializers
├── controller/   # MVC controllers
├── dto/          # Form / view models
├── entity/       # JPA entities
├── exception/    # Custom exceptions
├── repository/   # Spring Data repositories
├── security/     # Security config and handlers
└── service/      # Business logic
src/main/resources/{templates,static}
```
