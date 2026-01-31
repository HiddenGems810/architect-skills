---
name: consult_system_architecture
description: High-scale backend design, database selection, API patterns, and cloud infrastructure.
---

# System Architecture & Scalability

You have access to the blueprints for building software that can scale to millions of users. Use this to make robust technical decisions.

## 1. The 12-Factor App (Modern SaaS Standard)

1.  **Codebase**: One repo, many deploys.
2.  **Dependencies**: Explicitly declare and isolate (Docker).
3.  **Config**: Store config in the environment (ENV vars), not code.
4.  **Backing Services**: Treat DBs/Queues as attached resources.
5.  **Build, Release, Run**: Strict separation of stages.
6.  **Processes**: Execute the app as one or more stateless processes.
7.  **Port Binding**: Export services via port binding.
8.  **Concurrency**: Scale out via the process model (horizontal scaling).
9.  **Disposability**: Fast startup and graceful shutdown.
10. **Dev/Prod Parity**: Keep development, staging, and production similar.
11. **Logs**: Treat logs as event streams.
12. **Admin Processes**: Run admin/management tasks as one-off processes.

## 2. Database Strategy

### CAP Theorem
*   **Consistency**: Every read receives the most recent write.
*   **Availability**: Every request receives a (non-error) response.
*   **Partition Tolerance**: The system continues to operate despite network message drops.
*   **Reality**: In a distributed system (Partition Tolerance is mandatory), you must choose between Consistency (CP) and Availability (AP).

### SQL vs NoSQL
*   **SQL (Postgres, MySQL)**: Use for relational data, financing, complex queries, strict schemas. ACID compliance.
*   **NoSQL (MongoDB, DynamoDB)**: Use for unstructured data, massive write throughput, flexible schemas. Base/Eventual consistency.
*   **Caching (Redis)**: Mandatory layer for speed. Cache expensive queries.

## 3. API Architecture

### REST
*   **Pros**: Standard, cacheable, simple.
*   **Cons**: Over-fetching/Under-fetching data.

### GraphQL
*   **Pros**: Client asks for exactly what it needs. Great for complex frontends.
*   **Cons**: Complexity in caching, N+1 query problems.

### RPC (tRPC / gRPC)
*   **Pros**: Type-safety across the boundary. High performance.
*   **Use Case**: Internal microservices (gRPC) or Monorepo Fullstack (tRPC).

## 4. Scalability Patterns

### Horizontal vs Vertical
*   **Vertical**: Bigger machine (CPU/RAM). Easy but hits a ceiling.
*   **Horizontal**: More machines. Infinite scale but requires stateless architecture.

### Load Balancing
*   **Layer 4 (Transport)**: Fast, creates connection based on IP/Port.
*   **Layer 7 (Application)**: Smart, can route based on URL path, cookies, headers.

### Asynchronous Processing
*   **Pattern**: Don't block the web request. Offload heavy tasks (Email, Video processing, AI generation) to a **Job Queue** (BullMQ, SQS). return `202 Accepted` immediately.

## 5. Security Essentials

*   **Principle of Least Privilege**: Give services only the permissions they need.
*   **OWASP Top 10**: Protect against Injection, Broken Auth, XSS.
*   **Sanitization**: Never trust user input. Validate schema (Zod) at the boundary.
