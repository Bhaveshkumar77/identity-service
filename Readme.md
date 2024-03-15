Identity Service
The Identity Service is a Spring Boot application developed to handle customer identification and contact consolidation for FluxKart.com. It provides an endpoint /identify to consolidate customer contacts based on email or phone number.

Table of Contents
Setup
Database Setup
Environment Configuration
Running the Application
Testing
HTTP Requests and Responses
Contributing

Setup-
Database Setup
Install MySQL database server if not already installed.
Create a new database schema for the identity service.
Update the application.properties file with the database connection details:
spring.datasource.url=jdbc:mysql://localhost:3306/identity_service_db
spring.datasource.username=username
spring.datasource.password=password

Environment Configuration
Ensure that you have Java JDK and Maven installed on your system.

Running the Application
Clone the repository:
git clone https://github.com/your-username/identity-service.git

Navigate to the project directory:
cd identity-service

Build the project using Maven:
mvn clean install

Run the application:
mvn spring-boot:run

The application should now be running on https://localhost:8443.

Testing
HTTP Requests and Responses
1. Test with Existing Contact Information
Request:
Method: POST
URL: https://localhost:8443/identify
Body (JSON):
{
    "email": "existing@example.com",
    "phoneNumber": "1234567890"
}

Expected Response:
Status: 200 OK
Response Body (JSON):
{
    "id": 1,
    "email": "existing@example.com",
    "phoneNumber": "1234567890",
    "linkPrecedence": "primary",
    "secondaryContactIds": []
}

2. Test with New Contact Information
Request:
Method: POST
URL: https://localhost:8443/identify
Body (JSON):
{
    "email": "new@example.com",
    "phoneNumber": "9876543210"
}

Expected Response:
Status: 200 OK
Response Body (JSON):
{
    "id": 2,
    "email": "new@example.com",
    "phoneNumber": "9876543210",
    "linkPrecedence": "primary",
    "secondaryContactIds": []
}

Contributing
Contributions are welcome! Please feel free to submit pull requests or open issues if you encounter any problems.

