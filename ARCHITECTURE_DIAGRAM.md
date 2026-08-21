# Northstar EdTech - Architecture Diagram

This deployment-neutral architecture matches the Smart Campus Management Platform requirements. Replace provider names with the services used in the actual repository.

```mermaid
flowchart TB
    U["Campus users<br/>Student · Faculty · Coordinator · Admin"]
    FE["Responsive web client<br/>React · TypeScript · Tailwind CSS"]
    API["Application API<br/>Node.js · Validation · Business rules"]
    AUTH["Authentication and RBAC<br/>Email · OAuth · Sessions/JWT"]
    DATA[("Campus database<br/>PostgreSQL or MongoDB")]
    FILES["File storage<br/>Assignments · Resumes · Event banners"]
    MSG["Notification services<br/>In-app · Email · Real-time"]
    OPS["Operations<br/>Logs · Monitoring · CI/CD"]

    U -->|HTTPS| FE
    FE -->|Validated API requests| API
    API --> AUTH
    AUTH --> DATA
    API --> DATA
    API --> FILES
    API --> MSG
    API --> OPS
```

## Request flow

```mermaid
sequenceDiagram
    actor User
    participant Client as Web client
    participant API as Campus API
    participant Auth as Auth/RBAC
    participant DB as Database
    participant Notify as Notification service

    User->>Client: Performs a campus action
    Client->>API: Sends authenticated request
    API->>Auth: Validates session and permission
    Auth-->>API: Returns user identity and role
    API->>DB: Validates and stores domain change
    DB-->>API: Confirms transaction
    API->>Notify: Publishes relevant notification
    API-->>Client: Returns success or safe error
    Client-->>User: Updates dashboard state
```

## Main application modules

| Module | Primary responsibility |
|---|---|
| Authentication | Registration, login, verification, recovery and logout |
| Authorization | Server-side role and permission enforcement |
| Users | Profiles, departments, roles and account status |
| Attendance | Sessions, records, summaries and reports |
| Assignments | Creation, submission, grading and feedback |
| Events | Creation, capacity, registration and QR passes |
| Placements | Opportunities, eligibility, applications and status |
| Notifications | In-app, email and real-time delivery |
| Analytics | Attendance, assignment, event and placement summaries |
| Audit | Sensitive administrative and academic changes |

## Deployment notes

- Serve every public and authenticated route through HTTPS.
- Keep database, session, OAuth and storage secrets in environment variables.
- Store uploaded files in object storage rather than directly in the application container.
- Apply authorization inside API handlers; hiding a menu item is not a security control.
- Add indexes for email, course, student, session, assignment, event and notification queries.
- Use structured logs and health checks to diagnose deployment failures.
- Back up the database and restrict administrative access.

