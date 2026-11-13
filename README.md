# EthioPermit: A Fault-Tolerant Distributed One-Stop Business Permit and Tax-Clearance Platform

**Domain Pair:** A3 – One-Stop Service Portal and Permit Workflow + A9 – Tax and Customs Declarations

---

## Project Overview

**EthioPermit** is a distributed platform designed to simulate the coordination of business-permit applications across independent government agencies. It provides a unified interface through which applicants can submit applications, track their progress, satisfy simulated tax-clearance requirements, and receive electronic permits.

The platform consists of **three independently deployable domain microservices**:
* **Application and Workflow Service**
* **Agency Integration Service**
* **Tax Assessment and Clearance Service**

Each service maintains its own database and communicates with the other services through versioned REST APIs and asynchronous events.

---

## Problem Statement

Multi-agency administrative workflows involve independently operated institutions with separate data ownership, processing requirements, and service availability. A delay or failure in one institution can interrupt the overall application process, while duplicate messages, repeated requests, and partial transaction failures can produce inconsistent application states.

EthioPermit investigates how distributed-system techniques can coordinate these workflows while preserving data ownership, transaction correctness, security, and availability.

---

## Primary Research and Engineering Question

> How can a distributed one-stop government permit platform coordinate independent licensing and tax-assessment services while maintaining consistent workflow states, recovering from partial failures, and achieving acceptable performance under concurrent workloads?

---

## Core Technical Contributions

* **Microservices Architecture:** Independent microservices with database-per-service ownership.
* **Security & Gateway:** API gateway and OAuth 2.0 / OpenID Connect authentication.
* **Infrastructure & Configuration:** Service discovery and externalized configuration.
* **Asynchronous Messaging:** Event-driven communication using RabbitMQ.
* **Distributed Transactions:** Saga orchestration and compensating transactions.
* **Data Reliability:** Transactional outbox and idempotent event consumption.
* **Interoperability:** Legacy CSV integration.
* **Resilience:** Circuit breakers, retries, timeouts, and fault recovery.
* **Observability:** Centralized monitoring, metrics, and distributed correlation IDs.
* **Validation:** Controlled load, fault-injection, and security experiments.

---

## Evaluation

* **Mandatory Benchmarks:** The system will be evaluated through the seven mandatory experiments specified in the *Advanced Distributed Systems Project Manual*, covering:
  * Load performance
  * Horizontal scaling
  * Synchronous versus asynchronous processing
  * Circuit breakers
  * Fault injection
  * Idempotency
  * Security
* **Saga Experiment:** An additional saga-compensation experiment will evaluate workflow correctness under partial transaction failure.
* **Environment:** All experiments will use synthetic data and simulated external agencies.

---

## Expected Outcome

A reproducible, containerized distributed platform demonstrating how independent institutional services can cooperate through reliable communication, coordinated workflows, and fault-tolerant transaction processing. The project will be accompanied by:
* Architecture documentation
* API and event contracts
* Automated tests
* Raw experimental measurements
* A technical evaluation
