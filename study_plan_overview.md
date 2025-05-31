# System Design Interview Preparation: 3-Week Plan

**Overall Approach:**
*   **Daily Study:** Dedicate a consistent amount of time each day.
*   **Active Learning:** Don't just read. Draw diagrams for HLD, write pseudo-code or actual class structures for LLD.
*   **Problem Solving:** Tackle at least one HLD and one LLD problem every few days.
*   **Iterate:** Review your designs. What could be improved? What are the trade-offs?
*   **Mock Interviews:** If possible, do mock interviews, especially in the final week.

---

## Week 1: Fundamentals & Core Concepts

**Goal:** Build a strong understanding of the basic building blocks and principles for both HLD and LLD.

**Topics & Concepts:**

*   **High-Level Design (HLD):**
    *   **Introduction to System Design:**
        *   What is it? Why is it important?
        *   Goals: Scalability, Availability, Reliability, Performance, Maintainability, Cost-effectiveness.
        *   Gathering requirements and identifying constraints.
    *   **Core Distributed System Concepts:**
        *   Latency vs. Throughput.
        *   Consistency models (strong, eventual).
        *   Availability vs. Reliability.
        *   CAP Theorem (Consistency, Availability, Partition Tolerance).
    *   **Basic Building Blocks:**
        *   Clients, Servers (Web Servers, Application Servers).
        *   Load Balancers (Round Robin, Least Connections, etc.).
        *   Databases:
            *   SQL (Relational): ACID properties, use cases.
            *   NoSQL (Non-Relational): BASE properties, types (Key-Value, Document, Columnar, Graph), use cases.
        *   Caching: Purpose, benefits, cache invalidation, common strategies (e.g., Cache-Aside).
        *   Content Delivery Networks (CDNs).
        *   Message Queues: Purpose (decoupling, asynchronous processing).
    *   **API Design Basics:**
        *   RESTful APIs: Principles, HTTP methods, status codes.
        *   Brief overview of GraphQL.

*   **Low-Level Design (LLD):**
    *   **Object-Oriented Design (OOD) Principles:**
        *   SOLID: Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion.
        *   DRY (Don't Repeat Yourself), KISS (Keep It Simple, Stupid), YAGNI (You Ain't Gonna Need It).
    *   **Core Design Patterns (Gang of Four):**
        *   Creational: Singleton, Factory Method, Abstract Factory, Builder.
        *   Structural: Adapter, Decorator, Facade, Proxy.
        *   Behavioral: Observer, Strategy, Template Method, Command.
        *   (Focus on understanding the problem they solve and their structure).
    *   **UML Diagrams (Basics):**
        *   Use Case Diagrams.
        *   Class Diagrams.
        *   Sequence Diagrams.
    *   **Data Structures & Algorithms in LLD:** How choices impact class design and efficiency.

**Problems to Solve:**

*   **HLD:**
    1.  Design a URL Shortener (e.g., TinyURL).
    2.  Design a Pastebin-like service.
*   **LLD:**
    1.  Design a Parking Lot system.
    2.  Design a Library Management System.
    3.  Design a Vending Machine.

**Markdown Files to Create:**
*   `week1_plan_details.md`
*   `hld_fundamentals.md` (covering HLD topics)
*   `lld_ood_patterns.md` (covering LLD topics)
*   `problem_solutions/week1/` (folder for your solutions)

---

## Week 2: Scaling, Advanced HLD, and LLD in Practice

**Goal:** Dive deeper into scaling systems, explore advanced HLD components, and apply LLD principles to more complex scenarios.

**Topics & Concepts:**

*   **High-Level Design (HLD):**
    *   **Scaling Strategies:**
        *   Vertical vs. Horizontal Scaling.
        *   Sharding/Data Partitioning: Techniques, challenges (hotspots, re-sharding).
        *   Replication: Master-Slave, Master-Master.
    *   **Databases In-Depth:**
        *   Choosing the right database: Trade-offs.
        *   Database indexing, query optimization.
    *   **Advanced Caching:**
        *   Cache eviction policies (LRU, LFU, FIFO).
        *   Caching strategies: Read-through, Write-through, Write-back, Write-around.
        *   Distributed Caching (e.g., Redis, Memcached).
    *   **Message Queues In-Depth:**
        *   Use cases: Rate limiting, task queues, fan-out.
        *   Comparison (e.g., Kafka vs. RabbitMQ basics).
    *   **Designing for Fault Tolerance & Resilience:**
        *   Redundancy, failover mechanisms.
        *   Circuit Breaker pattern.
    *   **Monitoring, Logging, and Alerting.**
    *   **Communication Protocols:** TCP/IP, HTTP, RPC.

*   **Low-Level Design (LLD):**
    *   **Applying Design Patterns:** Combining patterns, choosing appropriate patterns for specific problems.
    *   **API Design - Advanced:**
        *   Versioning strategies.
        *   Idempotency.
        *   Error handling and robust API responses.
    *   **Code Modularity & Reusability:** Designing for maintainable and extensible code.
    *   **Testability in LLD:** Designing classes and modules that are easy to test (Dependency Injection).
    *   **Concurrency Basics (Conceptual):** Threads, locks, race conditions (awareness for LLD).

**Problems to Solve:**

*   **HLD:**
    1.  Design a Social Media Feed (e.g., Twitter, Instagram).
    2.  Design a Ride-Sharing App (e.g., Uber, Lyft).
    3.  Design a Web Crawler.
*   **LLD:**
    1.  Design an Online Shopping System (focus on product, cart, order, payment).
    2.  Design a Movie Ticket Booking System.
    3.  Design a Blackjack (or other card game) system.

**Markdown Files to Create:**
*   `week2_plan_details.md`
*   `hld_scaling_advanced_components.md`
*   `lld_apis_testability.md`
*   `problem_solutions/week2/`

---

## Week 3: Real-World Systems, LLD Case Studies & Interview Polish

**Goal:** Analyze real-world systems, tackle complex LLD case studies, and focus on interview communication and strategy.

**Topics & Concepts:**

*   **High-Level Design (HLD):**
    *   **Case Studies of Popular Systems:**
        *   Analyze architectures of systems like Netflix, Google Search, Amazon, WhatsApp, YouTube.
        *   Focus on key design choices and trade-offs.
    *   **Designing Data-Intensive Applications.**
    *   **Security Considerations in System Design:** Common threats and mitigation techniques.
    *   **System Design Interview Frameworks:**
        *   E.g., PEDALS (Process, Estimate, Design, Articulate, Learn, Summarize) or similar structured approaches.
        *   How to clarify requirements, make assumptions, discuss trade-offs, and present your solution.
    *   **Back-of-the-envelope estimations.**

*   **Low-Level Design (LLD):**
    *   **LLD for Components of Larger Systems:**
        *   E.g., LLD of a notification service, a payment processing module, a user authentication module.
    *   **Refactoring & Code Smells:** Identifying and addressing common LLD issues.
    *   **Concurrency and Multithreading in LLD (Practical Aspects):** Designing thread-safe classes, synchronization primitives. (This might be more relevant for SDE2 roles with specific concurrency needs).
    *   **LLD Interview Strategy:**
        *   Clearly defining classes, interfaces, enums.
        *   Explaining relationships (inheritance, composition, aggregation).
        *   Defining method signatures and responsibilities.
        *   Discussing design choices and alternatives.

**Problems to Solve:**

*   **HLD:**
    1.  Design a Distributed Key-Value Store (like DynamoDB or Cassandra).
    2.  Design a Video Streaming Service (like YouTube or Netflix).
    3.  Design a Stock Trading System.
*   **LLD:**
    1.  Design a Chess Game (AI not required, focus on game logic and pieces).
    2.  Design an ATM System.
    3.  Design a Splitwise-like expense sharing application.
*   **Combined:**
    *   Pick a HLD problem and then do a deep dive into the LLD of one of its key components.

**Markdown Files to Create:**
*   `week3_plan_details.md`
*   `hld_case_studies_interview_prep.md`
*   `lld_complex_scenarios_interview_prep.md`
*   `interview_frameworks_tips.md`
*   `problem_solutions/week3/`

---

**General Resources (to supplement):**
*   "System Design Interview – An Insider's Guide" by Alex Xu (Volumes 1 & 2).
*   "Designing Data-Intensive Applications" by Martin Kleppmann.
*   "Clean Code" and "Clean Architecture" by Robert C. Martin.
*   Online resources: Gaurav Sen's System Design playlist, System Design Primer on GitHub, Grokking the System Design Interview course, various tech blogs from companies like Netflix, Uber, Google.
