# Bazaar-Case-Study-
# 🏪 Distributed Stock Management System (AI-Enhanced & Event-Driven)

A horizontally scalable, event-driven, and AI-augmented **Distributed Stock Management System** designed to manage inventory across **thousands of retail stores** with near real-time synchronization, cache optimization, read/write separation, and automated alerting.

This project was built as a scalable microservice system that evolves through multiple phases, integrating core backend technologies like **FastAPI**, **Kafka**, **MySQL**, and **Redis**, with **AI logic** for threshold detection and future prediction.

---

## 📌 Project Summary

> **Objective:**  
To design and implement a robust inventory management system capable of handling high concurrency, providing near real-time updates, maintaining consistency, and enabling intelligent decision-making across distributed retail environments.

> **Key Highlights:**  
- Supports **thousands of stores** and products  
- Utilizes **Kafka** for async updates (event-driven architecture)  
- Redis for **low-latency reads and caching**  
- **MySQL** with **read/write separation** for database scaling  
- **AI module** to detect stock anomalies and forecast needs  
- Tracks all changes via **audit logs**  
- Built using **FastAPI** and modern Python tooling

---

## 🧱 Evolution: Phase-by-Phase Breakdown

### 🔹 Phase 1: Basic Architecture
- Simple CRUD-based stock system.
- Single MySQL DB handling all reads/writes.
- No async, no caching.

### 🔹 Phase 2: Performance Optimization
- Introduced **Redis** to cache reads and reduce DB hits.
- Added **background tasks** for better user experience.
- Reduced read/write coupling.

### 🔹 Phase 3: Scalable, Event-Driven System
- Kafka added for **asynchronous stock sync**.
- AI module integrated for **threshold alerts**.
- MySQL now uses **read/write replicas** for high concurrency.
- Full **audit logs** and **rate-limiting** support.
- Horizontally scalable, production-ready setup.

---

## 🎯 Real-World Impact

- Helps retail chains avoid **stockouts or overstocking**, saving costs.
- Ensures stock is synced **near real-time** across hundreds/thousands of branches.
- Provides **intelligent alerts** when inventory falls below defined thresholds.
- Improves customer satisfaction by ensuring **accurate stock visibility**.
- Enables scalability and fault tolerance using **microservices and event queues**.

---

## ⚙️ Tech Stack

| Layer | Technology Used |
|-------|------------------|
| API | FastAPI |
| Messaging | Kafka |
| Cache | Redis |
| Database | MySQL (with Read/Write separation) |
| Background Tasks | FastAPI BackgroundTasks |
| AI / Logic | Python (Pandas/Custom Rules) |
| Audit | SQL-based Audit Table |
| Rate Limiting | slowapi |

---

## 🧠 AI Integration

- Detects **low-stock thresholds** in real-time.
- Predicts future demand using trend analysis.
- Suggests **pre-emptive reorders** based on consumption patterns.
- Thresholds configurable per product/store.

---

## 🧰 Key Features

- 🔄 Event-driven stock updates via Kafka
- ⚡ Redis caching for high-speed reads
- 🧠 AI-based threshold alerts
- 📜 Audit logging for transparency
- 📈 Horizontal scalability
- 🔐 Rate-limited APIs to avoid abuse
- ⌛ Background tasks for async processing

---

## 🔌 API Overview

### `POST /update-stock/{store_id}/{product_id}?quantity=`
- Updates stock.
- Fires Kafka event.
- Updates Redis cache.
- Logs to audit trail.

### `GET /get-stock/{store_id}/{product_id}`
- Checks Redis → DB fallback.
- Enforced rate limit (5/sec/IP).

### `GET /audit-logs`
- Lists recent stock changes.
- Useful for monitoring & rollback analysis.

---

## 🚀 How to Run

1. **Start Kafka, Redis, and MySQL** locally.
2. Run the FastAPI app:  
```bash
uvicorn main:app --reload
