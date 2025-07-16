# Application Architecture and Data Flow

## Section 1: Architecture Summary

This Spring Boot application follows a hybrid architecture using both MVC and REST paradigms. Thymeleaf templates render views for the Admin and Doctor dashboards, providing a server-side rendered experience for these roles. For other modules such as patients and appointments, REST APIs expose the necessary endpoints to handle client requests.

The application interacts with two databases: a MySQL database for storing structured relational data such as patient records, doctor information, appointments, and admin details; and a MongoDB database for storing prescription documents, leveraging the flexibility of a NoSQL schema for unstructured medical data. 

All incoming requests are handled by controllers which delegate processing to a common service layer. This service layer encapsulates business logic and communicates with repository classes to perform database operations. JPA entities are used for the relational MySQL database, while MongoDB interactions use document models.

---

## Section 2: Numbered Flow of Data and Control

1. A user (Admin, Doctor, or Patient) initiates a request via a dashboard (Thymeleaf) or a REST API call.
2. The request is routed to the appropriate controller (MVC or REST).
3. The controller validates input data and forwards the request to the service layer.
4. The service layer processes business logic, including any necessary validations or computations.
5. The service layer calls the corresponding repository interfaces to interact with MySQL or MongoDB.
6. The repository executes database operations using JPA for MySQL or document queries for MongoDB.
7. The service layer returns the response to the controller, which then renders a view (Thymeleaf) or returns a JSON response (REST API) to the client.
