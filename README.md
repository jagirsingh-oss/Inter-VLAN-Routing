**Project Overview**
This project demonstrates hybrid inter-VLAN routing using two different approaches:

Router-on-a-Stick (ROAS) for Layer 2 switch VLANs
Layer 3 Switch Inter-VLAN Routing with IP routing enabled

The topology simulates a real-world enterprise network where different departments are segmented using VLANs, and communication between networks is facilitated through a central router.

**Concepts Covered**
VLAN creation and configuration
Trunk port configuration (802.1Q)
Router sub-interfaces (ROAS)
Layer 3 switch configuration
IP routing on Layer 3 switches
Inter-VLAN routing (both ROAS and SVI-based)
Default gateway configuration
Multi-network routing
End-to-end connectivity testing

**Network Topology
Network Components**

+ 1 Central Router (connecting both switches)
+ 1 Layer 2 Switch (using ROAS for inter-VLAN routing)
+ 1 Layer 3 Switch (using IP routing and SVIs)
+ 2 VLANs on Layer 2 Switch (4 PCs total - 2 per VLAN)
+ 3 VLANs on Layer 3 Switch (6 PCs total - 2 per VLAN)

           **[Router]**
         /            \
        /              \
   [L2-Switch]      [L3-Switch]
   (ROAS)          (IP Routing)
    /      \          /      |     \
 VLAN100 VLAN200     VLAN100 VLAN200 VLAN300
  PC1-2  PC3-4        PC5-6   PC7-8   PC9-10

  
