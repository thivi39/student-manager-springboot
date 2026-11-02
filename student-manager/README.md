# Student Registration System

A Spring Boot web application for registering and managing student records. It provides a server-rendered interface built with Thymeleaf and stores data in an H2 database.

## Features

- Register students with validation
- View all registered students
- Edit existing student details
- Delete students with confirmation
- Prevent duplicate email addresses
- Inspect stored records through the H2 Console

## Technologies

- Java 25
- Spring Boot
- Spring MVC
- Spring Data JPA
- Thymeleaf
- H2 Database
- HTML and CSS

## Run the application

From the project directory, run:

```powershell
.\mvnw.cmd spring-boot:run
```

Then open the application at:

```text
http://localhost:8080
```

## H2 Console

Open the H2 Console at:

```text
http://localhost:8080/h2-console
```

Use these connection settings:

| Field | Value |
| --- | --- |
| JDBC URL | `jdbc:h2:mem:studentdb` |
| User Name | `sa` |
| Password | Leave empty |

To view all students, run:

```sql
SELECT * FROM STUDENTS;
```

The database is stored in memory, so its records are removed when the application stops.

## Run the tests

```powershell
.\mvnw.cmd test
```
