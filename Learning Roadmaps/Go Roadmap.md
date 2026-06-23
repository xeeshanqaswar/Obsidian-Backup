---
title: Go Roadmap (Backend + Multiplayer Game Servers)
tags: [go, backend, multiplayer, roadmap, unity, grpc, kubernetes, kafka, websockets, security]
created: 2025-09-21
---

# Go Roadmap — Backend + Multiplayer Game Servers (Final)

**Policy:** Do the **Main** pick each month. Use the **Alt** only as a substitute if the Main doesn’t fit your style/stack. Books are supplementary—skim/deep‑dive while building; don’t let them block shipping.

---

## 🗓️ Execution Cadence (Weekly)
- [ ] **Build (6–8h):** Implement milestone features.
- [ ] **Study (3–4h):** Targeted course sections + book chapters tied to the milestone.
- [ ] **Ops (1–2h):** Tests, profiling, docs, dashboards.
- [ ] **Review (1h):** Short weekly log with key decisions/trade‑offs.

**Definition of Done (per service)**
- [ ] Automated tests; graceful shutdown; context cancellation.
- [ ] README with how‑to‑run and architecture notes.
- [ ] Basic dashboards/metrics and a load/soak test report.

---

## Month 1 — Go Core & Concurrency
**Main (Udemy):**
- [x] [Go: The Complete Developer’s Guide (Stephen Grider)](https://www.udemy.com/course/go-the-complete-developers-guide/)

**Alt (substitute):**
- [ ] [Backend Master Class \[Golang + Postgres + Kubernetes\]](https://www.udemy.com/course/backend-master-class-golang-postgresql-kubernetes/)

**Books (supplement):**
- [ ] *The Go Programming Language* — Donovan & Kernighan
- [ ] *Concurrency in Go* — Katherine Cox‑Buday
- [ ] *100 Go Mistakes and How to Avoid Them* — Teiva Harsanyi

**Milestone:**
- Build **`go-concurrent-scraper`** and **`go-tcp-chat`** with tests, race detector, and small benchmarks.

---

## Month 2 — HTTP Servers & REST (Revised)
**Main (outside Udemy):**
- [ ] [Jon Calhoun — Web Development with Go](https://www.usegolang.com/)

**Optional after Calhoun (Udemy):**
- [ ] (If/when you need a framework) pick a short **Gin** bootcamp: [Gin courses on Udemy](https://www.udemy.com/topic/gin-framework/)

**Books:**
- [ ] *API Design Patterns* — James Higginbotham
- [ ] *Designing Web APIs* — O’Reilly (Jordan/Moore et al.)

**Milestone:**
- Build **`taskapi-go`** (JWT access/refresh, RBAC, validation, CORS, health/ready) + **OpenAPI** + **load test** (hey/vegeta).

---

## Month 3 — Databases (Postgres), Migrations, Caching
**Main (Udemy):**
- [ ] [Backend Master Class \[Golang + Postgres + Kubernetes\]](https://www.udemy.com/course/backend-master-class-golang-postgresql-kubernetes/)

**Books:**
- [ ] *Designing Data‑Intensive Applications* — Martin Kleppmann
- [ ] *SQL Antipatterns* — Bill Karwin

**Milestone:**
- Build **`authsvc-go`** (signup/login/refresh, reset, email tokens) + **Redis** sessions; migrations & indexing rationale.

---

## Month 4 — Real‑time Networking & WebSockets
**Main (Udemy):**
- [ ] [Working with WebSockets in Go](https://www.udemy.com/course/working-with-websockets-in-go/)

**Alt (substitute):**
- [ ] [Golang + RabbitMQ + WebSocket at Scale (pattern)](https://www.udemy.com/topic/websocket/)

**Books:**
- [ ] *Network Programming with Go* — Adam Woodbeck
- [ ] *High Performance Browser Networking* — Ilya Grigorik (WebSocket/perf)

**Milestone:**
- Build **`ws-chatrooms-go`** (rooms, presence, heartbeats, bounded queues) + **Redis Pub/Sub**; **Unity** mini client.

---

## Month 5 — gRPC & Service Boundaries
**Main (Udemy):**
- [ ] [gRPC \[Golang\] Master Class — Stephane Maarek](https://www.udemy.com/course/grpc-golang/)

**Books/Refs:**
- [ ] *gRPC: Up & Running* — Kushwaha et al.
- [ ] Official gRPC‑Go docs (reference)

**Milestone:**
- Build **`mm-lobby-grpc`** (create/join/leave, ELO buckets, parties) + interceptors (auth/metrics) + per‑method SLOs.

---

## Month 6 — Event‑Driven Architecture & Observability
**Main (Udemy):**
- [ ] [Apache Kafka Series – Learn Apache Kafka for Beginners v3](https://www.udemy.com/course/apache-kafka/)
- [ ] [OpenTelemetry Foundations: Hands‑On Guide](https://www.udemy.com/course/opentelemetry-foundations/)

**Alt (Observability substitute):**
- [ ] [Observability in Cloud‑Native Apps using OpenTelemetry](https://www.udemy.com/topic/opentelemetry/)

**Books:**
- [ ] *Designing Event‑Driven Systems* — Ben Stopford
- [ ] *Kafka: The Definitive Guide* — (only if you choose Kafka)

**Milestone:**
- Emit/consume events (**`match_found`**, **`player_joined`**, **`game_started`**), outbox/idempotency, end‑to‑end tracing; **chaos tests**.

---

## Month 7 — Docker, Kubernetes, CI/CD, Monitoring
**Main (Udemy):**
- [ ] [Docker & Kubernetes: The Complete Guide — Stephen Grider](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/)

**Alt (deeper k8s):**
- [ ] [CKA with Practice Tests — Mumshad/KodeKloud](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)

**Books:**
- [ ] *Kubernetes: Up & Running* — Hightower/Burns/Beda
- [ ] *Production Kubernetes* — O’Reilly

**Milestone:**
- Containerize all services; **compose + k8s manifests**; **Prometheus/Grafana** dashboards; **zero‑downtime rollout**.

---

## Month 8 — Security & Hardening
**Main (Udemy):**
- [ ] [Web Authentication with Golang — JWT, OAuth2, Crypto](https://www.udemy.com/course/oauth-authentication/)

**Alt:**
- [ ] [OAuth2/OIDC with Keycloak (hands‑on)](https://www.udemy.com/topic/oauth/)

**Books:**
- [ ] *OAuth 2 in Action* — Ruth/Wolfe
- [ ] *API Security in Action* — Neil Madden

**Milestone:**
- Harden **`authsvc-go`**: refresh rotation, **mTLS** between services, **secrets mgmt**, **gosec** scan, **per‑identity rate‑limits**.

---

## Month 9 — Authoritative Multiplayer Session (Go + WS)
**Main:**
- [ ] Reuse advanced modules of **Working with WebSockets in Go** (Month 4).

**Alt:**
- [ ] Language‑agnostic real‑time backend/WebSocket scaling course (optional).

**Books:**
- [ ] *Multiplayer Game Programming* — Glazer & Madhav
- [ ] *Game Programming Patterns* — Robert Nystrom

**Milestone:**
- Build **`gamesession-go`** (deterministic tick, basic anti‑cheat, replay logs) + **Unity** client; multi‑room scaling & crash recovery.

---

## Month 10 — Payments, IAP, Entitlements
**Main (Udemy):**
- [ ] [Stripe In Practice](https://www.udemy.com/course/stripe-course/)

**Alt:**
- [ ] [Learn Web Payment Processing with Stripe (intro)](https://www.udemy.com/course/learn-web-payment-processing-with-stripe-a-quick-intro/)

**Refs:**
- [ ] Official **Stripe** docs; **Apple/Google IAP** server‑side receipt docs
- [ ] *Microservices Patterns* — Chris Richardson (sagas/outbox)

**Milestone:**
- Build **`billing-go`** (receipt verification pipeline + entitlements) with **contract tests** & **sandbox E2E** runs.

---

## Month 11 — Resilience, Caching, SLOs & System Design
**Main (Udemy):**
- [ ] [Redis: The Complete Developer’s Guide](https://www.udemy.com/course/redis-the-complete-developers-guide-p/)
- [ ] [Software Architecture & Design of Modern Large‑Scale Systems — Michael Pogrebinsky](https://www.udemy.com/course/software-architecture-design-of-modern-large-scale-systems/)

**Alt:**
- [ ] [System Design Masterclass (2025)](https://www.udemy.com/course/system-design-masterclass/)

**Books:**
- [ ] *Site Reliability Engineering* + *SRE Workbook* — Google
- [ ] *Release It!* — Michael Nygard

**Milestone:**
- Define **SLOs**; load test to target **CCU**; autoscaling tuned; **runbook + dashboards** proving SLOs.

---

## Month 12 — Capstone & Packaging
**Main:** No new course—ship the platform.

**Capstone repo: `go-mp-platform`**
- Services: **Auth, Profile, Lobby (gRPC), GameSession (WS), Chat, Billing, Events**
- Infra: **Docker, k8s, CI**
- Docs: **ADRs, diagrams, README**, short **demo video**
- Client: Minimal **Unity** demo

---

### Notes
- “Alt (substitute)” = pick **instead** of Main if you don’t like the Main’s style. Don’t do both end‑to‑end. Cherry‑pick modules only if you have extra time.
- Books are for depth; keep shipping code each month.
