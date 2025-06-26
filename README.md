
# VLAN & Trunk Port Network Topology

## 👨‍💻 Author
**Name:** Abubakri Faaruq Adebowale  
**Unique Code:** 06b4ad5b-1463-407b-b134-6d0373bdfff6

---

## 📌 Project Title
**Configuring VLANs and Trunk Ports with Inter-VLAN Routing and Security**

---

## 🎯 Objective
To implement network segmentation using VLANs, configure trunk ports for inter-VLAN communication, and apply network security best practices using Cisco Packet Tracer.

---

## 🧱 Network Topology Overview

### Devices Used:
- Router (R1) – Inter-VLAN routing (Router-on-a-Stick)
- Switch 1 (Layer 3) – VTP Server
- Switch 2 (Layer 2) – VTP Client 1
- Switch 3 (Layer 2) – VTP Client 2
- 6 PCs – 3 per VLAN

### VLAN Assignments:

| VLAN ID | Department | Subnet            | Devices        |
|---------|------------|-------------------|----------------|
| 10      | Admin      | 192.168.10.0/24   | Admin 1, 2, 3  |
| 20      | Guest      | 192.168.20.0/24   | Guest 1, 2, 3  |

---

## ⚙️ Configuration Summary

- **Switch Configuration:**
  - VTP domain created with Switch 1 as VTP Server
  - VLANs 10 and 20 created and propagated via VTP
  - Access ports assigned to VLANs
  - Trunk port configured (G0/0/3)

- **Router Configuration:**
  - Subinterfaces using `dot1Q` encapsulation
  - Each VLAN assigned a gateway IP

- **PC Configuration:**
  - Static IPs configured per VLAN
  - Gateway set to router subinterface

---

## 🔐 Security Implementation

| Security Measure         | Purpose                                |
|--------------------------|----------------------------------------|
| Port Security            | Limit MAC address per access port      |
| Disabled Unused Ports    | Prevent unauthorized physical access   |
| Trunk Port Hardening     | Prevent VLAN hopping attacks           |

---

## 🔁 Trunk Port Configuration

```bash
interface G0/0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 switchport nonegotiate
```

---

## 🔀 Inter-VLAN Routing (Router-on-a-Stick)

```bash
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

---

## ✅ Testing and Validation

- All PCs can ping their gateway
- Inter-VLAN communication successful
- Security controls tested and passed

---

## 🧾 Conclusion

This project demonstrates a secure and functional VLAN-based enterprise network using inter-VLAN routing and trunking. It follows standard Cisco configurations and includes basic network security controls.

---

## 📂 Files Included
- `Final_VLAN_Network_Documentation.docx` – Full project documentation
- `topology.png` (if available) – Network diagram
- `README.md` – This file

---

## 📎 Notes
Built and tested using Cisco Packet Tracer. Recommended for academic and training purposes.
