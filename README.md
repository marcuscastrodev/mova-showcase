<div align="center">

# mova.

### Freelance work, in motion.

**A multi-tenant workspace for managing clients, projects, tasks, calendars, partners, and finances.**

A product engineering case study by **Marcus Castro**, built as **MOVA, by EMI**.

[Live private demo](https://mova.agenciaemi.com) · [Technical overview](#architecture-at-a-glance) · [Project highlights](#project-highlights)

</div>

> **Portfolio showcase only.** The production application's source code lives in a separate private repository. This public repository documents the product, engineering decisions, and implementation experience without exposing credentials, customer information, or proprietary source.

## Explore the case study

| Documentation | Details |
| --- | --- |
| [Architecture](docs/architecture.md) | Application layers, tenancy, data protection, and deployment |
| [Features](docs/features.md) | Implemented product workflows and demo scope |
| [Engineering decisions](docs/engineering.md) | Challenges, trade-offs, and technical problem-solving |
| [Roadmap](docs/roadmap.md) | Current capabilities and planned directions |
| [Screenshots](screenshots/README.md) | Image gallery preparation and publication safety |

## The product

Freelancers and small creative teams often have to switch between spreadsheets, task boards, calendars, and invoicing tools to understand what is happening across their projects.

MOVA brings those workflows into one workspace:

| Area | What MOVA supports |
| --- | --- |
| **Clients** | Client profiles, lifecycle status, search, and project relationships |
| **Projects** | Project tracking, lifecycle states, deadlines, and progress |
| **Tasks** | Kanban workflows, priorities, ownership, deadlines, and delivery milestones |
| **Calendar** | Meetings, reminders, deadlines, time-zone-aware events, and all-day events |
| **Partners** | External collaborators and their participation in projects |
| **Finance** | Receivables, payables, partial settlements, reversals, cancellation history, and balances |
| **Dashboard** | Workspace-level overview, upcoming work, progress, financial indicators, and notes |

## Project highlights

- **Multi-tenant data model:** workspaces and membership roles, with workspace-scoped access enforcement.
- **Defense in depth:** Supabase Auth, PostgreSQL Row Level Security (RLS), database functions, and an additional HTTP Basic access gate for the private demonstration.
- **Server-oriented workflows:** Next.js App Router, React Server Components, Server Actions, and validated database operations.
- **Financial integrity:** partial payments, settlement history, reversals, cancellation rules, and safeguards against duplicate submissions.
- **Time-zone handling:** workspace-specific dates and calendar events.
- **Deployment engineering:** a multi-stage Docker image, a standalone Next.js server, runtime environment configuration, and deployment on Render.
- **Automated verification:** TypeScript checks, unit tests, Playwright end-to-end tests, and PostgreSQL/pgTAP coverage.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Frontend | Next.js 16, React 19, TypeScript, Tailwind CSS 4 |
| Backend | Next.js Server Actions, Supabase |
| Database | PostgreSQL 17, SQL migrations, RLS, RPCs, triggers |
| Authentication | Supabase Auth and an HTTP Basic demo gate |
| Testing | Playwright, unit tests, pgTAP |
| Delivery | GitHub, Docker, Render |
| Design | Manrope, Geist, responsive SaaS UI |

## Architecture at a glance

```text
Browser
  |
  v
Render HTTPS + HTTP Basic access gate
  |
  v
Next.js application
  |  App Router / Server Components / Server Actions
  |  Supabase Auth session
  v
Supabase
  |  PostgreSQL
  |  Row Level Security
  |  Workspace roles and database functions
  v
Workspace-scoped product data
```

The application is designed to enforce access rules in the database rather than relying on UI visibility alone. Financial operations use database-level rules and an auditable settlement history.

## Engineering challenges

### 1. Keeping tenant data isolated
Workspace membership, roles, and RLS policies prevent one tenant from accessing another tenant's records.

### 2. Making financial workflows predictable
Receivables and payables can be partially settled; reversals retain their history. Project cancellation rules restrict what can be added after closure.

### 3. Handling real dates and time zones
Project deadlines, timed events, and all-day events require different semantics. MOVA uses a workspace time zone and preserves the distinction between calendar dates and timestamps.

### 4. Shipping a private SaaS demo safely
The demo runs in a dedicated Supabase environment and is protected by both HTTP Basic and application login. Deployment uses a reproducible Docker build.

## Live demo

**URL:** [mova.agenciaemi.com](https://mova.agenciaemi.com)

**Access:** private, available upon request. The demo requires two authentication steps. No demo credentials are published in this repository.

**Scope:** the showcase demonstrates an active product prototype with fictional sample data. It is not presented here as a publicly open registration service or a general-availability SaaS.

## Screenshots

[Screenshot gallery preparation](screenshots/README.md). Images will be published after a final review to ensure they contain **only fictional data** and no session, infrastructure, or account details.

## What I worked on

This project demonstrates end-to-end product development across:

- Product requirements and workflow design
- Relational data modeling and tenant authorization
- Full-stack application implementation
- UI interaction design and accessibility improvements
- Database-level business rules and financial workflows
- Automated testing and issue investigation
- Docker packaging and deployment
- Technical documentation and release preparation

## Status and roadmap

**Current:** private online demonstration with clients, projects, tasks, calendar, partners, finance, and a dashboard.

**Future directions:** a smoother workspace onboarding experience, broader team administration, expanded financial reporting, and production readiness improvements.

## About

**Marcus Castro** — marketing strategist and web development practitioner focused on creating digital products that connect business strategy, product thinking, and engineering.

**MOVA, by EMI** — *Seus projetos em movimento.*

---

*This is a portfolio case study. Source code, secrets, and real customer data are not distributed here.*
