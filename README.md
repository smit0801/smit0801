# Hello there, I'm Smit Mhatre! 👋

**Master's in Computer Science @ Stevens Institute of Technology** 📍 *Hoboken, NJ / NYC Area*

I am a software engineer specializing in **Distributed Systems**, **High-Performance Infrastructure**, and **Scalable Backend Architecture**. I enjoy engineering systems that can handle high concurrency with strict correctness guarantees, moving beyond just "making it work" to "making it scale."

---

## 🛠️ Technical Stack

| Category | Technologies |
|----------|--------------|
| **Languages** | ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white) ![C++](https://img.shields.io/badge/-C%2B%2B-00599C?style=flat&logo=c%2B%2B&logoColor=white) ![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) ![SQL](https://img.shields.io/badge/-SQL-4479A1?style=flat&logo=postgresql&logoColor=white) |
| **Backend & Systems** | ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat&logo=fastapi&logoColor=white) ![gRPC](https://img.shields.io/badge/-gRPC-255F85?style=flat&logo=grpc&logoColor=white) ![Redis](https://img.shields.io/badge/-Redis-DC382D?style=flat&logo=redis&logoColor=white) ![WebSockets](https://img.shields.io/badge/-WebSockets-000000?style=flat) |
| **Infrastructure** | ![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/-Nginx-009639?style=flat&logo=nginx&logoColor=white) ![AWS](https://img.shields.io/badge/-AWS-232F3E?style=flat&logo=amazon-aws&logoColor=white) ![Linux](https://img.shields.io/badge/-Linux-FCC624?style=flat&logo=linux&logoColor=black) |
| **Observability & Tools** | ![Prometheus](https://img.shields.io/badge/-Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/-Grafana-F46800?style=flat&logo=grafana&logoColor=white) ![k6](https://img.shields.io/badge/-k6-7D64FF?style=flat&logo=k6&logoColor=white) |

---

## 🚀 Featured Engineering Projects

### 1. [Distributed Rate Limiter Service](https://github.com/smit0801/Distributed-Rate-Limiter)
*A high-performance, distributed rate limiting service designed for concurrency safety and low latency.*

* **Architecture:** Python (gRPC) workers behind Nginx load balancers with Redis (Lua) for atomic coordination.
* **Key Challenge:** Eliminating race conditions under high concurrency while maintaining throughput.
* **Engineering Wins:**
    * ⚡ Sustained **1,560 requests/sec** with **p95 latency ~71ms**.
    * 🔒 Implemented **Atomic Lua Scripts** to implement the Sliding Window Log algorithm.
    * ⚖️ Achieved linear throughput scaling via stateless gRPC workers and HTTP/2 multiplexing.

### 2. [Distributed Real-Time Collaborative Editor](https://github.com/smit0801/G-Doc)
*A production-grade collaborative editing system (Google Docs style) supporting 50+ concurrent users.*

* **Architecture:** React frontend, FastAPI backend, WebSockets for sync, and Redis Pub/Sub for horizontal scaling.
* **Key Challenge:** Synchronizing state across distributed server instances with sub-second latency.
* **Engineering Wins:**
    * ⏱️ Achieved **<100ms synchronization latency** using optimized WebSocket payloads.
    * 🔄 Implemented **Redis Pub/Sub** to broadcast updates across multiple backend nodes (scaling beyond a single server).
    * 🛡️ Built a conflict-resolution system inspired by CRDTs for handling concurrent edits.

### 3. Detectrozen (Medical Image Analysis)
* **Overview:** Engineered a pipeline to process 1M+ medical images using CNNs (TensorFlow/Keras).
* **Impact:** Achieved **95.2% diagnostic accuracy**; published research in **IJSRCSEIT**.


## 📫 Connect with Me

* 📧 **Email:** smitmhatre0801@gmail.com
* 💼 **LinkedIn:** [linkedin.com/in/Smit](https://www.linkedin.com/in/smitmhatre/)
* 🎓 **Resume:** [View My Resume](#)
