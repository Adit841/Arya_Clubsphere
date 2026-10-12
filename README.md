# Arya College ClubSphere
**Live Demo:** [Arya College ClubSphere](https://event-management-uylc.onrender.com/)

**One platform for clubs, events, and campus activities.**

Arya College ClubSphere is a web-based Club and Event Management System developed for Arya College of Engineering & IT, Jaipur. The project aims to simplify and centralize the management of college clubs, student memberships, events, registrations, and club-related activities.

The system provides different functionalities for administrators, club heads, club members, and students. It helps reduce manual work, improve communication, and make college club activities easier to manage.

The project is developed using Java, JSP, Servlets, JDBC, MySQL, and Apache Tomcat.

---

## Table of Contents

- [Features](#features)
- [User Roles](#user-roles)
- [Team Module Allocation](#team-module-allocation)
- [Tech Stack](#tech-stack)
- [How It Works](#how-it-works)
- [Project Structure](#project-structure)
- [Getting Started (Local Setup)](#getting-started-local-setup)
- [Configuration](#configuration)
- [Database Setup](#database-setup)
- [Running the Project](#running-the-project)
- [GitHub Workflow](#github-workflow)
- [Security](#security)
- [Future Enhancements](#future-enhancements)
- [Team](#team)
- [Contributing](#contributing)

---

## Features

| Module | Description |
|---|---|
| Authentication & User Management | Provides user registration, login, authentication, and role-based access to the system. |
| Club Management | Allows authorized users to manage college clubs and maintain club-related information and memberships. |
| Event Management | Supports the management of college events, event information, and student registrations. |
| QR Code Registration | Supports QR-based event registration and helps organizers verify registrations during event check-in. |
| Role-Based Dashboards | Provides dashboard functionality according to the user's role and permitted activities. |
| Tasks & Notifications | Supports task-related activities and notifications to help users stay informed about club work and events. |
| Database Management | Stores and manages information related to users, clubs, events, registrations, and other application data. |

---

## User Roles

Arya College ClubSphere is designed to support different categories of users.

| Role | Responsibilities |
|---|---|
| Admin | Manages the overall system and performs authorized administrative activities. |
| Club Head | Manages assigned club activities, coordinates events, and handles relevant event registrations. |
| Club Member | Participates in club activities and accesses permitted club-related features. |
| Student | Explores available clubs and events and participates in eligible college activities. |

Access to application features depends on the user's assigned role and permissions.

---

## Team Module Allocation

The project is divided into four major modules to support collaborative development.

| Module | Module Name | Assigned Member |
|---|---|---|
| Module 1 | Authentication & User Management | Avantika Mishra |
| Module 2 | Club Management | Avanshi Kothari |
| Module 3 | Event Management & QR Code Registration | Akansha Sharma |
| Module 4 | Dashboards, Tasks & Notifications | Aditi Maheshwari |

Each member is responsible for developing and maintaining the assigned module while coordinating with the other team members to integrate the complete application.

---

## Tech Stack

| Layer | Technologies |
|---|---|
| Frontend | HTML, CSS, JavaScript, JSP |
| Backend | Java, Java Servlets |
| Database | MySQL 8 |
| Database Connectivity | JDBC |
| Build Tool | Apache Maven |
| Application Server | Apache Tomcat 10.1 |
| Development Environment | Visual Studio Code |
| Version Control | Git and GitHub |
| Java Development Kit | JDK 17 |

### Technology Overview

- **HTML:** Defines the structure of the web pages.
- **CSS:** Provides styling and layout for the application.
- **JavaScript:** Supports client-side interactions and dynamic functionality.
- **JSP:** Generates dynamic web pages.
- **Java Servlets:** Handle incoming requests and application logic.
- **JDBC:** Connects the Java application with the MySQL database.
- **MySQL:** Stores application data.
- **Apache Maven:** Manages dependencies and builds the project.
- **Apache Tomcat:** Runs the web application.
- **Git and GitHub:** Support version control and collaboration among team members.

---

## How It Works

Arya College ClubSphere follows a web-based application architecture.

```text
                User
                 |
                 v
        Web Browser Interface
           HTML / CSS / JSP
                 |
                 v
           Java Servlets
                 |
                 v
        Application Processing
                 |
                 v
              JDBC
                 |
                 v
             MySQL DB
                 |
                 v
        Application Response
                 |
                 v
        Updated Web Interface
```

### Application Workflow

1. The user opens the ClubSphere web application.
2. The user registers or logs in using the available authentication functionality.
3. The system identifies the user's role and provides access to permitted features.
4. Users interact with the available club, event, dashboard, and other relevant modules.
5. Java Servlets process application requests.
6. JDBC communicates with the MySQL database when data needs to be retrieved or updated.
7. The application returns the appropriate response to the user.

### QR Code Event Workflow

The QR Code Registration feature supports the event registration process.

1. An authorized organizer manages an event through the Event Management module.
2. The event registration process makes a QR code available where implemented.
3. Students use the available registration process to participate in the event.
4. The organizer can use the QR-based check-in functionality to help verify event registrations.

The exact QR code generation and verification flow depends on the implemented event registration functionality.

---

## Project Structure

The project uses a Maven-based Java web application structure.

```text
Event_Management/
│
├── pom.xml
│
├── src/
│   └── main/
│       ├── java/
│       │   └── ...
│       │
│       ├── resources/
│       │   └── application.properties
│       │
│       └── webapp/
│           ├── WEB-INF/
│           │   └── web.xml
│           │
│           ├── *.jsp
│           ├── css/
│           ├── js/
│           └── images/
│
├── database/
│   └── SQL scripts, if maintained separately
│
├── docs/
│   └── Project documentation and reports
│
├── .gitignore
├── pom.xml
└── README.md
```

**Note:** The tree above illustrates the general structure of a Maven-based Java web application. The exact folders and files should correspond to the current project repository. Optional folders such as `database/` and `docs/` should be included only if they exist in the project.

### Main Components

| Component | Purpose |
|---|---|
| `pom.xml` | Defines Maven dependencies and build configuration. |
| `src/main/java/` | Contains Java source code, including application logic and Servlets. |
| `src/main/resources/` | Contains application resources and configuration files. |
| `application.properties` | Contains application configuration, where used. |
| `src/main/webapp/` | Contains web resources and JSP pages. |
| `WEB-INF/web.xml` | Contains web application configuration, where used. |
| `README.md` | Provides project information and setup instructions. |
| `.gitignore` | Specifies files and folders that Git should ignore. |

---

## Getting Started (Local Setup)

Follow the instructions below to set up the project on your local computer.

### Prerequisites

Install the following software:

- **JDK 17**
- **Apache Maven 3.9 or later**
- **Apache Tomcat 10.1**
- **MySQL Server 8.0 or later**
- **Visual Studio Code** or another compatible Java IDE
- **Git**

Ensure that Java, Maven, and Git are correctly configured on your system.

Verify the installations using:

```bash
java -version
```

```bash
mvn -version
```

```bash
git --version
```

---

### 1. Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/Avantikamishra862/Event_Management.git
```

Navigate to the project directory:

```bash
cd Event_Management
```

Open the project in Visual Studio Code:

```bash
code .
```

---

### 2. Configure MySQL

Start MySQL Server and open MySQL Workbench or another MySQL client.

Create the project database using the database name configured in the application.

For example:

```sql
CREATE DATABASE clubsphere_db;
```

If the project includes a database schema or SQL initialization script, execute that script to create the required tables.

**Important:** The database name, table names, and schema must match the application's actual SQL queries and configuration.

---

### 3. Configure Database Credentials

Locate the database configuration used by the application.

Depending on the current implementation, this may be in:

```text
src/main/resources/application.properties
```

or in the relevant Java database connection utility.

Configure the database URL, username, and password according to your local MySQL installation.

Example configuration:

```properties
db.url=jdbc:mysql://localhost:3306/clubsphere_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
db.username=root
db.password=YOUR_MYSQL_PASSWORD
```

The property names above are illustrative. Use the exact property names expected by the existing application.

Replace `YOUR_MYSQL_PASSWORD` with your own MySQL password.

**Never commit real database passwords or other private credentials to GitHub.**

---

### 4. Build the Project

Open the terminal in the project root directory, where `pom.xml` is located.

Run:

```bash
mvn clean package
```

Maven will resolve dependencies, compile the application, and generate the WAR file if the project is configured for WAR packaging.

The generated artifact is generally located inside:

```text
target/
```

The exact WAR filename depends on the project's Maven configuration.

---

## Configuration

Before running the project, verify the following settings.

| Configuration | Description |
|---|---|
| Java Version | JDK 17 |
| Database Server | MySQL Server |
| Database Name | Must match the application configuration |
| Database Username | Your local MySQL username |
| Database Password | Your local MySQL password |
| Database URL | Must point to the correct MySQL server and database |
| Tomcat Version | Apache Tomcat 10.1 |
| Maven Configuration | Defined in `pom.xml` |

### Important Configuration Notes

- MySQL Server must be running before the application attempts to connect to it.
- The database must contain the tables required by the application.
- Database credentials must match your local MySQL configuration.
- Tomcat must be configured correctly to run the generated WAR file.
- Java, Maven, and Tomcat versions should remain compatible with the application's dependencies and Servlet API.
- Do not upload private credentials, passwords, or secret configuration values to GitHub.

---

## Database Setup

MySQL is used to store the application's persistent data.

Depending on the implemented modules, the database may contain information related to:

- User accounts and roles
- College clubs
- Club memberships
- Events
- Event registrations
- QR-based registration and check-in records
- Tasks and notifications

The actual tables and relationships are defined by the project's database schema and application implementation.

### Database Setup Steps

1. Start MySQL Server.
2. Create the configured database.
3. Execute the project's SQL schema or initialization script, if provided.
4. Configure the database connection settings.
5. Build and start the application.
6. Verify that the application can connect to the database.

---

## Running the Project

The project can be built using Maven and deployed to Apache Tomcat.

### Step 1: Build the Application

From the project root directory, run:

```bash
mvn clean package
```

Confirm that the build completes successfully.

### Step 2: Deploy to Tomcat

Locate the generated WAR file inside the `target/` directory.

Deploy the WAR file to the deployment directory of your Tomcat installation, or use your configured deployment method.

### Step 3: Start Tomcat

Start the Apache Tomcat server using the method configured on your system.

Check the Tomcat logs if the application does not start successfully.

### Step 4: Open the Application

Open a browser and navigate to the context path corresponding to the deployed application.

For example:

```text
http://localhost:8080/aryaClgClubSphere
```

The actual URL depends on the deployed WAR filename and Tomcat configuration.

If the application uses a different context path, open that path instead.

---

## GitHub Workflow

GitHub is used for source code management and collaboration among the four team members.

Repository:

**[Arya College ClubSphere – Event Management Repository](https://github.com/Avantikamishra862/Event_Management)**

### Branches

The project repository uses the following branches for development and collaboration:

| Branch | Purpose |
|---|---|
| `main` | Main project branch |
| `backend` | Backend-related development |
| `frontend` | Frontend-related development |
| `database` | Database-related development |
| `testing` | Testing-related work |

The team should coordinate changes before merging shared files or integrating module updates.

### Clone the Repository

```bash
git clone https://github.com/Avantikamishra862/Event_Management.git
```

### Check the Current Branch

```bash
git branch
```

### Switch to a Branch

For example:

```bash
git switch backend
```

Replace `backend` with the branch you need.

### Pull the Latest Changes

```bash
git pull
```

### Stage Changes

```bash
git add .
```

### Commit Changes

```bash
git commit -m "Describe your changes"
```

### Push Changes

```bash
git push
```

### Collaboration Guidelines

1. Work on the branch agreed upon by the team.
2. Pull the latest changes before beginning new work.
3. Avoid editing the same files simultaneously without coordination.
4. Use clear and meaningful commit messages.
5. Test changes before pushing them.
6. Coordinate integration of the four modules.
7. Never commit database passwords or other secrets.
8. Review changes before merging them into the main project branch.

---

## Security

Security is important for a system that manages users, clubs, events, and registrations.

The following practices should be followed during development:

- Validate user input before processing it.
- Restrict access to administrative and club management operations according to user roles.
- Use secure password-handling practices.
- Use parameterized SQL queries or `PreparedStatement` to reduce SQL injection risks.
- Avoid exposing database credentials in source code or public repositories.
- Validate event registration requests on the server side.
- Verify registration records before confirming event check-in.
- Handle errors without exposing sensitive internal information.

The actual security protections depend on the application's implemented authentication and authorization logic.

---

## Future Enhancements

The following features may be considered for future development:

- Improved role-based dashboards
- Enhanced club membership management
- Advanced event scheduling and management
- QR-based event check-in improvements
- Real-time notifications
- Email notifications for important events
- Event attendance reports
- Club activity reports
- Improved mobile responsiveness
- Additional validation and automated tests
- Deployment to a hosted environment

These are potential enhancements and should not be considered implemented features unless they are present in the current codebase.

---

## Team

Arya College ClubSphere is being developed collaboratively by the following team members.

| S. No. | Team Member | Enrollment Number | Responsibility |
|---|---|---|---|
| 1 | Avantika Mishra | 24EARCS032 | Authentication & User Management |
| 2 | Avanshi Kothari | 24EARCS031 | Club Management |
| 3 | Akansha Sharma | 24EARCS012 | Event Management & QR Code Registration |
| 4 | Aditi Maheshwari | 24EARCS007 | Dashboards, Tasks & Notifications |

### Team Collaboration

Each team member works on an assigned module. The modules are integrated to create a unified college club and event management application.

The team uses GitHub for version control, code sharing, and collaborative development.

---

## Contributing

Contributions from team members should follow the project's agreed development workflow.

1. Check the current branch before making changes.
2. Pull the latest code before starting development.
3. Work on the appropriate branch or assigned module.
4. Keep changes focused and easy to review.
5. Test the affected functionality before committing.
6. Use meaningful commit messages.
7. Coordinate changes to shared files with other team members.
8. Review and resolve merge conflicts carefully.
9. Never commit passwords, private credentials, or other sensitive configuration values.
10. Verify that the integrated application continues to build and run correctly.

---

## Project Status

Arya College ClubSphere is a college project focused on simplifying the management of clubs, events, memberships, and related campus activities.

The application is being developed module by module, with each team member contributing to an assigned area of functionality.

The final functionality and deployment status depend on the implementation and integration of the project's modules.

---

**Developed by the Arya College ClubSphere Team**  
**Arya College of Engineering & IT, Jaipur**