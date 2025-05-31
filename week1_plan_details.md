# Week 1: Fundamentals & Core Concepts - Detailed Plan

**Goal:** Build a strong understanding of the basic building blocks and principles for both High-Level Design (HLD) and Low-Level Design (LLD).

---

## High-Level Design (HLD) Topics:

### 1. Introduction to System Design
*   **What is System Design?**
    *   Understanding the scope: Designing large-scale, distributed systems.
    *   Importance in software engineering interviews and real-world applications.
*   **Key Goals of System Design:**
    *   **Scalability:** Ability to handle increasing load (users, data, transactions).
    *   **Availability:** System remains operational and accessible. (e.g., 99.9%, 99.99% uptime).
    *   **Reliability:** System performs its intended function correctly without failure.
    *   **Performance:** Responsiveness of the system (latency, throughput).
    *   **Maintainability:** Ease of modifying, fixing, and extending the system.
    *   **Cost-Effectiveness:** Balancing features and performance with operational and development costs.
*   **The Process of System Design:**
    *   **Requirement Gathering:** Functional and Non-Functional Requirements (NFRs).
    *   **Estimation:** Traffic, storage, bandwidth.
    *   **System Interface Definition:** APIs.
    *   **Data Model Design:** Database schema, data flow.
    *   **High-Level Architecture:** Components and their interactions.
    *   **Detailed Design:** Deep dive into specific components.
    *   **Identifying Bottlenecks and Trade-offs:** Making informed design decisions.

### 2. Core Distributed System Concepts
*   **Latency vs. Throughput:**
    *   Latency: Time taken for a single operation.
    *   Throughput: Number of operations per unit of time.
    *   Understanding the trade-offs and how to optimize for each.
*   **Consistency Models:**
    *   **Strong Consistency:** All reads see the latest write.
    *   **Eventual Consistency:** Reads might see stale data for a period, but eventually, all replicas converge.
    *   Other models (e.g., Read-your-writes, Monotonic reads).
*   **Availability vs. Reliability:**
    *   Availability: Is the system up and running?
    *   Reliability: Does the system work correctly when it's up?
*   **CAP Theorem:**
    *   **Consistency:** All nodes see the same data at the same time.
    *   **Availability:** Every request receives a (non-error) response – without the guarantee that it contains the most recent write.
    *   **Partition Tolerance:** The system continues to operate despite network partitions.
    *   Understanding that in a distributed system, you must choose between C and A when P occurs.

### 3. Basic Building Blocks
*   **Clients:** Web browsers, mobile apps, other services.
*   **Servers:**
    *   **Web Servers:** (e.g., Nginx, Apache) - Handle HTTP requests, serve static content.
    *   **Application Servers:** (e.g., Tomcat, Node.js backend) - Host business logic.
*   **Load Balancers (LBs):**
    *   Purpose: Distribute traffic across multiple servers, improve availability and scalability.
    *   Types: L4 (Network) vs. L7 (Application).
    *   Algorithms: Round Robin, Least Connections, Weighted Round Robin, IP Hash.
    *   Sticky sessions.
*   **Databases:**
    *   **SQL (Relational Databases - RDBMS):**
        *   Examples: MySQL, PostgreSQL, Oracle.
        *   Structure: Tables, rows, columns, schemas.
        *   ACID Properties: Atomicity, Consistency, Isolation, Durability.
        *   Use Cases: Structured data, transactions, strong consistency requirements.
    *   **NoSQL (Non-Relational Databases):**
        *   Purpose: Handle large volumes of unstructured/semi-structured data, high throughput, scalability.
        *   BASE Properties: Basically Available, Soft state, Eventual consistency.
        *   Types:
            *   **Key-Value Stores:** (e.g., Redis, Memcached) - Simple key-value pairs.
            *   **Document Databases:** (e.g., MongoDB, Couchbase) - Store data in document format (JSON, BSON, XML).
            *   **Columnar Databases:** (e.g., Cassandra, HBase) - Store data in columns rather than rows, good for analytical queries.
            *   **Graph Databases:** (e.g., Neo4j, Amazon Neptune) - Store data as nodes and relationships, good for connected data.
        *   Use Cases: Vary by type - caching, user profiles, product catalogs, real-time analytics, social networks.
*   **Caching:**
    *   Purpose: Reduce latency, decrease load on backend systems.
    *   Benefits: Improved performance, reduced database cost.
    *   Cache Invalidation Strategies: Write-through, Write-around, Write-back, Cache-aside.
    *   Cache Eviction Policies: LRU (Least Recently Used), LFU (Least Frequently Used), FIFO (First-In, First-Out).
    *   Levels of Caching: Client-side, CDN, Server-side (In-memory, Distributed).
*   **Content Delivery Networks (CDNs):**
    *   Purpose: Distribute static content (images, videos, JS, CSS) geographically closer to users.
    *   Benefits: Reduced latency, lower server load, improved global availability.
*   **Message Queues (MQs):**
    *   Examples: RabbitMQ, Kafka, Amazon SQS.
    *   Purpose: Decouple services, enable asynchronous communication, buffer requests, handle load spikes.
    *   Key Concepts: Producer, Consumer, Queue, Topic, Broker.

### 4. API Design Basics
*   **RESTful APIs (Representational State Transfer):**
    *   Principles: Statelessness, Client-Server, Cacheable, Uniform Interface, Layered System.
    *   HTTP Methods: GET, POST, PUT, DELETE, PATCH.
    *   Status Codes: 2xx (Success), 3xx (Redirection), 4xx (Client Error), 5xx (Server Error).
    *   Resource Naming Conventions.
*   **GraphQL (Brief Overview):**
    *   Query language for APIs.
    *   Allows clients to request only the data they need.
    *   Single endpoint.

---

## Low-Level Design (LLD) Topics:

### 1. Object-Oriented Design (OOD) Principles
*   **SOLID Principles:**
    *   **S - Single Responsibility Principle (SRP):** A class should have only one reason to change.
    *   **O - Open/Closed Principle (OCP):** Software entities (classes, modules, functions) should be open for extension but closed for modification.
    *   **L - Liskov Substitution Principle (LSP):** Subtypes must be substitutable for their base types.
    *   **I - Interface Segregation Principle (ISP):** Clients should not be forced to depend on interfaces they do not use.
    *   **D - Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.
*   **Other Key Principles:**
    *   **DRY (Don't Repeat Yourself):** Avoid duplication of code.
    *   **KISS (Keep It Simple, Stupid):** Simplicity is a key goal.
    *   **YAGNI (You Ain't Gonna Need It):** Don't add functionality until it's necessary.
    *   **Composition over Inheritance:** Favor composing objects over extending classes.
    *   **Law of Demeter (Principle of Least Knowledge):** A module should not know about the innards of objects it manipulates.

### 2. Core Design Patterns (Gang of Four - GoF)
*   Focus on understanding the *problem* each pattern solves, its *structure* (classes and interactions), and its *consequences* (trade-offs).
*   **Creational Patterns:** Concerned with object creation mechanisms.
    *   **Singleton:** Ensure a class only has one instance and provide a global point of access to it.
    *   **Factory Method:** Define an interface for creating an object, but let subclasses decide which class to instantiate.
    *   **Abstract Factory:** Provide an interface for creating families of related or dependent objects without specifying their concrete classes.
    *   **Builder:** Separate the construction of a complex object from its representation so that the same construction process can create different representations.
*   **Structural Patterns:** Concerned with how classes and objects are composed to form larger structures.
    *   **Adapter:** Convert the interface of a class into another interface clients expect.
    *   **Decorator:** Attach additional responsibilities to an object dynamically.
    *   **Facade:** Provide a unified interface to a set of interfaces in a subsystem.
    *   **Proxy:** Provide a surrogate or placeholder for another object to control access to it.
*   **Behavioral Patterns:** Concerned with algorithms and the assignment of responsibilities between objects.
    *   **Observer:** Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
    *   **Strategy:** Define a family of algorithms, encapsulate each one, and make them interchangeable.
    *   **Template Method:** Define the skeleton of an algorithm in an operation, deferring some steps to subclasses.
    *   **Command:** Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.

### 3. UML Diagrams (Basics)
*   Purpose: Visualize, specify, construct, and document the artifacts of a software-intensive system.
*   **Use Case Diagrams:** Describe what a system does from the standpoint of an external observer. Emphasizes *what* a system does rather than *how*.
*   **Class Diagrams:** Describe the structure of a system by showing the system's classes, their attributes, operations (or methods), and the relationships among objects.
*   **Sequence Diagrams:** Show how objects interact with each other and the order in which these interactions occur. Focuses on the time ordering of messages.

### 4. Data Structures & Algorithms (DSA) in LLD
*   Understanding how the choice of data structures (e.g., List, Map, Set, Tree, Graph) for class attributes impacts the efficiency (time and space complexity) of methods.
*   How algorithmic choices within methods affect performance and maintainability.

---

## Week 1 - Problems to Solve:

*   **High-Level Design (HLD):**
    1.  **Design a URL Shortener (e.g., TinyURL):**
        *   Functional Requirements: Shorten URL, Redirect to original URL, Custom URLs (optional).
        *   Non-Functional Requirements: High availability, Low latency, Scalability.
        *   Estimate traffic, storage.
        *   Define APIs.
        *   High-level architecture diagram.
    2.  **Design a Pastebin-like service:**
        *   Functional Requirements: Create paste, View paste, Set expiration (optional), User accounts (optional).
        *   Non-Functional Requirements: High availability, Durability of pastes, Scalability.
        *   Estimate traffic, storage.
        *   Define APIs.
        *   High-level architecture diagram.

*   **Low-Level Design (LLD):**
    1.  **Design a Parking Lot system:**
        *   Classes: `ParkingLot`, `Level`, `Spot` (and types like `CompactSpot`, `LargeSpot`), `Vehicle` (and types), `Ticket`, `DisplayBoard`.
        *   Functionality: Park vehicle, Unpark vehicle, Find spot, Calculate fee.
        *   Consider different vehicle types and spot sizes.
    2.  **Design a Library Management System:**
        *   Classes: `Library`, `Book` (and `BookItem`), `Member`, `Librarian`, `Account`, `Fine`.
        *   Functionality: Search book, Issue book, Return book, Manage members, Calculate fines.
    3.  **Design a Vending Machine:**
        *   Classes: `VendingMachine`, `Item`, `Inventory`, `Coin`, `State` (e.g., `NoCoinState`, `HasCoinState`, `SoldOutState`).
        *   Functionality: Select item, Insert coin, Dispense item, Return change.
        *   Consider using the State design pattern.

---
**Next Steps:**
*   Study the HLD topics.
*   Study the LLD topics.
*   Attempt the HLD problems, focusing on diagrams and trade-off discussions.
*   Attempt the LLD problems, focusing on class diagrams, method signatures, and applying OOD/Patterns.
*   Create solution files in `problem_solutions/week1/`.
