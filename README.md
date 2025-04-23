# 📡 **Network Security Project – RIP v2 Configuration and Trace Route Tests**

![Cisco Network](https://img.shields.io/badge/Cisco-Router-blue)
![Status](https://img.shields.io/badge/status-completed-brightgreen)

## 📝 **Project Overview**

This project involves configuring routers (R6, R7, R8) with appropriate IP addresses and subnet masks, enabling interfaces, implementing RIP v2 routing protocol, and performing trace route tests between PCs to analyze the path of data packets in a simulated network.

---

## ⚙️ **Router Interface Configuration**

### 🔧 **R6, R7, R8 Setup**

- IP addresses and subnet masks are assigned to the interfaces of:
  - **R6**
  - **R7**
  - **R8**
- Interfaces are activated (`no shutdown`).

---

## 🔁 **RIP v2 Configuration**

- RIP version 2 is configured on **R6**, **R7**, and **R8**.
- Network statements include all directly connected networks.
- `version 2` and `no auto-summary` commands are used for modern routing behavior.

---

## 📈 **Trace Route Tests**

### ➤ **PC1 ➜ PC2**

- A trace route test is performed from PC1 to PC2.
- The path of the packets is observed.
- Results are captured and saved as screenshots in the original document.

### ➤ **PC1 ➜ PC3**

- A second trace route test is performed from PC1 to PC3.
- Hop-by-hop routing is analyzed.
- Results are also documented visually.

---

## ✅ **Conclusion**

This project demonstrates:
- Accurate IP addressing and interface configuration.
- Effective deployment of RIP v2 routing protocol across multiple routers.
- Use of diagnostic tools like trace route to validate network connectivity and routing paths.

---

> 🛠️ Simulated and tested using Cisco Packet Tracer for educational purposes.
