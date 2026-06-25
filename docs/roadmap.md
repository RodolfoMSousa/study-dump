# Roadmap — Modular Fullstack Web System

## Overview

This project has two primary goals:

1. Build a modular web application deployed to production.
2. Develop practical skills in architecture, backend, frontend, DevOps, and system operations.

The project is **education-first** and **product-second**.

---

# Learning Objectives

By the end of this project, the developer should be able to:

* Design modular systems
* Build modern Python APIs
* Work with relational databases
* Use caching and asynchronous processing
* Deploy applications to the cloud
* Automate testing and deployments
* Monitor production systems
* Operate and evolve real-world applications

---

# Official Technology Stack

## Backend

* Python 3.12+
* FastAPI
* SQLAlchemy 2.0
* Alembic
* Pydantic v2

## Database

* PostgreSQL
* Redis

## Frontend (Phase 1)

* HTMX
* Jinja2

## Frontend (Future)

* React
* Next.js

## Infrastructure

* Docker
* Docker Compose

## Observability

* Prometheus
* Grafana

## CI/CD

* GitHub Actions

## Cloud

* Render or Railway
* Linux VPS
* AWS

---

# Architectural Principles

Architecture style:

**Modular Monolith**

Expected structure:

```text
app/
    core/
    users/
    podcasts/
    youtube/
    movies/
    shortener/
```

Each module should contain:

```text
router/
service/
repository/
models/
schemas/
```

Design principles:

* High cohesion
* Low coupling
* Testability
* Observability
* Security
* Incremental evolution

Core question:

> "Can a new module be added without modifying existing modules?"

---

# Project Modules

## Core

Responsibilities:

* Authentication
* Authorization
* User management
* Dashboard
* Navigation
* Module registration

---

## Podcasts

Features:

* RSS feed ingestion
* XML parsing
* Podcast subscriptions
* Favorite episodes

---

## YouTube

Features:

* Channel subscriptions
* Video synchronization
* User feeds

---

## URL Shortener

Features:

* Base62 encoding
* Short URL generation
* Redirect handling
* Click statistics

---

## Movie Catalog

Features:

* TMDB integration
* Watchlists
* Watched movies
* User ratings

---

# Phase 0 — Architecture & Planning

## Goals

Understand the architectural foundations of the system.

## Study Topics

* Modular Monolith
* Clean Architecture
* Hexagonal Architecture
* Strategic DDD
* Bounded Contexts
* Aggregates
* Repositories
* SOLID Principles

## Exercises

* Draw the system architecture diagram
* Define module boundaries
* Identify core entities
* Map dependencies between modules

## Completion Criteria

* Architecture documented
* Modules defined
* Dependencies identified

## Skills Acquired

* Software Architecture
* Domain Modeling
* System Design

---

# Phase 1 — Local Infrastructure

## Goals

Create a fully reproducible development environment.

## Study Topics

* Docker
* Docker Compose
* Networks
* Volumes
* Environment variables
* Database migrations

## Implement

Run locally:

* API
* PostgreSQL
* Redis

Using:

```bash
docker compose up
```

## Exercises

* Create Dockerfile
* Configure docker-compose.yml
* Persist database volumes
* Run migrations automatically

## Completion Criteria

* Environment runs on a clean machine
* Database persists data
* Migrations work correctly

## Skills Acquired

* Docker
* Infrastructure
* Databases

---

# Phase 2 — Core & Authentication

## Goals

Implement user management and authentication.

## Study Topics

* JWT
* OAuth2
* Password hashing
* Sessions
* Cookies
* RBAC

## Implement

* User registration
* Login
* Logout
* Refresh tokens
* User profile

## Exercises

Answer:

* What is the difference between authentication and authorization?
* When should JWT be used?
* When are sessions preferable?

## Completion Criteria

* Users can authenticate
* Protected routes work correctly
* Permissions are enforced

## Skills Acquired

* Authentication
* Authorization
* Security

---

# Phase 3 — Modular Architecture

## Goals

Build an extensible modular architecture.

## Study Topics

* SOLID
* Dependency Injection
* Dependency Inversion
* Interfaces
* Code organization

## Exercises

Add a new module without modifying existing modules.

## Completion Criteria

* Low coupling
* Clear dependencies
* Easy extensibility

## Skills Acquired

* Modular Design
* Maintainability
* Extensibility

---

# Phase 4 — Podcast Aggregator

## Goals

Consume RSS feeds.

## Study Topics

* XML
* RSS
* HTTP
* Parsing

## Implement

* Feed registration
* Episode synchronization
* Podcast subscriptions
* Favorites

## Completion Criteria

* Feeds update correctly
* Data persists in the database

## Skills Acquired

* External Integrations
* Data Processing

---

# Phase 5 — YouTube Integration

## Goals

Integrate with external APIs.

## Study Topics

* REST APIs
* Pagination
* Rate limiting
* Caching
* API quotas

## Implement

* Channel subscriptions
* Video synchronization
* User feeds

## Completion Criteria

* API integration works reliably
* Cache reduces API calls

## Skills Acquired

* API Integration
* Scalability
* Caching

---

# Phase 6 — Movie Catalog

## Goals

Consume public APIs and manage user data.

## Study Topics

* TMDB API
* Pagination
* Data modeling

## Implement

* Search movies
* Watchlists
* Watched movies
* User ratings

## Completion Criteria

* Users manage their personal movie catalog

## Skills Acquired

* Data Modeling
* API Integration

---

# Phase 7 — URL Shortener

## Goals

Learn URL redirection and identifier generation.

## Study Topics

* Base62 encoding
* Hash generation
* HTTP redirects
* URL normalization

## Implement

* Short URL generation
* 301/302 redirects
* Click analytics

## Completion Criteria

* Short URLs redirect correctly
* Click statistics are stored

## Skills Acquired

* HTTP Fundamentals
* Identifier Design
* Analytics

---

# Phase 8 — Asynchronous Processing

## Goals

Process background jobs outside request/response cycles.

## Study Topics

* Celery
* Redis
* Workers
* Scheduling
* Message queues

## Implement

Background tasks for:

* RSS synchronization
* YouTube synchronization
* Notifications

## Completion Criteria

* Long-running tasks execute asynchronously
* Failures are handled properly

## Skills Acquired

* Distributed Processing
* Job Queues
* Reliability

---

# Phase 9 — Testing

## Goals

Build confidence and maintainability through automated tests.

## Study Topics

* Unit testing
* Integration testing
* API testing
* Mocking

## Tools

* pytest
* unittest.mock
* Docker databases

## Completion Criteria

* Critical flows are tested
* CI executes tests automatically

## Skills Acquired

* Quality Assurance
* Automated Testing

---

# Phase 10 — Observability

## Goals

Monitor and diagnose production systems.

## Study Topics

* Structured logging
* Metrics
* Distributed tracing

## Tools

* Prometheus
* Grafana

## Questions to Answer

* How do we detect failures?
* How do we measure performance?
* How do we investigate incidents?

## Completion Criteria

* Dashboards exist
* Metrics are collected
* Logs are searchable

## Skills Acquired

* Monitoring
* Incident Response
* Performance Analysis

---

# Phase 11 — CI/CD

## Goals

Automate build, test, and deployment workflows.

## Study Topics

* GitHub Actions
* Continuous Integration
* Continuous Deployment

## Implement

* Automated tests
* Linting
* Build pipelines
* Deployment pipelines

## Completion Criteria

* Code is automatically tested
* Deployments are automated

## Skills Acquired

* DevOps
* Automation

---

# Phase 12 — Deployment & Cloud

## Goals

Deploy and operate the application in production.

## Deployment Path

1. Render or Railway
2. Linux VPS
3. AWS

## AWS Topics

* EC2
* RDS
* S3
* IAM
* CloudFront

## Completion Criteria

* Application is publicly accessible
* HTTPS is configured
* Backups exist
* Monitoring is enabled

## Skills Acquired

* Cloud Computing
* Operations
* Production Engineering

---

# Success Criteria

The project is considered complete when the developer can:

* Design a modular system
* Build and deploy APIs
* Operate production infrastructure
* Monitor applications
* Debug incidents
* Automate deployments
* Evolve the system safely

The final goal is not the application itself.

The final goal is becoming a stronger software engineer.
