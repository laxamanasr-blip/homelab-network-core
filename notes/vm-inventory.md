# VM Inventory

This document tracks the major virtual machines and services running in the homelab.

## Core Infrastructure

### OPNsense
- **Role:** Virtual firewall / router
- **Purpose:** Inter-VLAN routing, WAN connectivity, firewall policy enforcement, and gateway services for the lab
- **Notes:** Router-on-a-stick design on Proxmox with multiple VLAN-backed interfaces

### Windows Server
- **Role:** Core Windows infrastructure services
- **Purpose:** DNS, NPS, and Certificate Authority
- **Notes:** Used to simulate enterprise-style internal infrastructure services

### NetBox
- **Role:** IPAM / documentation platform
- **Purpose:** Track subnets, VLANs, service inventory, and infrastructure documentation

### Authentik
- **Role:** Identity provider
- **Purpose:** Centralized authentication / SSO for supported internal services

### AdGuard Home
- **Role:** DNS filtering / resolver
- **Purpose:** DNS filtering, local resolution support, and visibility into DNS activity

### Tailscale Gateway
- **Role:** Remote access gateway
- **Purpose:** Secure remote access into the homelab environment

---

## Monitoring and Operations

### PRTG
- **Role:** Monitoring platform
- **Purpose:** Infrastructure monitoring, reachability checks, and service visibility

### Grafana
- **Role:** Dashboard / visualization platform
- **Purpose:** Visualization of infrastructure and monitoring data

### Vaultwarden
- **Role:** Password / secrets vault
- **Purpose:** Secure storage of credentials and internal access information

---

## Storage / User Services

### Nextcloud
- **Role:** Self-hosted cloud storage
- **Purpose:** Internal file storage and platform testing

### Jellyfin
- **Role:** Media service
- **Purpose:** Self-hosted media platform running in the lab

### Agent DVR
- **Role:** Video / surveillance workload
- **Purpose:** CCTV / DVR-related service hosted in the environment

---

## Network Lab Platforms

### EVE-NG
- **Role:** Network simulation platform
- **Purpose:** Practice network designs and troubleshooting scenarios

### GNS3
- **Role:** Network emulation / lab platform
- **Purpose:** Build and test network scenarios separately from the production-like homelab services

---

## To Be Expanded
This file will later be updated with:
- operating systems
- IP addresses / VLAN placement
- VM IDs
- resource allocations
- backup / restore notes
- dependency notes between services
