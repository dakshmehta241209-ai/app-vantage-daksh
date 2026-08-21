# Northstar EdTech

Northstar EdTech is a role-based Smart Campus Management Platform that brings students, faculty, coordinators and administrators into one centralized system. It is designed to reduce dependence on disconnected messaging groups, spreadsheets and separate campus portals.

> **Before submission:** Replace every value enclosed in `<...>`, remove any feature that is not working in the deployed build, and verify all demo credentials in an incognito window.

## Submission links

- Live application: [Northstar EdTech](https://northstaredu-hjnfsqav.manus.space/)
- GitHub repository: `<GITHUB_REPOSITORY_URL>`
- Demo video: `<DEMO_VIDEO_URL>`
- API documentation: `<SWAGGER_OR_POSTMAN_URL>`

## Problem addressed

Campus activities such as attendance, assignments, announcements, events and placement opportunities are frequently managed through disconnected tools. Northstar provides a single role-aware platform through which campus users can access the information and actions relevant to them.

## User roles

- **Student:** views attendance, assignments, events, placement notices and notifications; submits assignments and registers for events.
- **Faculty:** manages classes, records attendance, creates assignments, reviews submissions and publishes academic notices.
- **Coordinator:** manages events, clubs, registrations, approvals and campus announcements.
- **Admin:** manages users, roles, departments, permissions, reports and audit records.

## Core features

- Role-based dashboards for Student, Faculty, Coordinator and Admin
- Email-based authentication and protected routes
- Attendance recording and subject-wise attendance tracking
- Assignment creation, submission, grading and feedback
- Event creation, registration and capacity management
- Placement notices and student applications
- Announcements and role-specific notifications
- User, department and permission management
- Search, reports and administrative analytics
- Responsive user interface with loading, empty and error states

## Demonstration workflow

1. Sign in as Faculty and create an assignment.
2. Record attendance for a class.
3. Sign in as Student and verify that attendance has updated.
4. Submit the assignment and register for an event.
5. Sign in as Coordinator and inspect the event registration.
6. Sign in as Admin and review platform statistics and user controls.

## Demo credentials

| Role | Email | Password |
|---|---|---|
| Student | `<STUDENT_DEMO_EMAIL>` | `<STUDENT_DEMO_PASSWORD>` |
| Faculty | `<FACULTY_DEMO_EMAIL>` | `<FACULTY_DEMO_PASSWORD>` |
| Coordinator | `<COORDINATOR_DEMO_EMAIL>` | `<COORDINATOR_DEMO_PASSWORD>` |
| Admin | `<ADMIN_DEMO_EMAIL>` | `<ADMIN_DEMO_PASSWORD>` |

Use demonstration accounts only. Never publish production credentials or secret keys.

## Technology stack

| Layer | Technology |
|---|---|
| Frontend | React, TypeScript and Tailwind CSS |
| Backend | `<NODE_EXPRESS_OR_NEXT_API>` |
| Database | `<POSTGRESQL_OR_MONGODB>` |
| Authentication | Email/password, secure session or JWT, `<GOOGLE_OAUTH_IF_IMPLEMENTED>` |
| File storage | `<CLOUDINARY_AWS_S3_OR_OTHER>` |
| Deployment | Manus Space / `<BACKEND_DEPLOYMENT_SERVICE>` |

## System architecture

The client communicates only with authenticated API endpoints. The API validates requests, checks role permissions, applies business rules and then reads from or writes to the database. Files are stored outside the database and referenced using controlled URLs. Notifications and email services are triggered by successful domain events.

See [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md) for the complete diagram.

## Database design

The data model separates users and roles from operational entities such as attendance, assignments, events and placements. This allows authorization rules and campus records to evolve independently.

See [ER_DIAGRAM.md](ER_DIAGRAM.md) for the complete ER diagram.

## Security controls

- Password hashing using bcrypt or Argon2
- Server-side input validation
- Role-based authorization on protected API endpoints
- Secure cookies or short-lived access tokens with refresh-token rotation
- Rate limiting on authentication and sensitive endpoints
- File type and size validation
- Environment variables for secrets
- Audit logs for sensitive administrative actions
- Protection against XSS, CSRF and injection attacks where applicable

## Local setup

### Prerequisites

- Node.js 18 or later
- npm, pnpm or yarn
- `<DATABASE_NAME>` database instance

### Installation

```bash
git clone <GITHUB_REPOSITORY_URL>
cd <REPOSITORY_FOLDER>
npm install
cp .env.example .env
npm run dev
```

Open the local URL displayed by the development server.

## Environment variables

Create `.env` from `.env.example`. Typical variables are:

```env
DATABASE_URL=
SESSION_SECRET=
JWT_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
EMAIL_HOST=
EMAIL_PORT=
EMAIL_USER=
EMAIL_PASSWORD=
FILE_STORAGE_KEY=
FILE_STORAGE_SECRET=
APP_URL=
```

Do not commit the completed `.env` file.

## Useful commands

```bash
npm run dev
npm run build
npm run test
npm run lint
```

Delete commands that are not defined in the actual `package.json`.

## API overview

| Area | Example responsibility |
|---|---|
| `/api/auth` | Registration, login, verification, reset and logout |
| `/api/users` | Profiles, roles and user administration |
| `/api/attendance` | Sessions, attendance records and summaries |
| `/api/assignments` | Assignments, submissions, marks and feedback |
| `/api/events` | Events, registrations and capacity |
| `/api/placements` | Opportunities, eligibility and applications |
| `/api/notifications` | Role-specific notifications and read status |
| `/api/reports` | Administrative summaries and exports |

Update this table to match the actual API routes.

## Testing checklist

- All four demonstration accounts can sign in and sign out.
- Students cannot access faculty, coordinator or admin APIs.
- Attendance updates appear in the student dashboard.
- Assignment submission and faculty review work end to end.
- Event capacity and duplicate registrations are handled correctly.
- Invalid input produces a clear message.
- Protected pages redirect unauthenticated users.
- No secret keys appear in the repository or browser console.
- The deployed application works on desktop and mobile.

## Known limitations

- `<LIST_ONLY_REAL_LIMITATIONS>`
- Features not demonstrated in the submitted build should be described as future scope, not as completed work.

## Future scope

- QR-based attendance with replay protection
- Calendar and email integration
- Offline/PWA access
- Multilingual interface
- AI-powered campus FAQ assistant
- Plagiarism detection for assignment submissions
- CSV/Excel report export

## Licence

This project is released under the licence included in the repository. Add a `LICENSE` file before submission.

