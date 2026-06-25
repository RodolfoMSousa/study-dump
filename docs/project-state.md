# Project State

**Project:** Modular Fullstack Web System
**Repository:** <repository-url>
**Current Date:** YYYY-MM-DD

---

# Project Vision

Build a production-ready modular web application while learning:

* Python backend development
* Frontend development
* DevOps
* Cloud deployment
* Observability
* Production operations

The project is **education-first** and **product-second**.

---

# Current Phase

**Phase:** 0 — Architecture & Planning

**Status:** In Progress

**Overall Progress:** 0%

---

# Current Sprint

## Sprint Goal

Define the initial architecture and bootstrap the repository.

## Expected Deliverables

* [ ] Create repository structure
* [ ] Create AGENTS.md
* [ ] Create roadmap.md
* [ ] Create architecture.md
* [ ] Create project-state.md
* [ ] Define module boundaries
* [ ] Select initial frontend approach
* [ ] Create initial ADR

---

# Active Tasks

## High Priority

* [ ] Decide between HTMX/Jinja2 and React/Next.js for Phase 1
* [ ] Define package structure
* [ ] Design database entities
* [ ] Create architecture diagram

## Medium Priority

* [ ] Study Modular Monolith architecture
* [ ] Study Clean Architecture concepts
* [ ] Study Strategic DDD

## Low Priority

* [ ] Research deployment providers
* [ ] Compare Render vs Railway

---

# Project Modules

| Module    | Status      | Notes                        |
| --------- | ----------- | ---------------------------- |
| Core      | Not Started | Authentication and dashboard |
| Users     | Not Started | Registration and RBAC        |
| Podcasts  | Not Started | RSS ingestion                |
| YouTube   | Not Started | API integration              |
| Movies    | Not Started | TMDB integration             |
| Shortener | Not Started | URL shortening               |

Status values:

* Not Started
* In Progress
* Completed
* Blocked

---

# Technology Decisions

## Backend

**Decision:** Python + FastAPI

**Status:** Approved

---

## Database

**Decision:** PostgreSQL + Redis

**Status:** Approved

---

## Infrastructure

**Decision:** Docker + Docker Compose

**Status:** Approved

---

## Frontend

**Decision:** TBD

**Candidates:**

* HTMX + Jinja2
* React + Next.js

**Current Recommendation:**

Start with HTMX + Jinja2.

---

# Skill Matrix

Evaluate skills from 0 to 5.

| Skill         | Level | Notes               |
| ------------- | ----: | ------------------- |
| Python        |   1/5 | Learning ecosystem  |
| FastAPI       |   0/5 | Not started         |
| SQLAlchemy    |   0/5 | Not started         |
| Docker        |   1/5 | Basic usage         |
| Linux         |   2/5 | WSL environment     |
| PostgreSQL    |   3/5 | Existing experience |
| Redis         |   0/5 | Not started         |
| CI/CD         |   1/5 | Learning            |
| AWS           |   0/5 | Not started         |
| Observability |   0/5 | Not started         |
| Security      |   2/5 | Existing knowledge  |

---

# Technical Debt

Currently identified debt:

* None

Guidelines:

* Record debt immediately when discovered.
* Include impact and proposed mitigation.

Template:

```text
Debt:
Impact:
Mitigation:
Priority:
```

---

# Architectural Risks

## Risk 1

**Description:**
Frontend technology still undecided.

**Impact:**
May require future refactoring.

**Mitigation:**
Start with the simplest approach.

**Status:**
Open

---

# Open Questions

Questions that still need answers:

1. Should authentication use JWT only or sessions as well?
2. Will modules share database schemas?
3. How should permissions be modeled?
4. Should APIs be versioned from the start?
5. How will background jobs be scheduled?

---

# Decisions Log

## 2026-06-15

* Adopt Modular Monolith architecture.
* Use Python as backend language.
* Use PostgreSQL as primary database.
* Use Redis for caching and background jobs.
* Prefer HTMX + Jinja2 for the initial frontend.

---

# Milestones

## Milestone 1 — Repository Bootstrap

Status: In Progress

Requirements:

* [ ] Repository initialized
* [ ] Documentation created
* [ ] Initial architecture defined

---

## Milestone 2 — Local Infrastructure

Status: Not Started

Requirements:

* [ ] Dockerfile created
* [ ] docker-compose.yml created
* [ ] PostgreSQL container running
* [ ] Redis container running
* [ ] API starts successfully

---

## Milestone 3 — Authentication

Status: Not Started

Requirements:

* [ ] Registration
* [ ] Login
* [ ] JWT
* [ ] Refresh tokens
* [ ] Protected routes

---

## Milestone 4 — First Deploy

Status: Not Started

Requirements:

* [ ] Production environment configured
* [ ] HTTPS enabled
* [ ] Public URL available

---

# Learning Journal

Use this section to record discoveries and lessons learned.

Example:

```markdown
## 2026-06-20

Learned how Docker networks work.

Key takeaway:
Containers communicate using service names instead of IP addresses.
```

---

# Session Startup Instructions for the Agent

At the beginning of every session:

1. Read this file.
2. Read AGENTS.md.
3. Read architecture.md.
4. Read roadmap.md.
5. Summarize current progress.
6. Identify blockers.
7. Suggest next actions.
8. Update this file when appropriate.

---

# Definition of Success

The project succeeds when the developer can:

* Design modular systems
* Build production APIs
* Deploy applications
* Operate cloud infrastructure
* Monitor systems
* Troubleshoot incidents
* Continuously evolve the platform

The true deliverable is engineering capability, not only software.
