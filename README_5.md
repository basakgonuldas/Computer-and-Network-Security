# Network Routing Protocol Comparison: OSPF vs RIP

This project involves the configuration and analysis of dynamic routing protocols—OSPF and RIP—on a multi-router network topology. The aim is to compare their routing behavior, path selection criteria, and performance impact.


## 🧩 Project Objectives

1. Configure loopback interfaces on all routers with specific IP addresses.
2. Implement OSPF routing protocol using process ID `1` and area `0`.
3. Perform a traceroute from PC1 to PC2 and document the packet path.
4. Compare OSPF and RIP routing behavior using the same topology.
5. Explain differences in routing decisions and path selections.

---

## 🛠 Router Configurations

### Loopback Interface Assignments

| Router | Loopback1 IP        |
|--------|---------------------|
| R1     | 192.168.42.1        |
| R2     | 192.168.42.2        |
| R3     | 192.168.42.3        |
| R4     | 192.168.42.4        |
| R5     | 192.168.42.5        |

---

### OSPF Configuration (Process ID: 1, Area: 0)

| Router | Interface  | IP Address        |
|--------|------------|-------------------|
| R1     | Fa0/0      | 172.16.0.1        |
|        | Fa1/0      | 172.21.0.1        |
|        | Fa0/1      | 172.20.255.254    |
|        | Loopback1  | 192.168.42.1      |
| R2     | Fa0/0      | 172.16.255.254    |
|        | Fa0/1      | 172.17.0.1        |
|        | Fa1/0      | 172.22.0.1        |
|        | Loopback1  | 192.168.42.2      |
| R3     | Fa0/0      | 172.17.255.254    |
|        | Fa0/1      | 172.18.0.1        |
|        | Loopback1  | 192.168.42.3      |
| R4     | Fa0/0      | 172.18.255.254    |
|        | Fa0/1      | 172.19.0.1        |
|        | Loopback1  | 192.168.42.4      |
| R5     | Fa0/0      | 172.19.255.254    |
|        | Fa0/1      | 172.20.0.1        |
|        | Loopback1  | 192.168.42.5      |

---

## 🧪 Traceroute Analysis (PC1 → PC2)

- Traceroute performed from `PC1 (172.21.255.254)` to `PC2 (172.22.255.254)`.
- Topology diagram includes the route taken by packets under OSPF.

---

## 🔁 Routing Protocol Comparison

### RIP Behavior

- RIP selects routes based on **minimum hop count**.
- Shortest path (2 hops): `R1 → R2 → PC2`
- Alternative paths are longer (4-5 hops), and thus not selected.

#### RIP Route Evaluation:

1. R1 → R2 → PC2 → **(2 hops)**
2. R1 → R5 → R4 → R3 → R2 → PC2 → (5 hops)
3. R1 → R5 → R4 → R3 → PC2 → (4 hops)

**Selected Path:** `R1 → R2 → PC2`

### OSPF Behavior

- OSPF uses **cost metrics based on bandwidth**.
- Preference is given to higher-bandwidth links (e.g., 100 Mbps).
- Likely selected path: `R1 → R5 → R4 → R3 → R2 → PC2`

---

## 📊 Summary Table

| Protocol | Path                          | Criteria           | Hops | Preference Reason           |
|----------|-------------------------------|--------------------|------|-----------------------------|
| RIP      | R1 → R2 → PC2                 | Hop Count          | 2    | Least number of hops        |
| OSPF     | R1 → R5 → R4 → R3 → R2 → PC2  | Bandwidth (Cost)   | 5    | Higher bandwidth path       |

---


## 📌 Conclusion

This project demonstrates the distinct operational logic of RIP and OSPF routing protocols. While RIP selects the shortest path based on hop count, OSPF prioritizes paths with lower cost metrics, often influenced by bandwidth. These routing decisions directly affect network efficiency and reliability, making protocol selection a critical design factor in enterprise networks.
