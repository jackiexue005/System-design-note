# 🕒🛠️ Availability vs. Reliability in Distributed Systems

This chapter breaks down two important but often confused terms: **Availability** and **Reliability**. Let's explore what they really mean, how they're different, and why both matter for system design.

---

## ✅ What Is Availability?
> **Availability** is the percentage of time a system or service is working and accessible to users.

### ☕ Real-Life Analogy:
Think of your favorite **coffee shop**.
- If it's open 24/7, it's 100% available.
- If it's closed 3 days a year, that's ~99% availability.

### 📊 Formula:
$$Availability (%) = (Total Time – Downtime) / Total Time × 100$$

---

## 🔁 The Nines of Availability
| Availability | Downtime per Year     |
|--------------|------------------------|
| 90%          | 36.5 days              |
| 99.9%        | 8.76 hours             |
| 99.99%       | 52.56 minutes          |
| 99.999%      | 5.26 minutes           |
| 99.9999%     | ~30 seconds            |

---

## 🔧 What Is Reliability?
> **Reliability** is how long a system works **without failing**.

### 🚗 Real-Life Analogy:
Think of a **car**:
- If it runs for years with no breakdowns → very reliable.
- If it breaks down frequently → unreliable.

### 📏 Metrics:
- **MTBF (Mean Time Between Failures):** Time between failures.
- **MTTR (Mean Time To Repair):** Time it takes to fix after failure.

We want:
- ✅ High MTBF (few failures)
- ✅ Low MTTR (fast fixes)

---

## 🔄 Comparison Table
| Term           | What it Measures                   | Real-Life Analogy                     |
|----------------|------------------------------------|---------------------------------------|
| **Availability** | Is it working when you need it?     | Is the coffee shop open today?        |
| **Reliability**  | How often does it break?            | Does the car break down frequently?   |

---

## 🤔 Can You Have One Without the Other?

### ✅ High Reliability, Low Availability:
A great car that's locked in a garage most of the time. Reliable, but not always usable.

### ✅ High Availability, Low Reliability:
A rental car service with lots of cars—but they break down all the time.

---

## 🎯 The Goal
The ideal system has:
- ✅ High Availability (always accessible)
- ✅ High Reliability (rarely fails)

Together, they define how **trustworthy** and **robust** a system is.

---

> Understanding both helps design better services for users and meet service-level objectives (SLOs).
