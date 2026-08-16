# Cisco CCNA Routing & Switching Home Lab

## Overview
This repository documents my hands-on Cisco CCNA Routing & Switching studies. It includes network topology designs, configurations, troubleshooting scenarios, and learning notes from 15+ Packet Tracer labs.

**Status:** In Progress (Expected CCNA certification: Q4 2026)

---

## Lab Topology
┌─────────────────────────────────┐
                │  Router R1 (Edge/ISP)           │
                │  IP: 203.0.113.1 /24            │
                │  BGP AS 64001                   │
                └──────────┬──────────────────────┘
                           │
                           │ Eth 0/0
                           │
                ┌──────────┴──────────┐
                │ Router R2 (Core)    │
                │ IP: 10.0.0.1 /8     │
                │ OSPF Area 0         │
                └──────┬──────────────┘
                       │
      ┌────────────────┼────────────────┐
      │                │                │
  ┌───┴───┐      ┌─────┴─────┐    ┌────┴────┐
  │ Sw-1  │      │  Sw-2     │    │  Sw-3   │
  │Access │      │Access     │    │Core     │
  └───┬───┘      └─────┬─────┘    └────┬────┘
      │                │               │
VLANs │          VLANs │         VLANs │
10,20 │          30,40 │         1,99  │
---

## Key Components

### Router Configurations

| Device | Model | IP Address | Routing Protocol | Purpose |
|--------|-------|-----------|-----------------|---------|
| R1 | Cisco 2911 | 203.0.113.1 | BGP AS 64001 | Edge/ISP |
| R2 | Cisco 2911 | 10.0.0.1 | OSPF Area 0 | Core |

### Switch Configurations

| Switch | VLANs | Spanning Tree | Purpose |
|--------|-------|---------------|---------|
| Sw-1 | 10, 20 | PVST | Access Layer |
| Sw-2 | 30, 40 | PVST | Access Layer |
| Sw-3 | 1, 99 | PVST | Core Layer |

---

## Lab Achievements

### Routing Protocols Implemented
- ✅ OSPF (Open Shortest Path First)
  - Area 0 backbone configuration
  - Hello/Dead intervals tuning
  - Neighbor adjacency verification
  
- ✅ BGP (Border Gateway Protocol)
  - AS 64001 configuration
  - Neighbor relationships
  - Route advertisements
  
- ✅ Static Routing
  - Default route configuration
  - Metric assignment

### VLAN Configuration
- ✅ 8 VLANs created and configured
- ✅ Inter-VLAN routing via Router-on-Stick (ROAS)
- ✅ Native VLAN configuration
- ✅ Access Control Lists (ACLs) applied to VLANs

### Network Security
- ✅ Standard ACLs (Layer 3 filtering)
- ✅ Extended ACLs (port-based filtering)
- ✅ Port Security on access switches
- ✅ SSH configuration on routers

### Redundancy & Failover
- ✅ OSPF failover testing (primary route convergence: 2-5 seconds)
- ✅ Rapid PVST spanning tree (convergence: 1-2 seconds)
- ✅ Backup route validation

---

## Lab Scenarios Completed

### Scenario 1: Multi-Area OSPF with Failover
**Objective:** Design and test OSPF failover behavior
- Configured OSPF Area 0 on 3 routers
- Tested path changes when primary link fails
- Measured convergence time: 3 seconds
- Result: ✅ PASS

### Scenario 2: VLAN Segmentation & Inter-VLAN Routing
**Objective:** Isolate traffic by VLAN and enable controlled routing
- Created VLANs for different departments (Sales, IT, Finance)
- Configured Router-on-Stick for inter-VLAN communication
- Tested ping between VLANs
- Result: ✅ PASS

### Scenario 3: Network Troubleshooting Challenge
**Objective:** Identify and fix misconfigured network
- Simulated broken OSPF adjacency (due to mismatched hello timers)
- Debugged with `show ip ospf neighbor` and `show ip ospf interface`
- Fixed timer mismatch
- Re-established adjacency
- Result: ✅ PASS (Resolved in 15 minutes)

---

## Configurations

### Router R1 (Edge) - Basic Configuration

### Router R2 (Core) - OSPF Configuration
---

## How to Use This Lab

### Prerequisites
- Cisco Packet Tracer (free download from Cisco Learning Network)
- Basic understanding of IP addressing and routing concepts

### Steps to Rebuild Lab

1. **Download:** Download the `.pkt` file from the repository
2. **Open:** Launch Cisco Packet Tracer and open the file
3. **Examine:** Review the topology and current configurations
4. **Configure:** Follow the configuration guides to add/modify settings
5. **Test:** Run the test scenarios to verify functionality
6. **Debug:** If tests fail, refer to troubleshooting guide

### Verification Commands

```bash
# Check OSPF neighbors
show ip ospf neighbor

# Verify OSPF routes
show ip route ospf

# Check VLAN membership
show vlan brief

# Verify ACLs
show access-lists

# BGP status
show bgp summary
```

---

## Learning Resources Used

- Cisco Learning Network (free courses)
- Professor Messer CCNA YouTube videos
- Cisco IOS Command Reference
- CCNA Study Guide (Todd Lammle)

---

## Next Steps

- [ ] Configure BGP route filtering with route-maps
- [ ] Implement OSPF area filtering
- [ ] Add GRE tunnel between remote sites
- [ ] Configure MPLS LDP
- [ ] Implement QoS policies

---

## Contact & Questions

If you have questions about this lab setup, feel free to reach out:
- **Email:** ugbechieedmund073@gmail.com
- **LinkedIn:** [linkedin.com/in/edmund-ugbechie](https://linkedin.com/in/edmund-ugbechie)
