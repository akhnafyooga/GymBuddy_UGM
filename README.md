# UGM Gym Partner & Facility Tracker - GAMASPOT

> An AI-powered workout partner matching and gym capacity monitoring platform built exclusively for Universitas Gadjah Mada (UGM) students.

UGM Gym Partner is a campus-focused fitness platform designed to help UGM students find compatible workout partners, coordinate workout schedules, communicate safely, and monitor gym facility capacity.

The platform combines UGM student verification, workout partner matching, schedule synchronization, social safety features, in-app communication, facility reservations, and real-time capacity monitoring into a single campus fitness ecosystem.

Created By:
* Akhnaf Fawzan Yogatrisna - 24/536720/TK/59561 - Full-stack Developer
* Musa Hanif Moeljawan - 24/533080/TK/59061 - Full-stack Developer

---

## Features

### 1. Authentication & User Verification

* UGM email verification using `@mail.ugm.ac.id`
* Campus-only user access
* Role-Based Access Control (RBAC)
* Student, Facility Manager, and IT Admin roles
* Verified UGM student profile
* Workout style and pacing preferences

### 2. Workout Partner Matching

Students can find compatible workout partners based on:

* Workout schedule
* Fitness discipline
* Workout goals
* Workout pacing
* Preferred facility

Supported workout styles include:

* Powerlifting
* Bodybuilding
* HIIT
* Cardio
* Heavy Strength
* PPL

### 3. Schedule Synchronization

Students can enter their available workout hours through a visual schedule grid.

The matching system identifies students with overlapping availability, allowing students to find partners who can train at the same time.

### 4. Social Safety & Moderation

Because workout partners meet physically on campus, the platform provides safety and accountability features.

#### User Rating & Reliability Score

Students can provide feedback after a workout session.

The system tracks reliability indicators such as:

* Attended
* No-show
* Cancelled
* Reliability score

This helps students make more informed decisions when choosing workout partners.

#### Reporting & Blocking

Students can:

* Report inappropriate behavior
* Report harassment
* Report improper gym etiquette
* Block other users
* Submit reports directly to IT Admins / Moderators

IT Admins can review reports and take appropriate moderation actions.

### 5. In-App Communication

Students do not need to immediately exchange personal contact information after finding a match.

#### Direct Chat

Once a workout invitation or match is accepted, students can communicate through an in-app direct messaging system.

The chat can be used to coordinate:

* Workout time
* Meeting location
* Workout plans
* Schedule changes

#### Notifications

The system provides real-time or in-app notifications for important events, including:

* Workout invitation received
* Workout invitation accepted
* Workout invitation declined
* New chat message
* Session request
* Reservation updates
* Moderation updates

### 6. Facility Check-In

Students can select their workout location from supported UGM facilities:

* GMC
* Lembah
* UGM Residence
* GIK Gym

The selected facility is associated with the student's active workout session.

### 7. Live Gym Occupancy

Facility Managers can monitor gym occupancy across supported facilities.

The system provides capacity indicators:

* Low
* Moderate
* Peak / High Capacity

Live occupancy data helps facility managers identify overcrowding and monitor facility usage.

### 8. Slot Reservation & QR Check-In

Students can reserve available gym slots and receive a unique QR check-in pass.

Facility Managers can scan the QR code to verify:

* Student identity
* UGM email
* Reservation status
* Check-in status

### 9. Automated No-Show & Overstay Release

The reservation system handles unused or expired reservations automatically.

If a student reserves a slot but does not complete QR check-in within **15 minutes**, the reservation is automatically released back into the available capacity pool.

The system can also track session duration and release reservations when the allowed usage period has ended.

This prevents reserved capacity from being unnecessarily locked by inactive users.

### 10. Peak Hour Reservation Rules

To maintain fair access during busy periods, the system can enforce peak-hour reservation limits.

During peak traffic:

* Students can have a maximum of 1 active reservation per day.
* Additional reservations are restricted while the student already has an active peak-hour reservation.
* Released no-show reservations return to the available capacity pool.

This helps distribute facility access fairly across students and faculties.

---

## Core Modules

The system is organized into four main modules.

| Module                             | Description                                                                       |
| ---------------------------------- | --------------------------------------------------------------------------------- |
| Authentication & User Verification | UGM email verification, RBAC, profiles, and workout preferences                   |
| Partner Matching & Scheduling      | Schedule synchronization, workout matching, filtering, and workout invitations    |
| Social & Communication             | Reliability scores, reporting, blocking, direct chat, and notifications           |
| Facility Management                | Check-in, occupancy monitoring, reservations, QR verification, and capacity rules |

---

## User Roles

| Role                 | Responsibilities                                                                                          |
| -------------------- | --------------------------------------------------------------------------------------------------------- |
| Student              | Manage profile, find workout partners, coordinate sessions, chat, reserve gym slots, and provide feedback |
| Facility Manager     | Monitor facility occupancy, manage capacity, verify QR check-ins, and handle facility reservations        |
| IT Admin / Moderator | Manage users, roles, reports, blocks, moderation actions, and system access                               |

---

## System Architecture

```text
UGM Gym Partner
│
├── Authentication
│   ├── UGM Email Verification
│   ├── RBAC
│   └── User Profiles
│
├── Partner Matching
│   ├── Schedule Synchronization
│   ├── Workout Preferences
│   ├── Matching Algorithm
│   └── Workout Invitations
│
├── Social & Communication
│   ├── Reliability Score
│   ├── Reporting
│   ├── Blocking
│   ├── Direct Chat
│   └── Notifications
│
└── Facility Management
    ├── Facility Check-In
    ├── Live Occupancy
    ├── Slot Reservation
    ├── QR Verification
    ├── No-Show Release
    ├── Overstay Release
    └── Peak Hour Rules
```

---

## Tech Stack

* **Framework:** Next.js
* **Language:** TypeScript
* **Styling:** Tailwind CSS
* **UI:** Shadcn/UI
* **Backend:** Next.js API Routes / Node.js
* **Database:** PostgreSQL
* **Authentication:** NextAuth
* **Containerization:** Docker
* **Version Control:** Git & GitHub

---

## Getting Started

### Requirements

Make sure the following are installed:

* Node.js v18+
* Docker Desktop
* Git

### Installation

Clone the repository and install the dependencies:

```bash
git clone https://github.com/your-username/ugm-gym-partner.git
cd ugm-gym-partner
npm install
```

### Environment Variables

Create a `.env` file in the project root:

```env
DATABASE_URL="postgresql://user:password@localhost:5432/ugmgym"
NEXTAUTH_SECRET="your-secret-key"
ALLOWED_DOMAIN="mail.ugm.ac.id"
```

Do not commit your `.env` file to GitHub.

### Database

Start the local PostgreSQL environment using Docker:

```bash
docker compose up -d
```

Configure the database according to the project's database and migration setup.

### Run the Application

Start the development server:

```bash
npm run dev
```

The application will be available at:

```text
http://localhost:3000
```

---

## Project Structure

```text
ugm-gym-partner/
│
├── .github/
│   └── # Issue templates & GitHub workflows
│
├── public/
│   └── # Static assets & UI icons
│
├── src/
│   ├── components/
│   │   └── # Reusable UI components
│   │
│   ├── modules/
│   │   ├── auth/
│   │   │   └── # UGM authentication & RBAC
│   │   │
│   │   ├── matching/
│   │   │   └── # Schedule sync & partner matching
│   │   │
│   │   ├── social/
│   │   │   └── # Ratings, reporting & blocking
│   │   │
│   │   ├── communication/
│   │   │   └── # Direct chat & notifications
│   │   │
│   │   └── facility/
│   │       └── # Occupancy, reservations & QR check-in
│   │
│   ├── pages/
│   │   └── # Application routes
│   │
│   └── styles/
│       └── # Global styles & Tailwind configuration
│
├── .env
├── README.md
├── package.json
└── ...
```

---

## Development Workflow

The project follows the Scrum framework with one-week development sprints.

```text
Sprint Planning
      ↓
Sprint Backlog
      ↓
Development
      ↓
Testing & Pull Request
      ↓
Sprint Review
      ↓
Retrospective
      ↓
Next Sprint
```

### GitHub Project Workflow

```text
Product Backlog
      ↓
Sprint Backlog
      ↓
In Progress
      ↓
In Review / PR
      ↓
Done
```

The team maintains a maximum of 2 active tasks per developer to minimize context switching.

---

## Development Responsibilities

Both team members work as **Full-Stack Developers**, contributing across frontend, backend, database, API, and system integration.

### Musa Hanif Moeljawan — Full-Stack Developer

Primary focus:

* Authentication and UGM email verification
* User profiles and RBAC
* Workout preference management
* Schedule synchronization
* Workout partner matching
* Matching filters
* Student-facing UI
* Database models for users and matching
* Matching APIs
* Frontend and backend integration
* Unit and integration testing

Secondary responsibilities:

* Product backlog management
* User story definition
* Acceptance criteria
* Product validation
* Code review

### Akhnaf Fawzan Yogatrisna — Full-Stack Developer

Primary focus:

* Facility management
* Gym slot reservations
* QR check-in system
* Live occupancy tracking
* No-show and overstay handling
* Peak-hour reservation rules
* Social safety and moderation
* Reliability scoring
* Reporting and blocking
* Direct chat
* Notification system
* Facility and moderation APIs
* Database models for reservations, reports, chat, and occupancy
* Frontend and backend integration
* Unit and integration testing

Secondary responsibilities:

* Scrum facilitation
* GitHub Project management
* Technical architecture
* Technical blocker resolution
* Code review

### Shared Responsibilities

Both developers are responsible for:

* Frontend development
* Backend development
* Database development
* API design
* Authentication integration
* Testing
* Debugging
* Code review
* Git workflow
* Deployment
* Technical documentation

---

## Product Backlog

### Module 1 — Authentication & User Verification

* [ ] UGM email verification
* [ ] User registration
* [ ] RBAC
* [ ] Student profile
* [ ] Workout preference setup
* [ ] Verified UGM profile badge

### Module 2 — Partner Matching & Scheduling

* [ ] Schedule Sync Grid
* [ ] Workout partner matching
* [ ] Fitness preference filtering
* [ ] Workout invitations
* [ ] Match status management
* [ ] Match compatibility scoring

### Module 3 — Social Safety & Moderation

* [ ] User reliability rating
* [ ] No-show tracking
* [ ] Reliability score calculation
* [ ] User reporting
* [ ] User blocking
* [ ] IT Admin moderation dashboard
* [ ] Report status management
* [ ] Moderation actions

### Module 4 — Communication

* [ ] In-app direct messaging
* [ ] Conversation management
* [ ] Message notifications
* [ ] Workout invitation notifications
* [ ] Session request notifications
* [ ] Reservation notifications

### Module 5 — Facility Management

* [ ] Facility selection
* [ ] Student check-in
* [ ] Live occupancy tracking
* [ ] Capacity status
* [ ] Gym slot reservations
* [ ] QR check-in generation
* [ ] QR verification
* [ ] Automated no-show release
* [ ] Overstay release
* [ ] Peak-hour reservation limits

---

## Reservation Logic

The reservation system follows a controlled lifecycle:

```text
Available
    │
    ↓
Reserved
    │
    ├── QR Check-In within 15 minutes
    │          ↓
    │       Active
    │          │
    │          ↓
    │       Completed
    │
    └── No Check-In within 15 minutes
               ↓
           Auto Released
               ↓
           Available
```

During peak hours:

```text
Student
   │
   ↓
Check Existing Active Reservation
   │
   ├── Active Peak Reservation → Reject New Reservation
   │
   └── No Active Peak Reservation
              ↓
        Allow Reservation
```

---

## Matching Concept

The matching system considers multiple compatibility factors rather than simply matching students randomly.

```text
Student Availability
        +
Workout Discipline
        +
Workout Goal
        +
Workout Pacing
        +
Preferred Facility
        ↓
Compatibility Calculation
        ↓
Ranked Partner Suggestions
```

This allows students to discover partners who are compatible both in terms of **when they train** and **how they train**.

---

## Project Goals

UGM Gym Partner aims to solve several common problems faced by students using campus fitness facilities:

* Difficulty finding workout partners with compatible schedules
* Students working out alone because friends are unavailable
* Lack of real-time gym occupancy information
* Fragmented campus fitness facilities
* Difficulty coordinating workout sessions
* No reliable way to identify consistent workout partners
* Lack of campus-specific reporting and moderation tools
* Unnecessary sharing of personal contact information
* Gym slots being wasted by no-shows
* Unequal access during peak facility hours

The platform addresses these problems through a combination of **partner matching, social accountability, communication tools, and facility management**.

---

## Project Scope

This platform is designed specifically for the Universitas Gadjah Mada campus ecosystem.

Supported facilities:

* GMC
* Lembah
* UGM Residence
* GIK Gym

Access is restricted to authorized UGM users and campus facility operations.

---

## Academic Context

This project is developed as part of the **Software Engineering (RPL)** coursework at **Universitas Gadjah Mada**.

The project demonstrates the implementation of:

* Agile software development
* Scrum
* Full-stack web development
* Modular software architecture
* Authentication and authorization
* Database-driven applications
* Real-time systems
* Scheduling and matching algorithms
* Social safety and moderation
* In-app communication
* Facility management systems
* User-centered software design

---

## License

This project is developed for academic purposes as part of Universitas Gadjah Mada coursework.

The system is intended for use within the defined UGM campus scope.
