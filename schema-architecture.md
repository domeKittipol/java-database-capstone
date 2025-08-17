This Spring Boot application uses both MVC and REST controllers. Thymeleaf templates are used for the Admin and Doctor dashboards, while REST APIs serve all other modules. The application interacts with two databases—MySQL (for patient, doctor, appointment, and admin data) and MongoDB (for prescriptions). All controllers route requests through a common service layer, which in turn delegates to the appropriate repositories. MySQL uses JPA entities while MongoDB uses document models.

1. User accesses AdminDashboard or Appointment pages.
2. The action is routed to the appropriate Thymeleaf or REST controller.
3. The controller calls the service layer
4. The service layer communicates with the Repository Layer to perform data access operations.
5.Each repository interfaces directly with the underlying database engine MySQL and MongoDB.
6. Once data is retrieved from the database, it is mapped into Java model classes that the application can work with.
7. In MVC flows, models are passed from the controller to Thymeleaf templates, where they are rendered as dynamic HTML for the browser.
In REST flows, the same models (or transformed DTOs) are serialized into JSON and sent back to the client as part of an HTTP response.