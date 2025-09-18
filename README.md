# Hello World Spring Boot Application

This is a simple Spring Boot 3.2.0 application with a HelloWorld API that requires Spring Security authentication.

## Prerequisites

- Java 17 or higher
- Maven 3.6 or higher

## Project Structure

```
.
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/d5/
│   │   │       ├── D5Application.java
│   │   │       ├── config/
│   │   │       │   └── SecurityConfig.java
│   │   │       └── controller/
│   │   │           └── HelloController.java
│   │   └── resources/
│   │       └── application.yml
├── pom.xml
└── README.md
```

## Dependencies Added

- spring-boot-starter-web
- spring-boot-starter-security
- spring-boot-starter-test
- spring-security-test

## Configuration

The application uses the following configuration in `application.yml`:

```yaml
server:
  port: 8080
  servlet:
    context-path: /

spring:
  application:
    name: hello-world-app

logging:
  level:
    root: INFO
    com.d5: DEBUG
```

## How to Run

1. Clone the repository
2. Navigate to the project directory
3. Run the application using Maven:
   ```
   mvn spring-boot:run
   ```
4. The application will start on port 8080

## How to Test

### Using a Web Browser
1. Navigate to `http://localhost:8080/hello` in your browser
2. When prompted for credentials, use:
   - Username: `test`
   - Password: `123456`
3. You should see "Hello World" as the response

### Using cURL (Linux/Mac)
```bash
curl -u test:123456 http://localhost:8080/hello
```

### Using PowerShell (Windows)
```powershell
# Create credentials
$user = "test"
$pass = "123456"
$pair = "$($user):$($pass)"
$encodedCreds = [System.Convert]::ToBase64String([System.Text.Encoding]::ASCII.GetBytes($pair))
$basicAuthValue = "Basic $encodedCreds"

# Set headers
$headers = @{
    Authorization = $basicAuthValue
}

# Make the request
Invoke-WebRequest -Uri "http://localhost:8080/hello" -Headers $headers -UseBasicParsing
```

### Using Postman or similar REST client
1. Create a GET request to `http://localhost:8080/hello`
2. In the Authorization tab, select "Basic Auth"
3. Enter username `test` and password `123456`
4. Send the request

## Endpoints

- `GET /hello` - Returns "Hello World" (requires authentication)

## Credentials

- Username: `test`
- Password: `123456`

## Important Notes

1. This application uses Spring Security with basic authentication
2. The security configuration is defined in `src/main/java/com/d5/config/SecurityConfig.java`
3. The user credentials are configured in-memory for simplicity
4. The application uses Java 17 and Spring Boot 3.2.0
5. The maven-compiler-plugin is configured to use Java 17
6. The spring-boot-maven-plugin is configured with skip=false to allow packaging