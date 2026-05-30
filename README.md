# Cisco-Packet-Tracer-Project
# 🔒 Cisco Packet Tracer – Security Lab (VLANs, ACLs & Firewall)

A beginner-friendly network security lab built in Cisco Packet Tracer. This project demonstrates core security concepts including **VLAN segmentation**, **standard and extended ACLs**, and **basic firewall zoning**.

---

## 📋 Table of Contents
- [Network Topology](#network-topology)
- [Devices & IP Addressing](#devices--ip-addressing)
- [Features Demonstrated](#features-demonstrated)
- [Getting Started](#getting-started)
- [Configuration Guide](docs/configuration-guide.md)
- [Troubleshooting](docs/troubleshooting.md)

---

## 🗺️ Network Topology

```
                        INTERNET (Cloud)
                              |
                         [ISP Router]
                         203.0.113.1
                              |
                    +---------+---------+
                    |   Edge Firewall   |  
                    |  (ASA / Router)   |
                    |  203.0.113.2 WAN  |
                    |  192.168.1.1 LAN  |
                    +---------+---------+
                              |
                    +---------+---------+
                    |   Core Switch     |
                    |  (Layer 3 Switch) |
                    +--+----+----+------+
                       |    |    |
              VLAN 10  | VLAN 20 | VLAN 30
           (Management)| (Users) |(Servers)
           10.10.10.0  |10.10.20.|10.10.30.0
               /24     |   0/24  |   /24
                       |         |
               [SW-1]  |  [SW-2] | [SW-3]
              Mgmt PCs | User PCs| Servers
```

### VLAN Layout

| VLAN | Name       | Subnet         | Purpose                     |
|------|------------|----------------|-----------------------------|
| 10   | MGMT       | 10.10.10.0/24  | Admin / Management access   |
| 20   | USERS      | 10.10.20.0/24  | General employee workstations|
| 30   | SERVERS    | 10.10.30.0/24  | Internal servers (Web, DNS)  |
| 99   | NATIVE     | N/A            | Native VLAN (unused traffic) |

---

## 🖥️ Devices & IP Addressing

| Device        | Interface  | IP Address       | VLAN / Role          |
|---------------|------------|------------------|----------------------|
| ISP-Router    | Fa0/0      | 203.0.113.1/30   | Simulated Internet   |
| Edge-Firewall | Fa0/0      | 203.0.113.2/30   | WAN (Outside)        |
| Edge-Firewall | Fa0/1      | 192.168.1.1/24   | LAN (Inside)         |
| Core-Switch   | VLAN 10    | 10.10.10.1/24    | MGMT Gateway         |
| Core-Switch   | VLAN 20    | 10.10.20.1/24    | USERS Gateway        |
| Core-Switch   | VLAN 30    | 10.10.30.1/24    | SERVERS Gateway      |
| Admin-PC      | NIC        | 10.10.10.10/24   | VLAN 10 – Management |
| User-PC-1     | NIC        | 10.10.20.10/24   | VLAN 20 – Users      |
| User-PC-2     | NIC        | 10.10.20.11/24   | VLAN 20 – Users      |
| Web-Server    | NIC        | 10.10.30.10/24   | VLAN 30 – Servers    |
| DNS-Server    | NIC        | 10.10.30.11/24   | VLAN 30 – Servers    |

---

## ✅ Features Demonstrated

- **VLAN Segmentation** — Isolates traffic between departments
- **Inter-VLAN Routing** — Layer 3 switch routes between VLANs
- **Standard ACLs** — Restricts management access by source IP
- **Extended ACLs** — Controls traffic by protocol, source, and destination
- **Firewall Zoning** — Separates Inside, Outside, and DMZ traffic
- **Trunk Links** — Carries multiple VLANs between switches
- **Default Gateway / Static Routes** — Basic routing between zones

---

## 🚀 Getting Started

### Requirements
- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) 8.0 or later (free with Cisco NetAcad account)

### Open the Lab
1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR-USERNAME/cisco-security-lab.git
   ```
2. Open Packet Tracer
3. Go to **File → Open** and select `cisco-security-lab.pkt`
4. Follow the [Configuration Guide](docs/configuration-guide.md) to configure each device step by step

### File Structure
```
cisco-security-lab/
├── cisco-security-lab.pkt      # Packet Tracer project file
├── README.md                   # This file
├── docs/
│   ├── configuration-guide.md  # Step-by-step setup instructions
│   └── troubleshooting.md      # Common issues & fixes
└── configs/
    ├── edge-firewall.txt        # Edge router/firewall config
    ├── core-switch.txt          # Layer 3 switch config
    ├── access-switch-1.txt      # Access switch (MGMT VLAN)
    ├── access-switch-2.txt      # Access switch (USERS VLAN)
    └── access-switch-3.txt      # Access switch (SERVERS VLAN)
```

---

## 📚 Learning Objectives

After completing this lab you will be able to:
- Explain why VLANs are used for network security
- Configure VLANs and trunk ports on Cisco switches
- Write and apply standard and extended ACLs
- Understand basic firewall inside/outside zone concepts
- Verify connectivity using `ping` and `traceroute`

---

## 🤝 Contributing

Pull requests welcome! If you find a config issue or want to add a new security feature (e.g., DHCP snooping, port security), feel free to open a PR.

---

## 📄 License

MIT License — free to use for learning and education.
