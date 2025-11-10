HacknHex is an online platform built for coders — from beginners learning basics to competitive programmers preparing for contests. It combines a curated problem set, a timed contest engine, leaderboards, a discussion forum for editorial-style explanations, and automated judge support for multiple languages.

Goals:

Make practice consistent, trackable, and social.

Provide fair, fast judging for algorithmic problems.

Allow creators to publish and moderate contest/problem content.

Features

Problem library (tags, difficulty, editorial)

Fast judge supporting multiple languages (e.g., Java, Python, C++, JavaScript)

Contests: timed, ranked, private/public modes

Practice mode with detailed submissions and test-case feedback

Leaderboards and progress tracking

User profiles (achievements, solved problems)

Problem-authoring tools (test cases, sample I/O, scoring config)

Discussion threads per problem and contest

Admin dashboard for moderation and analytics

CI-friendly problem packaging (for import/export)

Tech Stack (suggested)

Frontend: React + TypeScript (or Next.js)

Styling: Tailwind CSS

Backend: Node.js (Express / NestJS) or Spring Boot (Java)

Database: PostgreSQL (primary), Redis (caching / queue)

Judge / Executor: Containerized sandbox (Docker, resource-limited)

Authentication: JWT / OAuth2 (GitHub, Google)

CI/CD: GitHub Actions / GitLab CI

Hosting: Vercel / Netlify (frontend), AWS / DigitalOcean (backend & judge)

Adjust the stack to your team’s experience and scale needs.

Getting Started
Prerequisites

Node.js (v18+) and npm / pnpm / yarn

Java (if judge supports Java)

Docker (for running judge sandbox locally)

PostgreSQL (or a dev-friendly SQLite alternative)

Usage
For Learners

Sign up / log in.

Browse problems by tags and difficulty.

Use the built-in code editor or connect your local setup.

Submit code; view results and per-test feedback.

Join live contests or create a private contest for practice.

For Problem Authors / Admins

Create problem with clear statement, constraints, and samples.

Add canonical test cases (public/private) and optional scoring rules.

Preview in local judge before publishing.

Moderate discussions and approve editorial content.

Architecture & Design

Client talks to API over HTTPS.

API handles user auth, problem CRUD, contest orchestration, and storage.

Judge is isolated: receives jobs via a queue (Redis/RabbitMQ), runs them inside containers, and sends results back.

Database stores users, problems, submissions; test cases stored in secure blob or DB with access controls.

Caching for leaderboard and heavy reads via Redis.

Scaling: Horizontally scale API and judge workers. Use autoscaling for contest peaks.

Contributing

We welcome contributors. Please follow these steps:

Fork the repo and create a feature branch: feature/describe-change

Follow the coding style and tests before opening a PR.

Add unit tests for new features or bug fixes.

Open a PR with a clear description and link to issues (if any).

Maintainers will review and merge.

Contributor checklist:

Linted code (npm run lint)

Tests added and passing

No sensitive info in commits or config

Deployment

A simple deployment flow:

Build frontend and deploy to Vercel/Netlify.

Build backend Docker image and push to registry.

Deploy backend to a cloud provider (AWS ECS / DigitalOcean App Platform / Kubernetes).

Run judge workers as separate autoscaled service with restricted privileges.

Use managed databases, secrets manager, and a CDN for static assets.

Monitor with Prometheus/Grafana and set alerts for judge failures, queue buildup, and DB errors.

Roadmap

Planned improvements:

Expand language support and better sandbox isolation

Gamification: badges, streaks, and skill maps

Team contests with live scoreboard updates

Problem-import tools (Codeforces / SPOJ format)

Mobile-friendly UI and offline practice mode22222
