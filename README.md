# Inter-VLAN Routing Project (RoaS & SVI)

A comprehensive network topology demonstration using **Cisco Packet Tracer** that showcases both traditional Router-on-a-Stick (RoaS) and modern Switch Virtual Interface (SVI) configurations for inter-VLAN routing.

## 📋 Project Overview

This project implements a hybrid network architecture featuring:
- **Router-on-a-Stick (RoaS)** configuration on Side A
- **Switch Virtual Interfaces (SVI)** on a Multilayer Switch on Side B
- **Static routing** between both sides for complete network connectivity

The topology demonstrates the evolution from traditional Layer 2 switching with external routing to modern Layer 3 switching capabilities.

---

## 🏗️ Network Architecture

### Topology Structure

```
Side A (RoaS)                    Side B (SVI)
┌─────────────┐                ┌──────────────┐
│   Switch 1  │                │     MLS      │
│  (Layer 2)  │                │  (Layer 3)   │
└──────┬──────┘                └──────┬───────┘
       │                              │
       │ Trunk (802.1Q)               │
       │                              │
┌──────┴──────┐                       │
│   Router    ├───────────────────────┘
│ (Sub-intf)  │    Transit: 10.0.0.0/30
└─────────────┘
```

### Device Roles

| Device | Type | Function |
|--------|------|----------|
| **Router** | Layer 3 Router | Performs inter-VLAN routing for Side A using sub-interfaces |
| **Switch 1** | Layer 2 Switch | VLAN segmentation with trunk to Router |
| **MLS** | Multilayer Switch | Layer 3 switching with SVI interfaces for VLAN routing |

---

## 📊 IP Addressing Scheme

### VLAN Configuration

| Location | VLAN ID | VLAN Name | Network Segment | Default Gateway |
|----------|---------|-----------|-----------------|-----------------|
| Switch 1 | 100 | Developer | 192.168.11.0/24 | 192.168.11.1 |
| Switch 1 | 200 | HR | 192.168.12.0/24 | 192.168.12.1 |
| MLS | 100 | Developer | 192.168.13.0/24 | 192.168.13.1 |
| MLS | 200 | HR | 192.168.14.0/24 | 192.168.14.1 |
| MLS | 300 | Security | 192.168.15.0/24 | 192.168.15.1 |

### Transit Network

| Link | Network | Router IP | MLS IP | Purpose |
|------|---------|-----------|--------|---------|
| Router ↔️ MLS | 10.0.0.0/30 | 10.0.0.1 | 10.0.0.2 | Inter-site routing |

---

## 🔧 Configuration Details

### Router Configuration (Side A)
- **Sub-interfaces** created for each VLAN (100, 200)
- **802.1Q encapsulation** on sub-interfaces
- **IP addresses** configured as default gateways for respective VLANs
- **Static routes** to reach Side B networks via MLS

### Switch 1 Configuration (Side A)
- **VLANs** created (100, 200)
- **Trunk port** configured to Router with 802.1Q encapsulation
- **Access ports** assigned to appropriate VLANs

### Multilayer Switch Configuration (Side B)
- **`ip routing`** enabled for Layer 3 functionality
- **SVIs** created for VLANs 100, 200, and 300
- **IP addresses** configured on SVI interfaces
- **Static routes** to reach Side A networks via Router

### Key Technologies Implemented
- ✅ VLAN segmentation
- ✅ 802.1Q trunk encapsulation
- ✅ Router-on-a-Stick (RoaS)
- ✅ Switch Virtual Interfaces (SVI)
- ✅ Static routing
- ✅ Layer 3 switching

---

## 🚀 Getting Started

### Prerequisites
- **Cisco Packet Tracer** (version 7.3 or higher recommended)
- Basic understanding of VLANs and routing concepts

### Installation & Setup

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/jagirsingh-oss/Inter-VLAN-Routing.git
   ```

2. **Open the topology file**
   - Launch Cisco Packet Tracer
   - Open `inter-VLAN-Routing.pkt` from the repository

3. **Verify the configuration**
   - All devices should be pre-configured
   - Check device configurations using CLI commands

---

## 🧪 Testing Connectivity

### Ping Test Examples

Test inter-VLAN routing within the same side:
```
PC1 (VLAN 100, Side A) → PC3 (VLAN 200, Side A)
ping 192.168.12.5
```

Test routing between sides:
```
PC0 (VLAN 100, Side A) → PC9 (VLAN 300, Side B)
ping 192.168.15.5
```

Test all connectivity:
```
PC5 (VLAN 100, Side B) → PC1 (VLAN 100, Side A)
ping 192.168.13.5
```

### Expected Results
✅ All PCs should be able to ping across VLANs and sides
✅ Traceroute should show proper routing paths
✅ No packet loss in simulation mode

---

## 📖 Learning Objectives

By exploring this project, you will understand:
- How to configure Router-on-a-Stick for inter-VLAN routing
- Implementing Switch Virtual Interfaces on Multilayer Switches
- Differences between Layer 2 and Layer 3 switching
- Static routing configuration between network segments
- VLAN trunk configuration with 802.1Q encapsulation
- Network segmentation best practices

---

## 🛠️ CLI Command Reference

### Quick Configuration Snippets

**Router Sub-interface (VLAN 100)**
```cisco
interface fa0/0.100
encapsulation dot1Q 100
ip address 192.168.11.1 255.255.255.0
```

**MLS SVI (VLAN 100)**
```cisco
ip routing
interface vlan 100
ip address 192.168.13.1 255.255.255.0
no shutdown
```

**Static Route (Router to MLS)**
```cisco
ip route 192.168.13.0 255.255.255.0 10.0.0.2
```

For complete configurations, refer to `configuration.txt`.

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs or issues
- Suggest improvements
- Submit pull requests
- Add additional test scenarios

---

## 📝 License

This project is available for educational purposes. Feel free to use and modify for learning.

---
