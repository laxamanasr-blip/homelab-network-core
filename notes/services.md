# Services

## Overview
This document summarizes the major services hosted in the homelab and the role each service plays in the overall platform.

---

## Identity and Access

### Authentik
- **Purpose:** Identity provider / SSO platform
- **Use in lab:** Centralized authentication for supported internal applications and future identity-aware access integrations

### Tailscale Gateway
- **Purpose:** Secure remote access into the homelab
- **Use in lab:** Remote administration and internal service access without broadly exposing services to the internet

### Vaultwarden
- **Purpose:** Password and credential management
- **Use in lab:** Storage of internal service credentials and operational secrets

---

## Core Network / Infrastructure Services

### OPNsense
- **Purpose:** Firewall, router, WAN gateway, inter-VLAN routing
- **Use in lab:** Central traffic control point for the entire environment

### Windows Server
- **Purpose:** DNS, NPS, Certificate Authority
- **Use in lab:** Enterprise-style core infrastructure services and authentication / certificate workflows

### AdGuard Home
- **Purpose:** DNS filtering / resolver platform
- **Use in lab:** DNS filtering, local name resolution support, and DNS visibility

### NetBox
- **Purpose:** IPAM / DCIM / infrastructure documentation
- **Use in lab:** Source of truth for addressing, VLANs, service inventory, and infrastructure notes

---

## Monitoring and Visibility

### PRTG
- **Purpose:** Monitoring platform
- **Use in lab:** Monitor infrastructure availability and service health

### Grafana
- **Purpose:** Visualization and dashboards
- **Use in lab:** Present infrastructure telemetry and future metrics integrations

---

## Storage and User Services

### Nextcloud
- **Purpose:** Self-hosted cloud storage
- **Use in lab:** File storage, internal access workflows, and service hosting practice

### Jellyfin
- **Purpose:** Media service
- **Use in lab:** Self-hosted media platform

### Agent DVR
- **Purpose:** DVR / surveillance-related workload
- **Use in lab:** Video / camera-related service hosting

---

## Network Simulation Platforms

### EVE-NG
- **Purpose:** Network simulation
- **Use in lab:** Practice network architecture, routing, and troubleshooting scenarios

### GNS3
- **Purpose:** Network emulation
- **Use in lab:** Build isolated lab scenarios without changing the production-like service environment
