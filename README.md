# Homelab Network Core

## Overview
This repository documents my homelab infrastructure built to practice **enterprise-style networking, virtualization, identity, monitoring, and security operations**. The environment is centered around **Proxmox VE** and is designed as a small production-like lab where I can test **network segmentation, internal infrastructure services, identity-aware access, reverse proxy publishing, DNS, PKI, monitoring, and security tooling**.

The lab also serves as the foundation for future portfolio projects related to **SIEM/log pipelines, WAF and reverse proxy security, hybrid/cloud connectivity, and network automation**.

---

## Objectives
- Build a structured homelab using **Proxmox** as the virtualization platform
- Segment services and management traffic using **VLANs** and firewall policy
- Host core infrastructure services such as **DNS, PKI, identity, IPAM, and monitoring**
- Publish selected internal services securely through a **reverse proxy**
- Use the environment as a practical lab for **network, cloud, and security engineering**
- Maintain infrastructure documentation and service inventory using **NetBox**

---

## Core Infrastructure

### Virtualization Platform
- **Proxmox VE** – primary hypervisor for hosting infrastructure VMs and self-hosted services

### Network and Security
- **OPNsense** – firewall, routing, NAT, and inter-VLAN policy enforcement
- **Managed switching / VLANs** – segmentation of management, infrastructure, and service networks
- **Tailscale gateway** – secure remote access / overlay connectivity into the homelab
- **Nginx Proxy Manager** – reverse proxy for controlled exposure of internal web services

### Identity, DNS, and PKI
- **Windows Server** – core Windows infrastructure services including:
  - **DNS**
  - **NPS**
  - **Certificate Authority**
- **Authentik** – identity provider / SSO platform for internal services
- **AdGuard Home** – DNS filtering and local resolver functionality

### Infrastructure Documentation and Secrets
- **NetBox** – IPAM / DCIM / infrastructure documentation
- **Vaultwarden** – internal secrets / password vault

### Monitoring and Visibility
- **PRTG** – infrastructure monitoring
- **Grafana** – dashboards and visualization for infrastructure observability

---

## Lab Use Cases
This environment is used to practice and document:

- **Proxmox virtualization** and service hosting
- **Firewalling, NAT, and segmentation** using OPNsense
- **VLAN-based network design** for infrastructure and services
- **DNS, PKI, and Windows-based network services**
- **Identity-aware access** using Authentik
- **Remote access / overlay networking** using Tailscale
- **Infrastructure monitoring and dashboards** with PRTG and Grafana
- **IPAM and infrastructure documentation** with NetBox
- **Secure publishing of internal services** through reverse proxying

---

## Platform Components

### 1) Virtualization Layer
The homelab runs on **Proxmox VE**, which hosts the core infrastructure and application VMs. Proxmox acts as the foundation for service isolation, VM lifecycle management, and future lab expansion.

This includes workloads for:
- network and security services
- Windows infrastructure services
- monitoring platforms
- internal self-hosted applications
- documentation and identity services

---

### 2) Network Edge and Segmentation
**OPNsense** acts as the lab firewall/router and provides:
- WAN edge connectivity
- internal routing between VLANs / subnets
- NAT and policy enforcement
- segmentation between management, infrastructure, and application networks

The network is intentionally designed around **segmentation instead of a flat LAN**, allowing services to be grouped by function and protected through firewall policy.

Planned documentation for this repository includes:
- VLAN IDs and purpose
- subnet assignments
- inter-VLAN routing paths
- administrative access restrictions
- which services are internal-only vs externally reachable

---

### 3) DNS, PKI, and Windows Infrastructure
A dedicated **Windows Server** VM provides core internal services for the lab, including:
- **DNS**
- **Network Policy Server (NPS)**
- **Certificate Authority (CA)**

This gives the lab a more realistic enterprise-style foundation and allows testing of:
- internal DNS resolution
- certificate issuance for internal services
- Windows-based identity and access workflows
- future authentication or 802.1X / certificate-based scenarios

---

### 4) Identity and Access
**Authentik** is used as the lab’s **identity provider (IdP)** for centralized authentication and SSO across supported internal applications.

This allows the lab to simulate:
- centralized authentication flows
- protected access to internal applications
- identity-aware access patterns for self-hosted services
- future integration with reverse proxy access control

---

### 5) DNS Filtering and Name Resolution
**AdGuard Home** provides DNS filtering and resolver functionality for the environment. It is used alongside internal DNS services to support:
- local name resolution
- filtering / policy control for clients
- cleaner internal service access
- visibility into DNS activity within the lab

---

### 6) Remote Access and Overlay Networking
A **Tailscale gateway** provides secure remote access into the homelab environment. This supports:
- administrative access to internal resources
- remote troubleshooting
- secure access without exposing internal services directly to the internet
- future access workflows for hybrid and security-related labs

---

### 7) Infrastructure Documentation and IPAM
**NetBox** is used for **IP address management, inventory, and infrastructure documentation**.

This is one of the most important parts of the lab because it keeps the environment documented like a real infrastructure platform rather than an undocumented collection of VMs.

NetBox is intended to document:
- subnets and VLANs
- IP assignments
- devices and service roles
- logical infrastructure relationships
- future expansion of rack/device/service documentation

---

### 8) Monitoring and Observability
The lab includes both **PRTG** and **Grafana** to improve visibility into the environment.

#### PRTG
Used for infrastructure monitoring such as:
- device reachability
- service availability
- network health and status checks
- basic infrastructure alerting

#### Grafana
Used for:
- dashboards
- visualization of infrastructure metrics
- future integrations with additional telemetry sources

---

### 9) Secrets and Internal Services
**Vaultwarden** is used as a self-hosted secrets/password vault for the environment.  
This supports better operational hygiene when working with:
- admin credentials
- service credentials
- internal documentation references
- lab access workflows

---

### 10) Reverse Proxy and Service Publishing
**Nginx Proxy Manager** is used to publish selected internal services in a more controlled way.

This layer is intended to support:
- reverse proxying for internal web applications
- TLS termination
- easier access to internal services
- future integration with identity-aware access and application protection

---

## Current Services in Scope
This repository documents the core platform components of the homelab, including:

- **Proxmox**
- **OPNsense**
- **Windows Server (DNS / NPS / CA)**
- **AdGuard Home**
- **Authentik**
- **Tailscale gateway**
- **NetBox**
- **Vaultwarden**
- **PRTG**
- **Grafana**
- **Nginx Proxy Manager**

As the lab evolves, this repository will be expanded with service diagrams, screenshots, implementation notes, and sanitized configuration examples.

---

## High-Level Topology
A topology diagram will be added to show:

- internet / WAN edge
- OPNsense firewall
- internal VLANs / subnets
- Proxmox host and VM groups
- Windows infrastructure services
- Authentik / AdGuard / NetBox / Vaultwarden
- monitoring stack
- reverse proxy placement
- remote access path through Tailscale

---

## Security Design Goals
The lab is designed with the following security goals in mind:

- segment infrastructure and services using VLANs and firewall rules
- restrict administrative access paths
- avoid unnecessary exposure of internal services
- centralize identity where possible
- use internal PKI / certificate services for lab workflows
- improve visibility through monitoring and future security tooling
- document the environment like a real infrastructure platform

---

## Repository Structure
This repository will be expanded with the following structure:

```text
homelab-network-core/
├─ README.md
├─ diagrams/
├─ screenshots/
├─ configs/
└─ notes/
