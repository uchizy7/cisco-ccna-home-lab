# Network Troubleshooting Guide

## Common Issues & Solutions

### Issue 1: OSPF Neighbors Not Showing Up
**Symptoms:** 
- `show ip ospf neighbor` returns empty
- Routers cannot ping each other

**Root Cause:**
- Hello/Dead timers don't match
- Network statement missing
- Interface shutdown

**Solution:**
```bash
# Check interface is up
show ip interface brief

# Check OSPF timers
show ip ospf interface

# Verify network statement
show run | include network

# Fix mismatched timers
interface Eth0/0
 ip ospf hello-interval 10
 ip ospf dead-interval 40
```

### Issue 2: VLAN Traffic Not Routing Between Switches
**Symptoms:**
- Ping from VLAN 10 to VLAN 20 fails
- Interfaces up but no communication

**Root Cause:**
- Trunk port misconfigured
- Native VLAN mismatch
- Router-on-Stick not configured

**Solution:**
```bash
# Verify trunk mode
show interfaces trunk

# Fix trunk port
interface Eth0/0
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30

# Check native VLAN
show interfaces trunk
```

### Issue 3: BGP Routes Not Advertising
**Symptoms:**
- BGP neighbor shows "Established" but no routes learned
- `show bgp summary` shows neighbors but `show ip route bgp` empty

**Root Cause:**
- Network statement not matching
- Neighbor not activated in address-family
- ACL blocking routes

**Solution:**
```bash
# Check BGP configuration
show run | section bgp

# Verify neighbors
show bgp summary

# Check advertised routes
show ip bgp
```

## Debugging Commands Cheat Sheet

| Command | Purpose |
|---------|---------|
| `show ip ospf neighbor` | Check OSPF adjacencies |
| `show ip route ospf` | View OSPF learned routes |
| `show ip ospf database` | View OSPF topology database |
| `debug ip ospf adj` | Debug OSPF neighbor formation |
| `show bgp summary` | Check BGP neighbors |
| `show ip bgp` | View BGP routing table |
| `show vlan brief` | List all VLANs |
| `show interfaces trunk` | Verify trunk ports |
| `show access-lists` | View ACL rules |

---

## Lab Recovery Steps

If the lab breaks completely:

1. Reset all routers to default (Erase NVRAM)
2. Reload the Packet Tracer file
3. Re-apply configurations from `configs/` folder
4. Verify with commands from troubleshooting section
