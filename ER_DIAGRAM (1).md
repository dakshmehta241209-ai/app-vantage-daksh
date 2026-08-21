# Northstar EdTech - ER Diagram

This logical model covers the minimum data required for users, attendance, assignments, events, placements and notifications. Rename fields to match the actual database before submission.

```mermaid
erDiagram
    ROLE ||--o{ USER : assigns
    DEPARTMENT ||--o{ USER : contains
    DEPARTMENT ||--o{ COURSE : offers
    COURSE ||--o{ ENROLLMENT : has
    USER ||--o{ ENROLLMENT : joins
    COURSE ||--o{ ATTENDANCE_SESSION : schedules
    USER ||--o{ ATTENDANCE_SESSION : records
    ATTENDANCE_SESSION ||--o{ ATTENDANCE_RECORD : contains
    USER ||--o{ ATTENDANCE_RECORD : receives

    COURSE ||--o{ ASSIGNMENT : includes
    USER ||--o{ ASSIGNMENT : creates
    ASSIGNMENT ||--o{ ASSIGNMENT_SUBMISSION : receives
    USER ||--o{ ASSIGNMENT_SUBMISSION : submits

    USER ||--o{ EVENT : creates
    EVENT ||--o{ EVENT_REGISTRATION : receives
    USER ||--o{ EVENT_REGISTRATION : makes

    USER ||--o{ PLACEMENT : publishes
    PLACEMENT ||--o{ PLACEMENT_APPLICATION : receives
    USER ||--o{ PLACEMENT_APPLICATION : applies

    USER ||--o{ NOTIFICATION : receives
    USER ||--o{ ACTIVITY_LOG : performs

    ROLE {
        uuid id PK
        string name UK
        json permissions
        datetime created_at
    }

    DEPARTMENT {
        uuid id PK
        string name UK
        string code UK
        datetime created_at
    }

    USER {
        uuid id PK
        uuid role_id FK
        uuid department_id FK
        string name
        string email UK
        string password_hash
        string roll_or_employee_no UK
        string phone
        string profile_image_url
        boolean email_verified
        string status
        datetime created_at
        datetime updated_at
    }

    COURSE {
        uuid id PK
        uuid department_id FK
        string code UK
        string title
        string semester
        datetime created_at
    }

    ENROLLMENT {
        uuid id PK
        uuid course_id FK
        uuid student_id FK
        string academic_year
        string status
        datetime enrolled_at
    }

    ATTENDANCE_SESSION {
        uuid id PK
        uuid course_id FK
        uuid faculty_id FK
        date session_date
        string topic
        string status
        datetime created_at
    }

    ATTENDANCE_RECORD {
        uuid id PK
        uuid session_id FK
        uuid student_id FK
        string attendance_status
        string remarks
        datetime marked_at
    }

    ASSIGNMENT {
        uuid id PK
        uuid course_id FK
        uuid faculty_id FK
        string title
        text description
        datetime deadline
        decimal maximum_marks
        string attachment_url
        datetime created_at
    }

    ASSIGNMENT_SUBMISSION {
        uuid id PK
        uuid assignment_id FK
        uuid student_id FK
        string file_url
        string github_url
        datetime submitted_at
        boolean is_late
        decimal marks
        text feedback
        string status
    }

    EVENT {
        uuid id PK
        uuid created_by FK
        string title
        text description
        string venue
        datetime starts_at
        datetime registration_deadline
        integer capacity
        string banner_url
        string status
    }

    EVENT_REGISTRATION {
        uuid id PK
        uuid event_id FK
        uuid student_id FK
        string qr_token UK
        string status
        datetime registered_at
    }

    PLACEMENT {
        uuid id PK
        uuid created_by FK
        string company
        string job_role
        text eligibility
        decimal ctc
        datetime deadline
        string status
    }

    PLACEMENT_APPLICATION {
        uuid id PK
        uuid placement_id FK
        uuid student_id FK
        string resume_url
        string application_status
        datetime applied_at
    }

    NOTIFICATION {
        uuid id PK
        uuid user_id FK
        string type
        string title
        text message
        string target_url
        boolean is_read
        datetime created_at
    }

    ACTIVITY_LOG {
        uuid id PK
        uuid actor_id FK
        string action
        string entity_type
        uuid entity_id
        json metadata
        datetime created_at
    }
```

## Recommended constraints

- One role name and one user email must be unique.
- One student may have only one enrollment per course and academic year.
- One attendance record may exist per student and attendance session.
- One submission may exist per student and assignment unless resubmission is explicitly supported.
- One active event registration may exist per student and event.
- One placement application may exist per student and opportunity.
- Deleting academic records should normally be restricted; use status fields and audit logs instead.

