# VMware vSphere Infrastructure Implementation
## Project Overview

This project documents the architecture, deployment, configuration, and validation of a resilient and highly available VMware vSphere infrastructure designed to simulate an enterprise-grade datacenter environment.

The implementation focuses on:

High Availability (HA)

Automated resource balancing (DRS)

Shared storage architecture (NFS)

Live migration (vMotion)

Zero-downtime protection (Fault Tolerance)

Advanced troubleshooting in nested virtualization environments

Infrastructure Architecture
Core Components

vCenter Server Appliance

Three VMware ESXi Hosts

Cluster01 configured with:

vSphere High Availability (HA)

vSphere Distributed Resource Scheduler (DRS)

Network Design

Two Standard Virtual Switches were configured across all ESXi hosts.

vSwitch0

Management Network

Virtual Machine Network

vSwitch1

vMotion VMkernel Adapter

NFS Storage VMkernel Adapter

Network traffic was logically and physically segregated to optimize performance and enhance security.

Storage Infrastructure

Backend Storage: Red Hat Enterprise Linux 9.2 Virtual Machine

Configured as an NFS Server

Shared datastore mounted across all ESXi hosts

Content Library created for centralized ISO management

This architecture enabled:

Cluster-wide shared storage

HA and DRS functionality

Template-based VM provisioning

Virtual Machine Lifecycle Management

The project included extensive validation of VM lifecycle operations:

Snapshot creation and management

Virtual machine cloning

Template creation (Thin Provisioning)

Live migration using vMotion

VMware Tools installation and verification (RHEL and Photon OS)

vSphere High Availability (HA)

To validate HA functionality:

A host failure was simulated.

The virtual machine experienced temporary downtime.

vSphere HA automatically restarted the VM on a surviving host.

Connectivity was restored without manual intervention.

This demonstrated automated disaster recovery capabilities.

vSphere Distributed Resource Scheduler (DRS)

Cluster01 was configured with:

Automation Level: Fully Automated

Migration Threshold: Aggressive

Virtual Machine Automation enabled

DRS automatically handled:

Initial VM placement

Continuous load balancing via live migrations

This ensured optimized resource utilization across the cluster.

vSphere Fault Tolerance (FT)

Fault Tolerance was implemented to achieve zero-downtime protection.

Real Lab Environment

FT Logging enabled on VMkernel adapter

Primary and Secondary VM deployment configured

CPU compatibility challenges addressed

VMware Hands-on Labs Validation

Dedicated EVC-enabled cluster created

CPU baseline unified using Enhanced vMotion Compatibility (EVC)

Admission Control limitations resolved

FT status successfully transitioned to Protected

This validated full lockstep VM execution with continuous availability.

Challenges and Lessons Learned
VMkernel Network Connectivity Issue

Root cause was traced to instability in the Linux-based host operating system running VMware Workstation.

Resolution:

Environment rebuilt on Windows host

Network stability restored

NFS datastore successfully mounted

EVC and Hardware Compatibility Challenges

CPU mismatches prevented Fault Tolerance deployment.

Resolution:

Nested ESXi host provisioned on identical physical hardware

Learned the importance of enabling EVC in production clusters

Resource Contention in Nested Environment

Memory constraints blocked FT synchronization.

Resolution:

Adjusted VM resource allocation

Optimized cluster memory usage

Gained deeper understanding of Admission Control policies

Linux Kernel Update Breaking VMware Workstation

Kernel updates caused module incompatibility.

Resolution:

Reverted to compatible kernel version

Ensured VMware modules compiled correctly

Avoided automatic kernel updates during lab timeline

Key Skills Demonstrated

VMware vSphere Administration

ESXi Host Deployment and Configuration

vCenter Management

HA, DRS, and FT Implementation

VMkernel Networking Configuration

NFS Storage Configuration using RHEL

Enhanced vMotion Compatibility (EVC)

Nested Virtualization Troubleshooting

Enterprise Datacenter Simulation

Team Members

Islam Yasser

Fatma Ahmed

Tasneem Adel

Supervisor:
Eng. Ekram AbdelWahab
