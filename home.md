---
title: Homelab
description: The Homelab Wiki documents a personal IT lab simulating enterprise infrastructure. It covers networking (VLANs, MLAG, BGP), high availability hypervisors, NAS storage, and monitoring tools like Uptime Kuma, SNMP Traps, and Wazuh.
published: true
date: 2025-02-03T14:36:39.979Z
tags: homepage
editor: markdown
dateCreated: 2025-01-31T18:12:06.808Z
---

# Welcome to the Homelab Wiki  

The Homelab Wiki serves as a comprehensive resource for documenting the design, configuration, and operations of our personal homelab. This lab replicates enterprise-level IT infrastructure, offering shared resources and fostering collaborative learning among peers. Its purpose is to provide a testing ground for enterprise technologies and methodologies, enabling experimentation and hands-on experience.  

## #whoami
Our names are Michael DeSocio and Tyler Barnes. In an effort to both share knowledge between ourselves and the world, we combined our homelabs to better service the functions and capabilities that we want. With the available bandwidth and internet, it has become increasingly difficult to host items and projects within our residences. Therefore, we have located our homelab (for now) at a location owned by Michael's family with FTTP (Fiber to the Premises). This allows for us to have increased upload to perform tasks such as offsite backups, hosting media servers for friends and family, and provide a fast, remote site for hosting various projects. 

## Homelab Overview  

The homelab is structured to mirror the complexity of modern enterprise environments, including:  

### Enterprise Networking Structure  
The network is designed for reliability, scalability, and security using enterprise-grade protocols and configurations:  
- **VLANs**: To segment traffic, improve security, and optimize resource utilization.  
- **Firewalls and Routing Protocols**: To ensure controlled and efficient traffic management.  
- **MLAG (Multi-Chassis Link Aggregation)**: Provides redundancy and increased bandwidth by enabling multiple devices to operate as a single logical system. This ensures high availability and seamless failover in case of device failure.  
- **BGP (Border Gateway Protocol)**: Implements dynamic routing to enhance scalability and traffic optimization, supporting complex networking scenarios and integration with external networks.  

### High Availability Hypervisors  
Virtualized workloads run on high availability (HA) hypervisors to ensure uninterrupted service and fault tolerance. This infrastructure supports rapid provisioning of virtual machines for diverse applications and services.  

### NAS Storage  
A Network-Attached Storage (NAS) solution provides centralized and redundant storage, ensuring reliability and accessibility. The NAS supports data for virtual machines, user resources, and backups, forming a critical part of the homelab's resilience.  

### Enterprise Monitoring Tools  
Monitoring tools are implemented to ensure operational reliability and detect issues proactively:  
- **Uptime Kuma**: Tracks service status and application performance in real time.  
- **SNMP Traps**: Collects and processes network events for immediate troubleshooting.  
- **Wazuh**: An open-source security platform for threat detection, compliance monitoring, and incident response.  

## Purpose of the Wiki  

This wiki is designed to document every aspect of the homelab, from hardware specifications and network configurations to monitoring workflows and best practices. By consolidating this information, the wiki serves as both a technical reference and a collaborative platform for peers. It encourages knowledge sharing, continuous improvement, and the exchange of ideas related to enterprise IT infrastructure and operations.  

Explore the pages to learn more about the homelab, its components, and its configurations. This resource is continually updated to reflect new developments and insights.  
