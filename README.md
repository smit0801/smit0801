# Hello there, I'm Smit Mhatre! 👋

**Master's in Computer Science @ Stevens Institute of Technology (Dec 2025)** 📍 *Hoboken, NJ / NYC Area*

I'm a software engineer focused on **Distributed Systems**, **High-Performance Backend Infrastructure**, and **Scalable Data Pipelines**. I like engineering systems that hold up under concurrency, prove their numbers with load tests, and don't fall over when the load doubles.

---

## 🛠️ Technical Stack

| Category | Technologies |
|----------|--------------|
| **Languages** | ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white) ![Go](https://img.shields.io/badge/-Go-00ADD8?style=flat&logo=go&logoColor=white) ![C++](https://img.shields.io/badge/-C%2B%2B-00599C?style=flat&logo=c%2B%2B&logoColor=white) ![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) ![SQL](https://img.shields.io/badge/-SQL-4479A1?style=flat&logo=postgresql&logoColor=white) |
| **Backend & Systems** | ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat&logo=fastapi&logoColor=white) ![gRPC](https://img.shields.io/badge/-gRPC-255F85?style=flat&logo=grpc&logoColor=white) ![Redis](https://img.shields.io/badge/-Redis-DC382D?style=flat&logo=redis&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white) ![WebSockets](https://img.shields.io/badge/-WebSockets-000000?style=flat) |
| **Streaming & Messaging** | ![Kafka](https://img.shields.io/badge/-Kafka-231F20?style=flat&logo=apachekafka&logoColor=white) ![Redpanda](https://img.shields.io/badge/-Redpanda-E63946?style=flat) |
| **Infrastructure** | ![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/-Nginx-009639?style=flat&logo=nginx&logoColor=white) ![AWS](https://img.shields.io/badge/-AWS-232F3E?style=flat&logo=amazon-aws&logoColor=white) ![Linux](https://img.shields.io/badge/-Linux-FCC624?style=flat&logo=linux&logoColor=black) |
| **Observability & Load Testing** | ![Prometheus](https://img.shields.io/badge/-Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/-Grafana-F46800?style=flat&logo=grafana&logoColor=white) ![k6](https://img.shields.io/badge/-k6-7D64FF?style=flat&logo=k6&logoColor=white) |

---

## 🚀 Featured Engineering Projects

### 1. [Distributed Task Queue](https://github.com/smit0801/<REPO-NAME>) &nbsp; 
*A distributed job queue in Go with at-least-once delivery, retries, and horizontal worker scaling.*

* **Stack:** Go, Redis, Docker, Prometheus.
* **Key Challenge:** Guaranteeing zero job loss on worker crashes while sustaining high throughput across a dynamic worker pool.
* **Engineering Wins:**
    * 🚀 Sustained **10,000 jobs/sec across 4 worker nodes**; validated horizontal scaling to **16 workers**.
    * 🔁 At-least-once delivery with **exponential-backoff retries**, **idempotency keys**, and a **dead-letter queue** with configurable visibility timeouts — graceful recovery on worker restart.
    * 🎯 Priority queues over Redis primitives, coordinated across goroutine worker pools.
    * 📊 Full **Prometheus** instrumentation: queue depth, worker utilization, retry rate, end-to-end latency.

### 2. [Fraud Radar — Real-Time Fraud Detection Pipeline](https://github.com/smit0801/fraud-radar)
*A streaming fraud detection pipeline (Stripe Radar–inspired) using unsupervised anomaly detection on 284K real credit card transactions.*

* **Stack:** Python, FastAPI, scikit-learn (Isolation Forest), Kafka (KRaft, single-node), Docker Compose.
* **Key Challenge:** Extreme class imbalance (0.17% fraud) and choosing an operating point with **asymmetric business costs** — a false review costs analyst time, but a false block auto-declines a real customer.
* **Engineering Wins:**
    * 📈 **AUROC 0.9474** offline (Kaggle credit card dataset, 30% held-out); **alert precision 23.4%** in a live 40K-transaction stream at 200 tx/s.
    * ⚙️ **Micro-batched scoring** (100 tx per HTTP call) — ~50× throughput multiplier at negligible added latency vs per-message scoring; **14–25 ms** per batch.
    * 🎯 **Percentile-calibrated risk scores** (0–100) instead of raw `decision_function` output — turns unusable model output into a thresholdable business signal. `review ≥ 99`, `block ≥ 99.9`.
    * 🔧 **Retuned the operating point from ~8% flag rate → 1.6%** after the first end-to-end run — cut alert volume 5× while keeping precision, making the queue actually workable by a real analyst team.
    * ✅ Consumer group lag = **0** at 200 tx/s, verified via `kafka-consumer-groups.sh` — scorer sustained the full producer rate.

### 3. [Distributed Rate Limiter Service](https://github.com/smit0801/Distributed-Rate-Limiter)
*A high-performance, distributed rate limiting service designed for concurrency safety and low latency.*

* **Stack:** Python (gRPC) workers behind Nginx (HTTP/2), Redis with atomic Lua scripts.
* **Key Challenge:** Eliminating race conditions under high concurrency while maintaining throughput.
* **Engineering Wins:**
    * ⚡ Sustained **~1,560 RPS with p95 latency ~71ms** under k6 load tests (100 concurrent VUs).
    * 🔒 **Atomic Lua scripts** implementing the Sliding Window Log algorithm over Redis ZSETs — race-free under contention.
    * ⚖️ Linear scaling via stateless gRPC workers and HTTP/2 multiplexing behind Nginx.

### 4. [Distributed Real-Time Collaborative Editor (G-Doc)](https://github.com/smit0801/G-Doc)
*A Google Docs–style collaborative editor supporting 50+ concurrent users across distributed backend nodes.*

* **Stack:** React + Monaco frontend, FastAPI backend, WebSockets, Redis Pub/Sub, PostgreSQL.
* **Key Challenge:** Synchronizing state across distributed server instances with sub-100ms latency, while keeping the database from collapsing under per-keystroke writes.
* **Engineering Wins:**
    * ⏱️ **<100ms edit propagation** across clients via WebSockets + Redis Pub/Sub cross-instance fan-out.
    * 💾 **Write-behind persistence layer** with in-memory dirty-tracking and async batch flushes — **~90% reduction in PostgreSQL writes** vs per-keystroke saves.
    * 🐛 Debugged real concurrency issues: **pub/sub echo** (server-ID filtering), **edit feedback loops** (remote-update flag), **stale initial state** on slow clients (deferred content hydration).

### 5. Detectrozen — Histopathological Scan Analysis
* **Overview:** Engineered a pipeline to process 1M+ medical images using CNNs (TensorFlow/Keras).
* **Impact:** Achieved **95.2% diagnostic accuracy**; published research in **IJSRCSEIT**.

---

## 📫 Connect with Me

* 📧 **Email:** smitmhatre0801@gmail.com
* 💼 **LinkedIn:** [linkedin.com/in/smitmhatre](https://www.linkedin.com/in/smitmhatre/)

