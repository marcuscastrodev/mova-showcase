# Engineering decisions and challenges

This document describes selected implementation challenges in the MOVA prototype. It is a case study, not a release of proprietary source.

## 1. Product modeling before visual polish

The application connects clients, projects, tasks, partners, events, and finances. Modeling these relationships early helps prevent disconnected workflows and makes dashboard summaries meaningful.

**Trade-off:** building shared data and lifecycle rules first requires more upfront design than implementing independent CRUD screens.

## 2. Authorization across multiple workspaces

A multi-tenant interface requires a clear boundary between records owned by different workspaces. MOVA combines authenticated application operations with PostgreSQL Row Level Security.

**Principle:** authorization belongs on the server and in the data layer, not only in frontend conditional rendering.

## 3. Finance as a sequence of events

Financial records are more complicated than a single paid/unpaid flag. MOVA supports partial settlement, reversals, and cancellation history.

**Principle:** preserve an auditable history and derive balances from supported movements instead of silently rewriting past transactions.

## 4. Business rules across project states

A cancelled project should not behave the same way as an active one. The prototype implements lifecycle-sensitive restrictions and specific cancellation handling.

**Principle:** model allowed state transitions and validate business actions close to their data.

## 5. Calendar semantics

Time-zone-aware meetings are different from date-only tasks. The workspace's time zone affects how schedules and deadlines are displayed.

**Principle:** use explicit date semantics and test boundaries, rather than assuming every date is a timestamp.

## 6. Delivering a private demo

The release uses a Dockerized Next.js build on Render and a dedicated Supabase environment. Access is protected by an additional HTTP Basic gate and application login.

**Principle:** a private portfolio demo needs reproducible deployment, operational boundaries, and realistic but fictional data.

## Verification approach

Development checks included TypeScript validation, automated tests, and read-only end-to-end walkthroughs. These checks support confidence in the demo workflows but do not imply a security certification or production SLA.

## Portfolio takeaway

MOVA demonstrates the process of turning a business problem into a connected full-stack application: feature requirements, data modeling, UI implementation, access control, business rules, testing, and deployment.

[← Back to overview](../README.md)
