# Planit Traveler

Plan a trip with other people, in one place.

**Live:** [planittraveler.com](https://planittraveler.com) · [See a trip without signing in](https://planittraveler.com/itineraries/26/reefs-tokyo-kyoto-and-osaka-1772089801)

The code is in a private repository. This page explains how the app works.

## What it does

- Build a day-by-day trip and invite people to edit it or only look at it
- Publish trips and travel posts that anyone can read

## Engineering

**Saving without overwriting each other.** Every trip has a version number. A save that started from an older version is rejected, and the person keeps their unsaved text and can copy or download it. Changes are not merged automatically.

**Sign-in.** Django REST Framework and Simple JWT, with tokens in HttpOnly cookies, CSRF checks, and sessions that end on the server when you sign out. Admin sign-in uses two-factor codes.

**Permissions.** Owner, editor and viewer roles, checked for each trip on the server.

**Rate limits.** Counted in PostgreSQL, so every server process shares one count.

**Email.** Account emails go into a PostgreSQL queue, and a separate job sends and retries them.

**Uploads and content.** Files are checked by their contents rather than their name, and HTML is cleaned on the server.

## Stack

| Layer | Technology |
|---|---|
| Frontend | React, Vite, Tailwind CSS, TipTap, TanStack Table, dnd-kit |
| Backend | Python, Django, Django REST Framework |
| Database | PostgreSQL |
| Tests | Django tests, Vitest, Playwright |
| Server | Linux on Hetzner, Nginx, Gunicorn, GitHub Actions deployment |

## About

Designed, built and run by [Faris Khammash](https://linkedin.com/in/fariskhammash), using AI coding tools. The decisions, testing and releases are mine.
