Northstar EdTech
Northstar EdTech is a role-based Smart Campus Management Platform that brings students, faculty, coordinators and administrators into one centralized system. It is designed to reduce dependence on disconnected messaging groups, spreadsheets and separate campus portals.

## Submission links

- Live application: [Northstar EdTech](https://northstaredu-hjnfsqav.manus.space/)
- GitHub repository: (https://github.com/dakshmehta241209-ai/app-vantage-daksh.git)
- Demo video: `<DEMO_VIDEO_URL>`

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
The code explicitly contains these privileged-role passcodes:

| Role | Passcode |
|---|---|
| Faculty	| faculty@123 |
| Coordinator	| coordinator@123 |
| Admin	| admin@123 |

For a student account, the application supports normal sign-up using a username, email, and password.

## Technology stack

| Layer | Technology |
|---|---|
| Frontend | •	React •	TypeScript •	Vite •	Tailwind CSS •	Wouter •	React Hook Form •	TanStack React Query •	tRPC Client •	Radix UI •	Lucide React •	Framer Motion •	Recharts  |
| Backend | •	Node.js •	Express.js •	TypeScript •	tRPC |
| Database | •	MySQL •	Drizzle ORM  |

## System architecture

The client communicates only with authenticated API endpoints. The API validates requests, checks role permissions, applies business rules and then reads from or writes to the database. Files are stored outside the database and referenced using controlled URLs. Notifications and email services are triggered by successful domain events.

See ARCHITECTURE_DIAGRAM.md for the complete diagram.

Database design
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

### Installation

```bash
git clone (https://github.com/dakshmehta241209-ai/app-vantage-daksh.git)
cd (app-vantage-daksh)
npm install
cp .env.example .env
npm run dev
```

Open the local URL displayed by the development server.

## Useful commands

```bash
npm run dev
npm run build
npm run test
npm run lint
```

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

