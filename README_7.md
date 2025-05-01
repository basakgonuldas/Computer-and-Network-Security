# 🌐 EIGRP Configuration and Redundancy Test in Cisco Network

## 🧩 Project Objective

In this project, configurations, routing, trace route tests, and metric calculations were performed on a network configured with the EIGRP protocol between Cisco Routers and PCs. A redundancy scenario was also tested.

---

## 🔧 Configurations Made

### 1. R1 Router Interface Settings
- The interfaces on R1 were configured with IP addresses.

---

### 2. EIGRP Configuration (AS 1)
- The `EIGRP` protocol was configured on all routers with `Autonomous System 1`.
- `Auto-summary` was disabled.
- EIGRP updates from the networks connected to `PC0` and `PC1` were excluded.

#### Router-based Configurations:
- R1 → EIGRP + interfaces
- R2 → EIGRP + passive-interface
- R3 → EIGRP + passive-interface
- R4 → EIGRP + passive-interface
- R5 → EIGRP + passive-interface

---

## 🔍 3. Trace Route Test

- A `traceroute` test was conducted from `PC0` to `PC1`.
- The test screenshot and the path reflected on the topology were added to the Word document.

---

## 📊 4. EIGRP Cost Calculation

EIGRP cost calculations for three routes to the `192.168.4.0/24` network:

### 🛣 Route 1: `R1 → R3 → R5 → PC1`
- Bandwidth: **70 Mbps**
- Delay: **342 µs**
- **Min Bandwidth:** `70,000,000 bps`

### 🛣 Route 2: `R1 → R4 → R5 → PC1`
- Bandwidth: **65 Mbps**
- Delay: **400 µs**
- **Min Bandwidth:** `65,000,000 bps`

### 🛣 Route 3: `R1 → R2 → R5 → PC1`
- Bandwidth: **80 Mbps**
- Delay: **350 µs**
- **Min Bandwidth:** `80,000,000 bps`

**📌 Result:** The lowest-cost path was calculated as `R1 → R3 → R5 → PC1`.

---

## 🚫 5. R4 Router Shutdown

### Steps:
1. The `Running Config` of `R4` was saved.
2. `R4` was physically powered off.
3. A new `traceroute` test was conducted from `PC0` to `PC1`.

---

## 📈 6. Alternate Route Explanation

The new path taken when R4 was shut down:

```text
PC0 → R1 → R3 → R5 → PC1
