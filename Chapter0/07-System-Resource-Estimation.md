# 📦 System Resource Estimation (BOTECs Made Simple)

This guide walks through examples of **back-of-the-envelope calculations (BOTECs)** used to estimate the feasibility of large-scale systems like Twitter. It includes practical assumptions, formulas, and approximations for servers, storage, bandwidth, and cost.

---

## 🧠 What Is a BOTEC?

**BOTEC** stands for **Back-of-the-envelope calculation** – a quick estimate to check if a system design idea is feasible before building anything.

**Analogy**: Planning juice for 100 guests → 1 bottle serves 5 → You need ~20 bottles.  
Fast. Not perfect. Good enough.

---

## 🏗️ Case: Designing Twitter at Scale

### Assumptions:
| Metric                          | Value              |
|---------------------------------|--------------------|
| Daily Active Users (DAUs)       | 500 million        |
| Requests per user per day       | 20                 |
| Total requests per day          | 10 billion         |
| Server capacity (64-core)       | 64,000 req/sec     |
| Seconds in a day                | 86,400             |

---

## 📟 Server Estimation

### ✅ Average Load:
Requests/sec = 10B / 86,400 ≈ 115,740 RPS  
Servers = 115,740 / 64,000 ≈ 2

🟡 Note: Too optimistic. Assumes traffic is evenly spread.

---

### 🔺 Peak Load:
Servers = 500M / 64,000 = 7,813 OR 10B req/sec = 157,000 servers

---

## ⚙️ Reducing Load

### Option 1: Improve Throughput
- WhatsApp handled 2M connections/server (2012)
- Optimization can triple performance

### Option 2: Spread Load (Pareto 80/20 Rule)
- 80% of traffic in 20% of the time (4.8 hrs = 17,280 sec)
- 8B / 17,280 = 463K RPS → 463K / 64K ≈ 8 servers

---

## 💰 Server Cost Estimation

| Servers        | Cost/hour (AWS) | Total/hour     |
|----------------|------------------|----------------|
| 2              | $3.55           | $7.10          |
| 8              | $3.55           | $28.40         |
| 157,000        | $3.55           | $557,350       |

---

## 💾 Storage Estimation

### Assumptions:
| Metric                          | Value              |
|---------------------------------|--------------------|
| Tweets per user per day         | 3                  |
| Total tweets/day                | 1.5 billion        |
| Size per tweet                  | 250 bytes          |
| 10% tweets with image (200KB)   | 150M × 200KB = 30TB|
| 5% tweets with video (3MB)      | 75M × 3MB = 225TB  |

---

### 📦 Daily Storage:
| Type      | Estimate           |
|-----------|--------------------|
| Text      | 1.5B × 250B = 375GB|
| Images    | 30 TB              |
| Videos    | 225 TB             |
| **Total** | ≈ 255 TB/day       |
| Yearly    | ≈ 93 PB/year       |

---

## 🌐 Bandwidth Estimation

### Incoming:
255 TB/day = ~24 Gbps

### Outgoing (based on 50 tweet views/user/day):
| Type     | Estimate     |
|----------|--------------|
| Text     | 0.58 Gbps    |
| Images   | 46.24 Gbps   |
| Videos   | 346.8 Gbps   |
| **Total**| ≈ 393.62 Gbps|

**Combined Total (In + Out): ≈ 418 Gbps**

---

## ✅ Summary Table
| What               | Estimate                 |
|--------------------|--------------------------|
| 🖥️ Servers         | 2–157K (avg vs peak)     |
| 💾 Storage         | 255 TB/day = 93 PB/year |
| 🌐 Bandwidth       | ~418 Gbps               |
| 💰 Cost            | $7 – $500K+/hour        |

---

## 🧯 Handling Spikes
- Disable personalization
- Use CDN for static content
- Throttle or cache aggressively
- Use queues, circuit breakers, fallbacks

> Graceful degradation keeps services online under stress.

---

> BOTECs are fast, helpful for interviews and planning. But always validate with real metrics later.
