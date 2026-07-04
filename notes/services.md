# Services

This document lists the major services running in the homelab, their purpose, and how they fit into the overall platform.

---

## Core Platform Services

### OPNsense
- **Role:** Virtual firewall / router
- **Purpose:** Default gateway, inter-VLAN routing, WAN connectivity, NAT, and security policy enforcement
- **Notes:**
  - Runs as a VM on Proxmox
  - Uses a router-on-a-stick design with VLAN-backed interfaces
  - Connects the homelab to dual ISP paths and internal VLAN segments
  - Acts as the primary gateway for the internal lab network

---

### Nginx Proxy Manager
- **Role:** Reverse proxy / application publishing
- **Purpose:** Publishes internal services behind friendly subdomains and centralizes TLS termination
- **Notes:**
  - Used to expose internal services such as Grafana, NetBox, Authentik, Nextcloud, and AdGuard
  - Fronts services with HTTPS and custom certificates
  - Simplifies internal service access and acts as the main ingress layer for the homelab

**Example published services**
- `authentik`
- `grafana`
- `netbox`
- `nextcloud`
- `adguard`
- other internal tools and dashboards

---

### Authentik
- **Role:** Identity Provider (IdP) / SSO portal
- **Purpose:** Central authentication point for selected internal applications
- **Notes:**
  - Used to centralize access to internal services
  - Provides a single application portal for services such as Grafana, NetBox, Nextcloud, Proxmox, Vaultwarden, and Wazuh
  - Helps simulate enterprise-style identity and access workflows inside the lab

---

### NetBox
- **Role:** IPAM / infrastructure documentation platform
- **Purpose:** Tracks virtual machines, IP addressing, service inventory, and infrastructure metadata
- **Notes:**
  - Used as the source of truth for VM records and service inventory
  - Documents virtual machines, assigned IP addresses, service roles, and logical infrastructure relationships
  - Helps keep the lab structured like a documented production environment rather than an ad-hoc collection of VMs

---

### Grafana
- **Role:** Monitoring / observability dashboard
- **Purpose:** Provides visibility into host and service performance metrics
- **Notes:**
  - Used to monitor the Proxmox host and selected services
  - Tracks CPU, memory, disk, network traffic, and temperature metrics
  - Serves as the primary visualization layer for operational monitoring

---

### AdGuard Home
- **Role:** DNS filtering / DNS forwarding
- **Purpose:** Provides DNS resolution with ad and tracker filtering for internal clients
- **Notes:**
  - Used as an internal DNS filtering layer
  - Provides query visibility and filtering statistics
  - Integrated into the homelab as part of the internal service stack
  - A separate AWS-hosted AdGuard instance is also documented in NetBox for external/alternate DNS use cases

---

## Infrastructure and Access Services

### Windows Server
- **Role:** Internal Windows infrastructure services
- **Purpose:** Provides DNS, NPS, and Certificate Authority services for the lab
- **Notes:**
  - Used to simulate enterprise-style Microsoft infrastructure
  - Hosts internal DNS services and certificate-related functions
  - Supports authentication and certificate workflows used by other parts of the homelab

---

### Internal Certificate Authority
- **Role:** PKI / certificate issuance
- **Purpose:** Issues internal certificates for selected homelab services
- **Notes:**
  - Used to support TLS for internal applications and services
  - Helps simulate internal enterprise PKI workflows
  - Integrated with the Windows Server environment

---

### Tailscale Gateway
- **Role:** Remote access / VPN gateway
- **Purpose:** Provides secure access into the homelab from external networks
- **Notes:**
  - Used as a remote-access path into the environment
  - Useful for securely reaching internal services without exposing them broadly to the internet
  - Part of the management and remote administration layer of the lab

---

## Security and Operations Services

### Wazuh
- **Role:** SIEM / security monitoring
- **Purpose:** Provides security visibility, endpoint telemetry, and event monitoring
- **Notes:**
  - Used to collect and review endpoint telemetry and security-related information
  - Helps simulate SOC-style visibility and endpoint monitoring
  - Integrated into the broader monitoring and security side of the homelab

---

### Vaultwarden
- **Role:** Password manager / secrets storage
- **Purpose:** Stores credentials and access information for lab systems and services
- **Notes:**
  - Used for managing passwords and access credentials for homelab systems
  - Helps centralize access to internal applications and administrative accounts
  - Included as part of the platform’s operational security tooling

---

## Productivity / Utility Services

### Nextcloud
- **Role:** Self-hosted cloud storage
- **Purpose:** File storage, sync, and internal document hosting
- **Notes:**
  - Used for self-hosted file storage inside the lab
  - Provides a private storage platform for documents and internal files
  - Useful for testing storage, access, and application publishing workflows

---

### Jellyfin
- **Role:** Media streaming platform
- **Purpose:** Self-hosted media access and streaming
- **Notes:**
  - Runs on a Windows 11 VM in the environment
  - Included as part of the self-hosted application layer of the homelab
  - Also serves as a practical workload hosted behind the broader infrastructure stack

---

### AgentDVR / NVR
- **Role:** Camera monitoring / NVR
- **Purpose:** Local camera viewing and recording
- **Notes:**
  - Hosted in the lab as part of the Windows 11 workload
  - Demonstrates support for non-traditional infrastructure applications beyond core network services
  - Included as a practical example of a real service hosted within the environment

---

## Lab / Engineering Tooling

### GNS3
- **Role:** Network emulation platform
- **Purpose:** Used for network testing, simulation, and lab exercises
- **Notes:**
  - Used for building and testing network scenarios outside the production homelab service stack
  - Useful for routing, switching, and connectivity experiments

---

### EVE-NG
- **Role:** Network / systems lab platform
- **Purpose:** Used for more advanced network and infrastructure simulations
- **Notes:**
  - Supports labbing of network topologies and platform behavior
  - Complements the main Proxmox environment by providing a separate simulation platform for experiments and study

---

### Kali Linux
- **Role:** Security testing workstation
- **Purpose:** Used for lab validation, testing, and security tooling
- **Notes:**
  - Included as a utility VM for testing and security-related workflows
  - Used as part of the broader security-focused lab environment

---

## Service Relationships

High-level service flow inside the homelab:

- **OPNsense** provides routing, segmentation, and gateway services
- **Nginx Proxy Manager** publishes selected internal apps
- **Authentik** provides centralized access / SSO for selected services
- **NetBox** documents infrastructure and VM inventory
- **Grafana** provides monitoring visibility
- **AdGuard** provides DNS filtering and query visibility
- **Windows Server / CA** provides internal Windows infrastructure and certificate services
- **Wazuh** provides security monitoring
- **Vaultwarden** stores operational credentials
- **Nextcloud / Jellyfin / AgentDVR** represent hosted application workloads running on top of the platform

---

## Notes
This homelab is designed as a **small enterprise-style infrastructure environment** rather than a single-purpose lab. It combines:

- virtualization with Proxmox
- virtualized routing and segmentation with OPNsense
- identity and access services
- reverse proxy publishing
- monitoring and observability
- infrastructure documentation / IPAM
- security monitoring
- self-hosted application workloads

The goal is to use the environment both as a personal platform and as a place to practice cloud, network, and security engineering concepts in a realistic way.
