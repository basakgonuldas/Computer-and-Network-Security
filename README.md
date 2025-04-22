# 📡 **Network Security Project – Router Configuration and ACL Implementation**

![Cisco Network](https://img.shields.io/badge/Cisco-Router-blue)
![Status](https://img.shields.io/badge/status-completed-brightgreen)

## 📝 **Project Overview**

This project simulates a small-scale enterprise network using Cisco routers, implementing RIP v1 routing and Access Control Lists (ACLs) to control and secure traffic flow between devices.

---

## ⚙️ **Network Configuration**

### 🔧 **R1 – RIP Setup**
- RIP v1 protocol enabled.
- Relevant networks added to RIP.
- Interfaces configured appropriately.

---

## 🔐 **Access Control List (ACL) Rules**

### 📌 **R1 – ACL 122 (fa0/0 interface, OUT direction)**

```bash
access-list 122 deny ip 192.168.151.0 0.0.0.255 any
access-list 122 permit ip 192.168.0.0 0.0.255.255 any
```

- ❌ Blocks all traffic from 192.168.151.0/24.
- ✅ Allows traffic from 192.168.0.0/16.

---

### 📌 **R2 – ACL 122 (fa1/0 interface, IN direction)**

```bash
access-list 122 permit ip any 192.168.26.0 0.0.0.255
access-list 122 deny icmp any any
access-list 122 permit ip any any
```

- ✅ Allows traffic destined for 192.168.26.0/24.
- ❌ Denies all ICMP traffic.
- ✅ Permits all remaining traffic.

---

### 📌 **R3 – ACL 150 (fa0/1 interface, OUT direction)**

```bash
access-list 150 deny tcp any any eq 80
access-list 150 permit ip any any
```

- ❌ Denies all HTTP traffic (port 80).
- ✅ Allows all other IP traffic.

---

## 🔁 **ACL Application Summary**

| Router | ACL  | Interface | Direction |
|--------|------|-----------|-----------|
| R1     | 122  | fa0/0     | OUT       |
| R2     | 122  | fa1/0     | IN        |
| R3     | 150  | fa0/1     | OUT       |

---

## 🧪 **Ping Tests and Observations**

### ➤ **PC0 ➜ PC1**
- ✅ Success  
- Unaffected as it bypasses the ACL on R1.

### ➤ **PC0 ➜ PC2**
- ❌ Failed  
- Blocked by R1's `deny ip` rule on fa0/0.

### ➤ **PC0 ➜ Server0**
- ❌ Failed  
- Blocked by R2's `deny icmp` rule on fa1/0.

---

## 🌐 **Web Access Results (PC1 ➜ Server0)**

### **HTTP (Port 80)**
- ❌ Failed  
- Denied by R3 due to the port 80 block rule.

### **HTTPS (Port 443)**
- ✅ Success  
- Permitted as no ACL blocks port 443.

---

## ✅ **Conclusion**

This project demonstrates how ACLs can selectively permit or deny traffic based on protocol, IP range, and port criteria. When combined with dynamic routing (RIP v1), these mechanisms form the foundation of a secure and segmented network infrastructure.

---


