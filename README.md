# Three-Tier-Distributed-Web-Based-Application
This project is a full-stack, three-tier distributed web-based application designed to simulate an enterprise-level system using Java Servlets, JSP, and a MySQL backend, all deployed on an Apache Tomcat server. The application integrates a structured database consisting of suppliers, parts, jobs, and shipments, allowing users to interact with persistent data through a browser-based interface. It demonstrates the separation of concerns across the presentation layer, application layer, and data layer, where client-side JSP pages handle user interaction, servlets manage business logic and request processing, and the MySQL database ensures data integrity through relational constraints. A key component of the system is role-based access control, where different user types including root, client, data-entry, and accountant users are authenticated and granted specific permissions that dictate how they interact with the system. The application also highlights the use of JDBC for database connectivity, prepared statements for secure data insertion, and callable statements for executing stored procedures. Additionally, it incorporates server-side business logic that dynamically updates supplier status values based on shipment conditions, reinforcing concepts of transactional processing and backend validation. Overall, the project serves as a practical implementation of distributed system design, database-driven web development, and enterprise application architecture within a controlled academic environment.

# Architecture

This application follows a three-tier architecture consisting of the presentation layer, application layer, and data layer. The presentation layer is built using HTML and JSP and is responsible for displaying the user interface and collecting input through the browser. The application layer is implemented using Java Servlets running on Apache Tomcat, where all request handling, authentication, business logic, and database communication take place. The data layer consists of a MySQL database server that stores all persistent data and enforces relational integrity through primary and foreign key constraints. This separation allows the system to be modular, scalable, and easier to maintain.

# Features

The application includes a complete authentication system where users log in through a centralized page and are validated against a credentials database. Based on successful authentication, users are redirected to different interfaces depending on their role. The system supports executing SQL commands, inserting structured data through forms, and generating reports using stored procedures. It also includes error handling for invalid SQL commands and displays all results directly within the web interface.

# User Roles and Permissions

The root user has full access to the database and can execute all types of SQL commands including queries and updates. This user is also responsible for triggering the system’s business logic when certain conditions are met.

The client user has limited access and can only execute SELECT queries. This user cannot modify the database and does not trigger any business logic.

The data-entry user interacts with the system through structured forms instead of writing SQL commands directly. This user can insert records into the database tables using prepared statements, ensuring safe and controlled data entry.

The accountant user does not interact with raw SQL but instead selects predefined reports. These reports are generated through stored procedures using callable statements and return summarized data to the interface.

# Database Schema

The backend database named project4 consists of four main tables. The suppliers table stores supplier information including supplier number, name, status, and city. The parts table stores part details such as part number, name, color, weight, and city. The jobs table contains job-related data including job number, name, number of workers, and city. The shipments table connects suppliers, parts, and jobs together and includes a quantity field. This table uses a composite primary key and enforces referential integrity through foreign key relationships.

# Business Logic

The application includes server-side business logic implemented in the root-level servlet. Whenever a shipment is inserted or updated with a quantity greater than or equal to 100, the system automatically increases the status value of all relevant suppliers by 5. This logic is handled entirely in the application layer rather than the database, ensuring compliance with project requirements and demonstrating proper separation of concerns.

# Technologies Used

This project was developed using Java Servlets and JSP for backend and frontend integration. Apache Tomcat is used as the web server to deploy and run the application. MySQL is used as the database management system, and JDBC is used for database connectivity. HTML and CSS are used to design the user interfaces.

``` bash
Project-4/
│
├── index.html (authentication page)
├── errorpage.html
│
├── rootHome.jsp
├── clientHome.jsp
├── dataEntryHome.jsp
├── accountantHome.jsp
│
├── WEB-INF/
│   ├── web.xml
│   ├── classes/ (servlets)
│   ├── lib/ (JDBC driver)
│   └── conf/
│       ├── root.properties
│       ├── client.properties
│       ├── dataentry.properties
│       ├── accountant.properties
│       └── system.properties
```
# Setup Instructions

To run this project, first set up the database by executing the required SQL scripts in the correct order. Begin with the project4 database script, followed by the credentials database script, and then the script that creates user permissions. After that, configure the properties files for each user role as well as the system-level authentication user.

Next, place the project folder inside the Tomcat webapps directory. Start the Tomcat server and open a browser to access the application at http://localhost:8080/Project-4
. From there, users can log in and interact with the system based on their assigned role.

# Screenshots 
Screenshots are found \Project-4.zip\Project-4\Screenshots.pdf
