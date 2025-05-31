# Week 1: High-Level Design (HLD) Fundamentals - Notes

This document is for your notes on the High-Level Design topics covered in Week 1.

---

## 1. Introduction to System Design

*   **What is System Design?**
    *   Architecting large-scale, distributed systems (e.g., Netflix, Google).
    *   Components on networked computers coordinating via messages.
    *   Crucial for interviews (FAANG) & real-world scalable, reliable products.
*   **Key Goals of System Design:**
    *   Scalability: Handle increasing load (users, data). Vertical (up) vs. Horizontal (out - preferred). Ex: Amazon on Black Friday.
    *   Availability: System operational & accessible (uptime %, e.g., 99.999%). Achieved via redundancy, failover. Ex: Google Search.
    *   Reliability: System performs intended function correctly. Achieved via error handling, fault tolerance. Ex: Banking transactions.
    *   Performance: Responsiveness. Latency (delay for one op) & Throughput (ops per time unit). Ex: Stock trading platforms.
    *   Maintainability: Ease of modification, fixing, extending. Achieved via modularity, clean code. Ex: E-commerce sites adding features.
    *   Cost-Effectiveness: Balance features/performance with development/operational costs. Ex: MVP startups using serverless.
*   **The Process of System Design:**
    *   Requirement Gathering: Functional (what it does) & Non-Functional (how it should be - scalability, perf, etc.).
    *   Estimation: "Back-of-the-envelope" for traffic (DAU, QPS), storage, bandwidth.
    *   System Interface Definition: APIs (e.g., REST, GraphQL) defining interactions.
    *   Data Model Design: Data structure, storage (SQL/NoSQL), schema, relationships.
    *   High-Level Architecture: Block diagram of main components (clients, LBs, servers, DBs, caches, MQs) & connections.
    *   Detailed Design: Deeper dive into specific complex components, algorithms, tech choices.
    *   Identifying Bottlenecks and Trade-offs: No perfect system; make informed decisions (e.g., consistency vs. availability).

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
