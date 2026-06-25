# Architecture Documentation

## Project

Modular Fullstack Web System

---

# Purpose

This document describes the high-level architecture of the system, its guiding principles, module boundaries, and major technical decisions.

Detailed architectural decisions should be recorded as ADRs under:

```text
docs/decisions/
```

---

# System Goals

The system is designed to:

* Support modular growth
* Be easy to maintain
* Enable incremental learning
* Be deployable to production
* Encourage good engineering practices
* Remain simple while scalable

This project is educational first and product second.

---

# Architectural Style

## Chosen Architecture

**Modular Monolith**

The system is implemented as a single deployable application with clearly separated modules.

### Why Modular Monolith?

Benefits:

* Lower operational complexity
* Easier deployment
* Easier local development
* Clear module boundaries
* Simpler debugging
* Better learning experience

Microservices are intentionally avoided in early stages to reduce unnecessary complexity.

---

# High-Level Architecture

```text
                    ┌─────────────────┐
                    │     Browser     │
                    └────────┬────────┘
                             │
                             │ HTTP/HTTPS
                             │
                    ┌────────▼────────┐
                    │    FastAPI      │
                    │ Application API │
                    └────────┬────────┘
                             │
      ┌──────────────────────┼──────────────────────┐
      │                      │                      │
      ▼                      ▼                      ▼
 ┌──────────┐         ┌──────────┐          ┌──────────┐
 │PostgreSQL│         │  Redis   │          │ Celery   │
 │ Database │         │ Cache    │          │ Workers  │
 └──────────┘         └──────────┘          └──────────┘
```

---

# Technology Stack

## Backend

* Python 3.12+
* FastAPI
* SQLAlchemy 2.0
* Alembic
* Pydantic v2

## Database

### PostgreSQL

Responsibilities:

* Persistent storage
* Transactions
* Relational data
* User data
* Business entities

### Redis

Responsibilities:

* Caching
* Session storage
* Rate limiting
* Message broker
* Background jobs

---

## Background Processing

### Celery

Responsibilities:

* RSS synchronization
* YouTube synchronization
* Scheduled tasks
* Long-running jobs

---

## Frontend

### Initial Phase

* Jinja2
* HTMX

Goals:

* Learn HTTP fundamentals
* Learn server-side rendering
* Reduce frontend complexity

### Future Evolution

* React
* Next.js

---

# Module Structure

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

Each module should follow:

```text
module/
    router/
    service/
    repository/
    models/
    schemas/
```

---

# Module Responsibilities

## Core

Responsibilities:

* Application startup
* Dependency injection
* Configuration
* Logging
* Security
* Shared utilities

---

## Users

Responsibilities:

* Registration
* Authentication
* Authorization
* User profiles
* Preferences

---

## Podcasts

Responsibilities:

* RSS feed ingestion
* XML parsing
* Podcast subscriptions
* Favorites

---

## YouTube

Responsibilities:

* Channel subscriptions
* Video synchronization
* User feeds

---

## Movies

Responsibilities:

* TMDB integration
* Watchlists
* Watched history
* Ratings

---

## Shortener

Responsibilities:

* URL generation
* Redirect handling
* Click analytics

---

# Design Principles

The system should follow:

## SOLID Principles

* Single Responsibility Principle
* Open/Closed Principle
* Liskov Substitution Principle
* Interface Segregation Principle
* Dependency Inversion Principle

---

## High Cohesion

Each module should have a clear responsibility.

---

## Low Coupling

Modules should interact through explicit interfaces.

Avoid:

* Circular dependencies
* Shared mutable state
* Cross-module database access

---

# Dependency Rules

Allowed:

```text
router → service → repository → database
```

Avoid:

```text
repository → router
service → HTTP layer
module → module internals
```

Modules should communicate through public interfaces only.

---

# Data Flow

Example request flow:

```text
Client Request
      │
      ▼
Router
      │
      ▼
Service Layer
      │
      ▼
Repository Layer
      │
      ▼
Database
```

Response flow:

```text
Database
      │
      ▼
Repository
      │
      ▼
Service
      │
      ▼
Router
      │
      ▼
Client
```

---

# Authentication Strategy

Authentication:

* JWT Access Tokens
* Refresh Tokens

Password storage:

* Argon2 or bcrypt

Authorization:

* Role-Based Access Control (RBAC)

---

# API Design Principles

API style:

* RESTful APIs

Guidelines:

* Version APIs when necessary
* Use consistent naming conventions
* Return structured errors
* Validate all inputs
* Document endpoints automatically

---

# Database Principles

Guidelines:

* Normalize data initially
* Optimize only when needed
* Use indexes intentionally
* Prefer explicit migrations
* Avoid premature optimization

---

# Caching Strategy

Redis may be used for:

* API responses
* External API calls
* Rate limiting
* Session data

Caching should be introduced only after identifying bottlenecks.

---

# Error Handling

Principles:

* Fail fast
* Log useful information
* Avoid leaking sensitive data
* Return meaningful error messages

---

# Security Principles

Requirements:

* Hash passwords
* Validate inputs
* Escape outputs
* Protect secrets
* Use HTTPS in production
* Enforce least privilege

Never commit:

* API keys
* Secrets
* Passwords
* Tokens

Use environment variables instead.

---

# Observability

The system should expose:

## Logs

* Structured logs
* Request IDs
* Error tracking

## Metrics

* Request count
* Response time
* Error rates

## Tracing

* Request tracing
* Background job tracing

---

# Deployment Strategy

Deployment progression:

1. Local Docker
2. Render or Railway
3. Linux VPS
4. AWS

Production requirements:

* HTTPS
* Automated backups
* Monitoring
* Health checks

---

# Definition of Done

A feature is complete only if:

* Code works
* Tests pass
* Documentation exists
* Logs exist
* Security is considered
* Deployment succeeds

---

# Architectural Questions

Before implementing any feature, ask:

1. Which module owns this responsibility?
2. Can this be tested independently?
3. Does this increase coupling?
4. How will this scale?
5. How will this be monitored?
6. How will it evolve in the future?

Architecture is the art of making future changes easier.
