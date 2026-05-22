# Planit Traveler — Travel Itinerary Platform

**Live app:** [planittraveler.com](https://planittraveler.com)

Production full-stack SaaS built and self-deployed solo — no team, no budget, no shortcuts.

## What It Does

A collaborative travel itinerary platform where users can build, share, and export 
detailed trip plans. Designed for real production from day one.

## Technical Highlights

### 🔐 Auth & Security
Custom JWT authentication using HttpOnly cookies + CSRF token validation — deliberately 
avoiding the localStorage anti-pattern to protect against XSS and CSRF attacks simultaneously.

### 👥 Collaboration System
Full role-based access control with invite/accept/decline flow. Three permission tiers 
(owner/editor/viewer) enforced via object-level DRF permission classes.

### 📤 Export Pipeline
Multi-format export (PDF, PNG, email) using DOM serialization with cross-browser formatting 
preservation — the platform's core monetization feature.

### ⚡ Frontend Performance
High-performance data tables via TanStack Table + react-virtual with drag-drop reordering 
and inline rich-text editing through custom TipTap extensions.

### 🛡️ Production Ops
Rate limiting on public endpoints, spam detection heuristics, soft-delete on comments, 
admin email alerts, and cascade-aware database protection rules.

## Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React, Tailwind CSS, TanStack Table, TipTap, react-virtual |
| Backend | Django, Django REST Framework, PostgreSQL |
| Auth | Custom JWT + HttpOnly cookies + CSRF validation |
| DevOps | Hetzner VPS, Nginx, SSL/TLS, Linux (Ubuntu) |

## Architecture Decisions

- **Self-hosted over managed:** Deployed on Hetzner VPS with Nginx reverse proxy for 
  full control over infrastructure and cost
- **Custom auth over Auth0/Firebase:** Built JWT auth from scratch to understand and 
  control the full security surface
- **DRF over GraphQL:** REST with object-level permissions was the right fit for this 
  access control model

## About

Built by [Faris Khammash](https://linkedin.com/in/fariskhammash) — full-stack engineer 
with a background in biomedical engineering and 6 years in regulated biotech environments.
