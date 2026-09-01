This project is a proof-of-concept (PoC) of a highly scalable, event-driven payment simulation system (inspired by the Brazilian Pix). It is designed to showcase modern software architecture practices for the financial sector, focusing on resilience, consistency, and asynchronous communication.

The system operates on a Kubernetes cluster and is composed of distinct microservices built with .NET 8. It tackles common distributed systems challenges such as double-charging, database locking, and dual-write issues by implementing industry-standard patterns.

# Key Features & Patterns
- Event-Driven Architecture (EDA): Asynchronous communication between microservices using RabbitMQ and MassTransit.
- Transactional Outbox Pattern: Guarantees atomic writes between the relational database (SQL Server) and the message broker to prevent dual-write anomalies.
- Idempotency & Velocity Checks: Leverages Redis/Valkey at the edge to prevent duplicate payment requests and block fraudulent spikes in real-time.
- Polyglot Persistence: Each microservice owns its data, utilizing the best tool for the job (SQL Server for ACID transactions, Redis for caching/locking, and DynamoDB/PostgreSQL for ledger history).
- Cloud-Native & Edge Routing: Containerized workloads orchestrated by Kubernetes (K3s) with edge routing and rate-limiting handled by the NGINX Ingress Controller.
