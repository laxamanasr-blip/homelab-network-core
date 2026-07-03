
# Network Design

## Overview
The homelab uses an **OPNsense router-on-a-stick (ROAS)** design running as a VM on **Proxmox**.  
A **VLAN-aware bridge** on the Proxmox host carries multiple tagged networks from a managed switch into the OPNsense VM, allowing the firewall to terminate multiple VLAN-backed interfaces while the rest of the lab services remain virtualized on the same host.

This design allows the environment to simulate a small production-style network with:
- multiple WAN uplinks
- segmented internal networks
- a dedicated home / Deco network path
- an isolated VM compute network for infrastructure services

---

## Core Design
The lab is built around the following principles:

- **virtualized firewall/router** using OPNsense on Proxmox
- **VLAN-based separation** instead of a flat network
- **dedicated internal VM network** for hosted infrastructure services
- **separate home/client network path** through the Deco environment
- **dual ISP connectivity** for resilience and testing

---

## VLAN Design

### VLAN 10 – PLDT WAN
- **Purpose:** Primary ISP handoff
- **Role in lab:** Main WAN interface for OPNsense

### VLAN 30 – Globe WAN
- **Purpose:** Secondary / backup ISP handoff
- **Role in lab:** Secondary WAN interface for failover / alternate internet path

### VLAN 50 – Deco / Home Network Uplink
- **Purpose:** Uplink for the TP-Link Deco mesh / home client network
- **Role in lab:** Separates home/user traffic from the internal VM compute environment

### VLAN 60 – Internal VM / Compute Network
- **Purpose:** Isolated network for hosted virtual machines and infrastructure services
- **Role in lab:** Main network for internal services hosted on Proxmox

---

## Traffic Flow Summary
A managed switch trunks the required VLANs to the Proxmox host.  
Inside Proxmox, the OPNsense VM terminates the tagged interfaces and provides:

- routing between internal networks
- WAN connectivity handling
- firewall policy enforcement
- gateway services for the isolated VM network
- separation between home/client traffic and infrastructure workloads

---

## Proxmox Networking
The current design uses Proxmox as both:
- the virtualization platform for hosted services
- the platform on which the OPNsense virtual firewall runs

Key concepts in the design:
- a **VLAN-aware bridge** on Proxmox carries the trunked networks
- OPNsense consumes multiple tagged interfaces from that bridge
- the internal VM network is isolated from the home network and controlled through OPNsense
- hosted services sit behind the virtual firewall rather than directly on a flat LAN

---

## OPNsense Role
OPNsense is the central routing and security point of the homelab and is responsible for:

- terminating VLAN-backed interfaces
- providing default gateway services for internal networks
- enforcing firewall policy
- controlling connectivity between the VM network and the home/deco network
- handling WAN connectivity and failover design

Security tooling attached to the OPNsense platform includes:
- **Suricata IDS/IPS**
- **Zenarmor NGFW**

---

## Design Goals
This network design supports the following goals:

- simulate a production-like routed environment inside a homelab
- separate home/client traffic from infrastructure services
- support multiple WAN uplinks
- provide a controlled network for internal services and future security projects
- make it easier to test reverse proxy, monitoring, DNS, and identity workflows without collapsing everything into a flat LAN
