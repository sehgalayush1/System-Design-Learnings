Absolutely! Here's a **condensed notes version** of everything I explained above, along with the **new concepts you asked** about—consistency in DBs, polling vs event-driven, and normalization.

---

## 🔖 **Cheat Sheet / Notes**

### 1. **Asynchronous Message Queuing**

* **What:** Decouple producer and consumer using a queue. Instead of doing everything right now, the system puts the work in a queue (like a todo list). Then another part of the system (called a "worker") picks it up later and does the job.
* **Example:** AWS SQS, RabbitMQ, Apache Kafka
* **Why:** Improves scalability and reliability.

### 2. **Pub-Sub Architecture**

* **What:** One service publishes a message, many services subscribe to act on it. Each acts on the same message independently. If one fails, others are unaffected.
* **Example:** SNS, Kafka.
* **Why:** Allows multiple systems to react independently to the same event.
🖥️ In system design:
OTP service publishes: "Send this OTP to +91xxxx".
Different subscribers might be:
Email sender service
SMS sender service
Logging system
Analytics tracker

### 3. **Tiered Routing with Bulk Providers**

* **What:** Use cheaper or fallback SMS/Email providers based on rules. Route messages to different vendors based on cost, performance, or region.
* **Why:** Cost-effective and resilient.
* **Example:** Try MSG91, fallback to Twilio if MSG91 fails.


### 4. **Rate Limiting**

* **What:** Limit number of requests per user/time period.
* **Why:** Prevent abuse, protect services.

### 5. **Retries with Exponential Backoff**

* **What:** Retry failed actions after increasing delays.
* **Why:** Avoids retry storms and allows system recovery.
* **Example Delays:** 1s → 2s → 4s → 8s.

### 6. **DLQ (Dead Letter Queue)**

* **What:** Separate queue for messages that repeatedly fail.
* **Why:** Prevents system from being stuck on bad data.

### 7. **Stateless Workers**

* **What:** Workers that don’t store state across jobs.
* **Why:** Easy to scale horizontally.
* **Example:** Lambda functions picking OTP jobs from SQS.

### 8. **Failover Mechanism**

* **What:** Backup systems that take over on failure to ensure availability.
* **Why:** Ensure availability.
* **Example:** Use load balancers, health checks, and multi-region deployments.

---

## 🧠 **What is a Consistent Database?**

### ✅ **Definition:**

A **consistent database** ensures **strong data correctness** — the data you read is always **up-to-date** and reflects the latest committed write.

### 🧱 Examples:

* **Strongly Consistent:**

  * **PostgreSQL**, **MySQL**, **Oracle**, **MongoDB (w/ write concern: majority)**.
* **Eventually Consistent (by default):**

  * **DynamoDB**, **Cassandra**, **Redis (clustered)**, **S3**

### 🧮 **How are they consistent?**

* Use **ACID Transactions** (Atomicity, Consistency, Isolation, Durability).
* Use **write-ahead logs**, **replication logs**, and **quorum acknowledgments**.

### 🔍 How to know?

* Look at documentation → look for terms like:

  * **“strong consistency”**, **“eventual consistency”**
  * **“replication guarantees”**, **“read-your-write”**.

---

## 🔄 **Polling vs Event-Driven Architecture**

### 🕰️ 1. **Polling**

| Aspect      | Explanation                                        |
| ----------- | -------------------------------------------------- |
| What        | System repeatedly checks if something has changed. |
| Example     | Every 10s, check DB for new OTPs to send.          |
| When to use | Simple use cases, where real-time is not critical. |
| Drawback    | Wastes resources; introduces delay.                |

### 🔔 2. **Event-Driven**

| Aspect      | Explanation                                               |
| ----------- | --------------------------------------------------------- |
| What        | System reacts **immediately** to events.                  |
| Example     | A message added to a queue triggers a Lambda to send OTP. |
| When to use | Real-time, scalable systems.                              |
| Benefit     | Efficient, decoupled, fast.                               |

### 🧠 Rule of Thumb:

> “Use **polling** for simplicity and low-frequency tasks. Use **event-driven** for real-time systems with unpredictable loads.”

---

## 🧱 **Database Normalization**

### ✅ **What is it?**

A technique to **organize DB tables to reduce redundancy** and improve **data integrity**.

### 📚 Common Normal Forms:

1. **1NF**: No repeating groups or arrays in a row.
2. **2NF**: Every non-key column depends on **the full primary key**.
3. **3NF**: No **transitive dependencies** — i.e., data depends only on primary key.

### 🔄 Denormalization:

* Combine tables for **faster reads** in read-heavy systems.
* Common in data warehouses, caching systems.

---

## 📌 Summary Table

| Concept             | Key Idea                        | When to Use                   |
| ------------------- | ------------------------------- | ----------------------------- |
| Async Queues        | Decouple producer/consumer      | Notification systems, retries |
| Pub-Sub             | Broadcast messages to many subs | Analytics, email + SMS        |
| Bulk Providers      | Fallbacks to reduce cost/risk   | OTP, email systems            |
| Rate Limiting       | Throttle users                  | Prevent spam, API safety      |
| Exponential Backoff | Retry smarter                   | Handle transient failures     |
| DLQ                 | Handle failed jobs              | Debugging                     |
| Stateless Workers   | Easy to scale                   | OTP, batch jobs               |
| Failover            | Backup services                 | High availability             |
| Consistent DBs      | ACID guarantees                 | Banking, Orders               |
| Polling             | Repeated checking               | Simple, low urgency tasks     |
| Event-Driven        | Reactive to change              | Real-time, high-scale         |
| Normalization       | Reduce redundancy               | OLTP systems, business logic  |

---

Let me know if you want:

* A diagram showing event-driven OTP delivery?
* A mock system design with normalization vs denormalization?
* Or a **scenario to apply these ideas (FR/NFR + estimation)** as next step?
