# Week 1: High-Level Design (HLD) Fundamentals - Notes

This document is for your notes on the High-Level Design topics covered in Week 1.

---

## 1. Introduction to System Design

*   **What is System Design?**
    *   **Scope:** Architecting large-scale, distributed systems (components on different networked computers, coordinating via messages). Not just small features.
    *   **Examples:** Netflix, Google Search, Amazon. These are ecosystems of many services.
    *   **Importance:**
        *   **Interviews (FAANG+):** Assesses high-level thinking, trade-off analysis, ambiguity handling.
        *   **Real-world:** Daily activity for building scalable, reliable products. Poor design leads to outages, slow performance, high costs.
*   **Key Goals of System Design (Non-Functional Requirements - NFRs):**
    *   **Scalability:** Ability to handle increasing load (users, data, transactions).
        *   Vertical Scaling (Scaling Up): More resources to a single server (CPU, RAM). Limited, expensive.
        *   Horizontal Scaling (Scaling Out): Add more servers. Preferred for large systems.
        *   *Example:* Amazon scaling servers for Black Friday.
    *   **Availability:** System remains operational and accessible (uptime % like 99.9%, 99.999% - "five nines" ~5.26 min downtime/year).
        *   Achieved via redundancy (no single point of failure), failover mechanisms.
        *   *Example:* Google Search's global data centers ensuring it's rarely down.
    *   **Reliability:** System performs its intended function correctly without failure (works correctly when up).
        *   Achieved via robust error handling, fault tolerance, testing.
        *   *Example:* Banking systems accurately processing money transfers.
    *   **Performance:** Responsiveness of the system.
        *   Latency: Time for a single operation (e.g., page load time). Lower is better.
        *   Throughput: Number of operations per unit of time (e.g., requests per second). Higher is better.
        *   *Example:* Stock trading platforms needing low latency and high throughput.
    *   **Maintainability:** Ease of modifying, fixing, and extending the system.
        *   Achieved via good documentation, modularity (e.g., microservices), clean code.
        *   *Example:* Large e-commerce sites constantly adding features without breaking existing ones.
    *   **Cost-Effectiveness:** Balancing features, performance, and NFRs with operational and development costs.
        *   Involves smart choices on tech, infrastructure (cloud vs. on-premise).
        *   *Example:* Startups using serverless for MVPs to keep initial costs low.
*   **The Process of System Design:**
    *   **Requirement Gathering:**
        *   Functional Requirements: What the system *should do*. (e.g., URL shortener: shorten URL, redirect).
        *   Non-Functional Requirements (NFRs): How the system *should be* (the key goals above).
    *   **Estimation (Back-of-the-envelope):** Rough calculations for scale.
        *   Traffic: Daily Active Users (DAU), Queries Per Second (QPS).
        *   Storage: Data volume (e.g., GB/TB/PB per day/year).
        *   Bandwidth: Data transfer rates (e.g., Mbps, Gbps, Tbps).
        *   *Example:* Estimating YouTube's daily new video storage (Petabytes).
    *   **System Interface Definition (APIs):** How components/clients interact.
        *   Define endpoints, request/response formats (e.g., REST: `POST /shorten`, `GET /{short_code}`).
    *   **Data Model Design:** How data is structured, stored, accessed.
        *   Choose database type (SQL vs. NoSQL).
        *   Define tables/collections, schemas, relationships.
        *   *Example:* Twitter: `Users`, `Tweets`, `Follows` tables.
    *   **High-Level Architecture:** Block diagram of main components and their interactions.
        *   Components: Clients, Load Balancers, Web Servers, App Servers, Databases, Caches, Message Queues.
        *   *Example:* E-commerce: Browser -> LB -> Web Servers -> App Servers -> DBs & Cache.
    *   **Detailed Design:** Deep dive into specific complex components.
        *   Internal design, algorithms, specific technology choices for key services.
        *   *Example:* Twitter's timeline generation service (push vs. pull, caching).
    *   **Identifying Bottlenecks and Trade-offs:**
        *   No system is perfect; always trade-offs (e.g., CAP theorem: Consistency vs. Availability).
        *   Identify potential bottlenecks (parts that slow down/fail under load).
        *   Make conscious decisions based on requirements.
        *   *Example:* Facebook News Feed: Eventual consistency for fast load times (trade-off).

---

## 2. Core Distributed System Concepts

*   **Latency vs. Throughput:**
    *   (Your notes here)
*   **Consistency Models:**
    *   Strong Consistency: (Your notes here)
    *   Eventual Consistency: (Your notes here)
*   **Availability vs. Reliability:**
    *   (Your notes here)
*   **CAP Theorem:**
    *   Consistency: (Your notes here)
    *   Availability: (Your notes here)
    *   Partition Tolerance: (Your notes here)
    *   Trade-offs: (Your notes here)

---

## 3. Basic Building Blocks

*   **Clients:** (Your notes here)
*   **Servers:**
    *   Web Servers: (Your notes here)
    *   Application Servers: (Your notes here)
*   **Load Balancers (LBs):**
    *   Purpose: (Your notes here)
    *   Types: (Your notes here)
    *   Algorithms: (Your notes here)
*   **Databases:**
    *   **SQL (Relational Databases - RDBMS):**
        *   ACID Properties: (Your notes here)
        *   Use Cases: (Your notes here)
    *   **NoSQL (Non-Relational Databases):**
        *   BASE Properties: (Your notes here)
        *   Types (Key-Value, Document, Columnar, Graph): (Your notes here for each type)
        *   Use Cases: (Your notes here for each type)
*   **Caching:**
    *   Purpose: (Your notes here)
    *   Cache Invalidation Strategies: (Your notes here)
    *   Cache Eviction Policies: (Your notes here)
*   **Content Delivery Networks (CDNs):**
    *   Purpose: (Your notes here)
*   **Message Queues (MQs):**
    *   Purpose: (Your notes here)
    *   Key Concepts: (Your notes here)

---

## 4. API Design Basics

*   **RESTful APIs:**
    *   Principles: (Your notes here)
    *   HTTP Methods: (Your notes here)
    *   Status Codes: (Your notes here)
*   **GraphQL (Brief Overview):**
    *   (Your notes here)

---
