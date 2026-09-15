# 🏋️ UGM Gym Partner & Facility Tracker

> An AI-powered workout partner matching and gym capacity monitoring platform built exclusively for Universitas Gadjah Mada (UGM) students.

UGM Gym Partner is a campus-focused fitness platform designed to help UGM students find compatible workout partners, coordinate workout schedules, and monitor gym facility capacity in real time.

The platform combines **UGM student verification, workout partner matching, schedule synchronization, facility check-ins, occupancy monitoring, and QR-based reservations** into a single campus fitness ecosystem.

Created by:
Akhnaf Fawzan Yogatrisna - 24/536720/TK/59561 - Full-stack Developer
Musa Hanif Moeljawan - 24/536720/TK/59561 - Full-stack Developer

---

## Features

### Authentication & User Verification

* UGM email verification using `@mail.ugm.ac.id`
* Campus-only user access
* Role-Based Access Control (RBAC)
* Student and facility manager portals
* Verified UGM student profile
* Workout style and pacing preferences

### Workout Partner Matching

Find compatible workout partners based on:

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

### Schedule Sync

Students can enter their available workout hours through a visual schedule grid.

The system identifies students with overlapping free time, making it easier to find workout partners who can train at the same time.

### Real-Time Spotter Beacon

Students can broadcast a **Spotter Beacon** when they need assistance during a workout.

Nearby students training at the same facility can receive notifications and respond to the request.

### Facility Check-In

Students can select their current workout location from supported UGM facilities:

* GMC
* Lembah
* UGM Residence
* GIK Gym

The selected facility is displayed as part of the student's active workout status.

### Live Gym Occupancy

Facility managers can monitor gym occupancy across supported facilities.

The system provides capacity indicators:

* 🟢 Low
* 🟡 Moderate
* 🔴 Peak / High Capacity

This helps facility managers identify overcrowding and monitor facility usage.

### Slot Reservation & QR Check-In

Students can reserve gym slots and receive a unique QR check-in pass.

Facility managers can scan the QR code to verify the student's reservation and entry status.

---

## Core Modules

The system is organized into three main modules:

| Module                                 | Description                                                                               |
| -------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Authentication & User Verification** | UGM email verification, RBAC, user profiles, and workout preferences                      |
| **Partner Matching & Schedule Sync**   | Schedule synchronization, partner matching, filters, Spotter Beacon, and partner requests |
| **Facility & Capacity Monitoring**     | Facility check-in, occupancy monitoring, slot reservations, and QR verification           |

---

## User Roles

| Role                 | Responsibilities                                                                                    |
| -------------------- | --------------------------------------------------------------------------------------------------- |
| **Student Lifter**   | Find workout partners, manage schedules, check into facilities, reserve slots, and request spotters |
| **Facility Manager** | Monitor gym occupancy and verify student check-ins                                                  |
| **IT Admin**         | Manage users, roles, permissions, and system access                                                 |

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
│   ├── Schedule Sync
│   ├── Workout Preferences
│   ├── Partner Matching
│   ├── Spotter Beacon
│   └── Partner Requests
│
└── Facility Management
    ├── Facility Check-In
    ├── Occupancy Tracking
    ├── Slot Reservation
    └── QR Verification
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

* [Node.js](https://nodejs.org/) v18+
* [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* [Git](https://git-scm.com/)

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

> Do not commit your `.env` file to GitHub.

### Database

Start the local PostgreSQL environment using Docker:

```bash
docker compose up -d
```

Configure the database according to your project's database setup before running the application.

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
│   │   └── facility/
│   │       └── # Occupancy & QR check-in
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

The project uses the **Scrum** framework with one-week development sprints.

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

The team maintains a maximum of **2 active tasks per developer** to minimize context switching.

---

## Development Roadmap

### Authentication & User Verification

* [ ] UGM email verification
* [ ] RBAC
* [ ] Student profile
* [ ] Workout preference setup

### Partner Matching

* [ ] Schedule Sync Grid
* [ ] Workout partner matching
* [ ] Fitness preference filtering
* [ ] Spotter Beacon
* [ ] Partner requests

### Facility Management

* [ ] Facility selection
* [ ] Student check-in
* [ ] Live occupancy monitoring
* [ ] Gym slot reservations
* [ ] QR check-in verification

### Future Improvements

* [ ] Improved matching algorithm
* [ ] Real-time notifications
* [ ] Occupancy analytics
* [ ] Mobile-first optimization
* [ ] Performance improvements

---

## Problem & Goals

Students often face several difficulties when using campus fitness facilities:

* Finding workout partners with compatible schedules
* Working out alone because friends are unavailable
* Not knowing how crowded a facility is before arriving
* Coordinating across multiple campus fitness facilities
* Inefficient facility check-in processes
* Difficulty coordinating workout sessions

UGM Gym Partner aims to address these problems by connecting students with compatible workout partners while providing facility-level visibility and management tools.

---

## Project Scope

This platform is designed specifically for the **Universitas Gadjah Mada campus ecosystem**.

Supported facilities:

* GMC
* Lembah
* UGM Residence
* GIK Gym

Access is restricted to authorized UGM users and campus facility operations.

---

## Development Team

| Role                         | Member                   |
| ---------------------------- | ------------------------ |
| **Product Owner**            | Musa Hanif Moeljawan     |
| **Scrum Master & Developer** | Akhnaf Fawzan Yogatrisna |

### Musa Hanif Moeljawan

* Product backlog management
* User story definition
* Acceptance criteria
* Product validation

### Akhnaf Fawzan Yogatrisna

* Scrum facilitation
* GitHub Project management
* Full-stack development
* Technical implementation
* Technical blocker resolution

---

## Academic Context

This project is developed as part of the **Software Engineering (RPL)** coursework at **Universitas Gadjah Mada**.

The project demonstrates the implementation of:

* Agile software development
* Scrum
* Full-stack web development
* Modular software architecture
* Authentication and authorization
* Real-time systems
* Database-driven applications
* User-centered software design

---

## 📄 License

This project is developed for academic purposes as part of Universitas Gadjah Mada coursework.

The system is intended for use within the defined UGM campus scope.
