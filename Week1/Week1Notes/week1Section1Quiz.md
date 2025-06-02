Great! Let’s get into a rigorous **quiz + scenario-based discussion** based on **Week 1: Introduction to System Design**.

---

## 🔍 **Part 1: Tricky Quiz Questions**

I'll start with **5 tough conceptual questions** to assess your understanding.

### ❓ Q1:

A system is highly available but not reliable. Can you describe what this system might look like in a real-world context?
---
A highly available but unreliable system ensures the API is always accessible (e.g., 99.99% uptime) but may serve incorrect or stale data. A good example is a social media feed that loads every time (available) but may not show the latest posts (not reliable). This trade-off is often due to systems choosing eventual consistency (AP in CAP theorem) to maintain availability under network partitioning.

### ❓ Q2:

If a service is designed for 99.99% availability, what is the **maximum allowable downtime per month**? Show your calculation.
---
99.99% availability means 0.01% downtime.
Per month:
30 days * 24 * 60 = 43,200 minutes
0.01% of 43,200 = ~4.32 minutes/month

### ❓ Q3:

What design decisions would you make if you are building a **cost-effective but highly scalable notification service** for sending OTPs to users?
---
To build a cost-effective, highly scalable OTP service:

Use asynchronous message queuing (e.g., Amazon SQS) to decouple request and send logic.

Use a pub-sub system to send SMS/email via different providers (fallbacks for failures).

Use bulk providers (e.g., Twilio, SendGrid) and tiered routing to reduce cost.

Implement rate limiting, retries with exponential backoff, and DLQs for failures.

Use stateless workers to scale horizontally and handle peak loads.

### ❓ Q4:

Which system design goal is **most likely to conflict** with cost-effectiveness? Why? Give an example scenario.
---
Availability often conflicts with cost-effectiveness, because ensuring high uptime requires:

Redundant servers (multi-zone or multi-region)

Load balancers

Failover mechanisms
These add significant infrastructure cost.
E.g., a 99.999% SLA may require 3–5x the infra cost vs a 99.9% system.

### ❓ Q5:

You’re asked to design an internal admin dashboard that has **no strict latency requirements**, but has to **always show accurate, up-to-date data**. What would be the **primary system design goal** you’d focus on? How would your tech choices differ from a public-facing product page?
---
The primary goal is reliability and data consistency. Internal dashboards often need accurate, real-time data for decision-making.

I'd use strongly consistent databases (e.g., SQL, Spanner).

Possibly a polling system or event-driven architecture for near real-time updates.

Public-facing systems, in contrast, prioritize latency, caching, and denormalization to ensure snappy UX at scale.


## 🎯 **Part 2: Scenario + Functional and Non-Functional Analysis + Estimations**

Let’s start with **Scenario 1**.

---

### 📦 **Scenario 1: “Image Storage & Retrieval System (like Imgur)”**

You’ve been asked to design a system where:

* Users can upload images.
* Each image has a unique URL.
* Images can be viewed by anyone with the URL.
* The system should handle **1 million uploads per day** and **50 million image views per day**.

---

### ✍️ 1. Functional Requirements (FR):

List down **functional requirements** of this system.
---
1. User can upload images via web/mobile UI.
2. System generates a unique, immutable URL per image.
3. Any user with the URL can access the image (no auth by default).
4. System should support optional privacy/access controls (future enhancement).

### 🛠️ 2. Non-Functional Requirements (NFR):
1. The system should be scalable because we need 10^6 uploads 5*10^6 views in a day
2. Availability - System should be available to users at all times - although not a mandatory requirement
3. Reliability: System should always open the correct image with the URL although since the data is not being updated this is not a requirement
4. Performance: System should be highly performant, should not take a lot of time in upload or view
5. Mantainability: User base may increase over time, or over zones so should be easily mantainable for higher loads,to extensive geographic areas, without compromising on throughput and latency
6. System should be cost effective

----💡 Clarify why availability is important: if Imgur is down, image embeds across the internet break. So it's actually crucial.

### 📊 3. Estimation:

* Estimate the total **storage** needed per month (assuming average image size is 2MB).
Uploads in a day = 10^6 * 2 MB
Uploads in a month = 10^6 * 2 * 30 MB = 60 TB

* Estimate the **bandwidth** for reads (if average view is 200KB).
1 view = 200KB
Views in a day = 50 * 10^6
Data sent for reads in a day = 50 * 10^6 * 200 KB =  10 TB 
Bandwidth = 10PB / (24*60*60) = 115 MB per second

### ⚖️ 4. Trade-offs:

What are **two design trade-offs** you’d need to consider when designing this system?
1. Reliability
2. Mantainability

After this scenario, I’ll give you **Scenario 2: Real-time messaging system like Slack/WhatsApp** to explore latency, throughput, and consistency.
------------------------------------------------------------------------------------------------------------------------


## 🧩 **System Design Practice Scenario #2: “Log Aggregation & Search System (like ELK or Splunk)”**

### 🔍 **Context**:

You are designing a log aggregation system for a cloud infrastructure team. It should collect logs from thousands of microservices, store them efficiently, and allow querying for debugging and monitoring purposes.
---

### ✅ **Your Task:**

### ✍️ 1. Functional Requirements (FR):

* What core features does this system need?
- Ingest logs from distributed microservices in real-time.
- Store logs in a durable, queryable form.
- Support full-text search and filtering (e.g., by timestamp, service, severity).
- Provide APIs/UI for querying logs.
- Optional: Support aggregation/grouping for insights (e.g., error trends).


### 🛠️ 2. Non-Functional Requirements (NFR):

* What performance and reliability qualities should it have?
Logs must not be lost or duplicated, and should arrive in order (at least per source). This is part of eventual consistency in distributed systems.

- **High Availability**: The system must accept logs 24/7 and serve queries reliably.
- **Durability**: Logs, once written, must never be lost.
- **Scalability**: Must scale with services, log volume, and concurrent queries.
- **Query Performance**: Near-real-time logs can be delayed by a few seconds; however, historical queries should be optimized.
- **Cost Efficiency**: Use cold storage for old logs to manage costs.
- **Maintainability**: Should be modular, observable, and easy to evolve.

### 📊 3. Estimations:

Assume:

* Each service emits \~1000 log entries per minute.
* There are 2000 services.
* Each log is \~500 bytes.

Estimate:

1. Total data ingested per day.
1000 logs per minute per servie
2000 services - 2000 * 1000 logs per minute over all = 2 * 10^6 logs per minute
1 log = 500B
Total logs in a minute: 500B * 2 * 10^6 = 1GB/min
Total data ingested in a day = 1GB/min * 24*60 = 1.44 TB/day

2. Storage needed for 30 days.
1.44 TB/day * 30 = 43.2 TB/month
3. Query latency expectations.
5 minutes, idk i am giving general estimation idk how to calculate

---

### ⚖️ 4. Design Trade-offs:
1. Cost vs Performance  : Cost would win here
2. Write Throughput vs Query Latency: - To maintain high ingest speed, we may delay indexing, which slows queries.
Trade-off: Real-time analytics vs high-volume ingestion.
3. Cold Storage vs Immediate Access: Older logs may be moved to cheaper, slower storage (like S3 Glacier).
Trade-off: Cost vs Speed.
4. Consistency vs Availability: In distributed systems (e.g., multi-region), writes may be accepted before all replicas sync.
We may choose availability over strict consistency.

---

### 💭 5. Bonus:

Suggest how you'd:

* Index logs for fast querying. - Indexing: Index on timestamp, service_id, and log_level. You can also allow full-text indexing (e.g., Elasticsearch or OpenSearch).
When you get a high volume of logs every second, if you try to index every log immediately, your system might slow down.

So, some systems ingest the data first, and index later in batches, or index only partial fields to reduce load.
 Indexing Process (simplified):
Log is ingested (written to a queue or buffer).

A worker or background thread picks it up and:

Parses the log.

Extracts fields (e.g., timestamp, error type, service name).

Builds an inverted index (data structure for fast search).

That index is stored for queries later.

* Store logs in a cost-effective manner over time. - Use hot storage (SSD, Elasticsearch nodes) for recent logs (e.g., 7 days).
Archive older logs to object storage (e.g., S3) in compressed form.
Use lifecycle policies to transition to even cheaper storage (e.g., Glacier) after 30/90 days.
What is full-text indexing?
Full-text indexing means you allow users to search any word or phrase inside log messages.

🔍 Example:
A log:
2024-06-02 12:44:01 [ERROR] Payment failed due to timeout at step 3

vbnet
Copy
Edit
2024-06-02 12:44:01 [ERROR] Payment failed due to timeout at step 3
With full-text indexing, you can query:

“timeout”
“step 3”
“payment failed”
logs containing "error"

This is different from structured querying (timestamp > X AND service_id = Y).

📌 Used when:
You want flexible search like a search engine.

Useful for unstructured data like logs, emails, documents.

📦 Common Engines:
Elasticsearch

OpenSearch (AWS fork of Elasticsearch)

Apache Lucene (core library behind both)

🔥 What is "Hot Storage"?
🔥 Hot Storage:
Fast, frequently accessed data.

E.g., SSD-backed Elasticsearch nodes.

Used for recent logs (like past 7 days).

Expensive but fast.

🧊 Cold Storage:
Cheaper, slower (like S3 or Glacier).

Used for older logs (e.g., older than 30 days).

Must trade off latency for cost savings.

💡 Design Pattern:
Store logs in hot storage → index, serve fast queries.

After 7 days → move logs to cold storage → slower search, no real-time queries.

----------------------------------------------------------------------------------------------------------------------------

