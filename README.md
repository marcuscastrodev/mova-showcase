<div align="center">

# mova.

### Freelance work, in motion.

**A full-stack workspace for clients, projects, tasks, calendars, partners, and finances.**

A product engineering case study by **Marcus Castro** · **MOVA, by EMI**

[![Explore product](https://img.shields.io/badge/Explore_the_product-10281B?style=for-the-badge)](#the-product)
[![Engineering](https://img.shields.io/badge/Engineering_decisions-DBA821?style=for-the-badge&labelColor=10281B)](#engineering-decisions)
[![Private demo](https://img.shields.io/badge/Private_demo-181818?style=for-the-badge)](https://mova.agenciaemi.com)

**Next.js 16 · React 19 · TypeScript · Supabase · PostgreSQL · Tailwind CSS 4**

</div>

> **Portfolio case study, not an open-source application.** The production code remains private. This repository documents the product, the implementation approach, and engineering decisions without exposing proprietary source, credentials, or customer data. Demo access is restricted.

## The problem

Freelancers and small creative teams often manage clients, projects, deadlines, collaborators, and finances across disconnected tools. Work gets harder to follow when a delivery milestone, assigned task, and payment history are managed in different places.

**MOVA explores one connected workspace** for the day-to-day operations of a small service business.

## The product

The interface is organized around a consistent sidebar, workspace context, and direct access to the main workflows.

| Area | Product experience |
| :--- | :--- |
| **Home dashboard** | Active projects, clients, pending and overdue tasks, upcoming events, and personal notes |
| **Clients** | Customer records, lifecycle status, search, and related projects |
| **Projects** | Status-based management, deadlines, client relationships, filters, and list/board views |
| **Tasks** | Kanban, priorities, assignees, deadlines, and progress states |
| **Calendar** | Month, week, and list views; events, deadlines, and time-zone-aware scheduling |
| **Partners** | External collaborators associated with projects |
| **Finance** | Receivables, payables, partial settlements, reversals, cancellation history, and balances |

### Interface walkthrough

**01 — Onboarding and sign-in.** A focused entry screen communicates the core value proposition and offers account creation and sign-in options.

**02 — Workspace dashboard.** Summary cards and a prioritized task list create an operational overview without requiring navigation between modules.

**03 — Project management.** Search, status, client, visibility, and sorting controls support daily project operations.

**04 — Calendar.** A month grid makes appointments and deadlines easy to scan, with additional week and list modes.

> Authentic screenshots of these four views have been captured from the private demonstration and are being prepared for publication after removing identifying session details. See [gallery notes](screenshots/README.md). No image placeholders are embedded here, so the README remains fully functional until the approved files are uploaded.

## Design decisions

- **Information hierarchy:** key metrics and immediate actions appear before detailed task lists.
- **Consistent navigation:** a persistent sidebar makes client, project, task, calendar, partner, and finance workflows predictable.
- **Action-oriented dashboard:** quick-create buttons reduce the steps required to add a task, project, client, or event.
- **Meaningful states:** overdue work receives visual emphasis; project and task states use labels alongside color.
- **Workspaces as context:** the active workspace and role remain visible throughout the experience.

## Product highlights

- **Multi-tenant architecture:** workspaces, membership roles, and workspace-scoped data access.
- **Database authorization:** Supabase Auth, PostgreSQL Row Level Security (RLS), database functions, and validated server actions.
- **Financial workflows:** partial payments, settlement history, reversals, cancellation rules, and duplicate-submission safeguards.
- **Date and time semantics:** workspace-specific time zones with separate handling for dates, timed events, and all-day events.
- **Reproducible deployment:** multi-stage Docker build, standalone Next.js server, and deployment on Render.
- **Automated verification:** TypeScript checks, unit tests, Playwright end-to-end tests, and PostgreSQL/pgTAP coverage.

## Tech stack

| Layer | Technologies |
| :--- | :--- |
| Frontend | Next.js 16, React 19, TypeScript, Tailwind CSS 4 |
| Backend | Next.js App Router, Server Components, Server Actions, Supabase |
| Database | PostgreSQL 17, SQL migrations, RLS, RPCs, triggers |
| Authentication | Supabase Auth and HTTP Basic access gate for the private demo |
| Testing | Playwright, unit tests, pgTAP |
| Delivery | GitHub, Docker, Render |
| Interface | Manrope, Geist, responsive SaaS UI |

## Architecture at a glance

```text
Browser
  |
  v
Render HTTPS + HTTP Basic demo gate
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

Authorization is enforced in the data layer as well as the application. Database rules protect workspace boundaries and financial state transitions.

## Engineering decisions

### 01 — Isolating tenant data

Workspace memberships and roles determine access. PostgreSQL RLS and server-side checks protect records independently of whether a control is visible in the interface.

### 02 — Preserving financial history

Partial settlements and reversals require accounting for what happened, not just changing a current balance. The system maintains a settlement history and guards important transitions.

### 03 — Handling dates correctly

A calendar date is not always a timestamp. MOVA distinguishes deadlines, timed meetings, and all-day events, while supporting workspace-specific time zones.

### 04 — Demonstrating a SaaS privately

The demonstration runs in a dedicated environment using sample data, protected by an HTTP Basic gate and application authentication. The public showcase does not provide access credentials.

## Live demonstration

**[mova.agenciaemi.com](https://mova.agenciaemi.com)** · **Private access, available on request**

This is an active product prototype, not a public SaaS launch. The demo is intended to illustrate existing product flows with fictional data.

## Documentation

| Read more | What's covered |
| :--- | :--- |
| [Architecture](docs/architecture.md) | Application layers, tenant authorization, security, and deployment |
| [Features](docs/features.md) | Product workflows and demo scope |
| [Engineering notes](docs/engineering.md) | Implementation decisions, challenges, and trade-offs |
| [Roadmap](docs/roadmap.md) | Current scope and future directions |
| [Screenshot gallery](screenshots/README.md) | Screenshot preparation and publication safeguards |

## My role

This project combines product requirements, interface design, full-stack implementation, relational data modeling, authorization, tests, deployment, and technical documentation.

It reflects my approach to development: **start with the user workflow, build the right data and interaction model, and validate the behavior that matters.**

## Status and next steps

**Current:** private online demonstration covering client, project, task, calendar, partner, finance, and dashboard workflows.

**Next:** complete the approved screenshot gallery; improve onboarding and collaboration; expand reporting; continue production-readiness work.

---

<div align="center">

**[Marcus Castro](https://github.com/marcuscastrodev)** · Web development · Product engineering

*MOVA, by EMI — Seus projetos em movimento.*

</div>
