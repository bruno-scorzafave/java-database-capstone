# Schema Architecture

## Architecture summary
This Spring Boot application features a hybrid architecture that incorporates both MVC and REST controllers. While the Admin and Doctor dashboards are rendered using Thymeleaf templates, all other modules are driven by RESTful APIs. The system relies on a dual-database approach: MySQL manages relational data (patients, doctors, appointments, and admins) via JPA entities, whereas MongoDB handles prescriptions using document models. All controller requests are routed through a unified service layer, which seamlessly delegates operations to the corresponding repositories.

## Numbered flow of data and control

1. User accesses the Dashboards (Admin or Doctor) or REST Modules (Appointments, Patient pages).

2. The action is routed to the appropriate Thymeleaf or REST controller.

3. The controller calls the service layer to process the business logic.

4. The service layer uses the corresponding MySQL or MongoDB repositories depending on the required data.

5. The repositories access the respective physical databases (MySQL or MongoDB) to execute queries.

6. The database returns the data, which is then mapped into application-level MySQL or MongoDB models.

7. These models are defined and structured as JPA Entities (Patient, Doctor, Appointment, Admin) or Document models (Prescription).