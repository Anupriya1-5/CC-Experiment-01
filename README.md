# CC Experiment 01 – Hypervisor Performance Analysis

## CPU Performance Comparison of Type-1 and Type-2 Hypervisors

This experiment focuses on evaluating the CPU performance of two virtualization platforms: **Proxmox VE**, which represents a Type-1 hypervisor, and **VMware Workstation**, which represents a Type-2 hypervisor. Ubuntu virtual machines with comparable resources were configured on both platforms and tested using the **Sysbench CPU benchmark**.

### Experimental Result

The Proxmox VE virtual machine recorded **1689.43 events/sec**, while the VMware Workstation virtual machine recorded **1058.76 events/sec**. The benchmark results indicate a difference in CPU throughput and latency between the two virtualization environments.

---

## Table of Contents

1. [Aim](#1-aim)
2. [Hypervisor Classification](#2-hypervisor-classification)
3. [Common VM Configuration](#3-common-vm-configuration)
4. [Type-1 Hypervisor – Proxmox VE](#4-type-1-hypervisor--proxmox-ve)
5. [Type-2 Hypervisor – VMware Workstation](#5-type-2-hypervisor--vmware-workstation)
6. [Performance Comparison](#6-performance-comparison)
7. [Performance Analysis](#7-performance-analysis)
8. [Conclusion](#8-conclusion)
9. [Project Structure](#9-project-structure)
10. [VM Shutdown](#10-vm-shutdown)

---

# 1. Aim

The experiment is carried out with the following objectives:

- To create and configure an Ubuntu virtual machine using **Proxmox VE**.
- To create and configure another Ubuntu virtual machine using **VMware Workstation**.
- To allocate comparable CPU, memory, and storage resources to both VMs.
- To run an identical CPU benchmark on both virtual machines.
- To record the CPU performance measurements.
- To compare the throughput and latency obtained from both hypervisor platforms.

---

# 2. Hypervisor Classification

| Feature | Proxmox VE | VMware Workstation |
|---|---|---|
| Hypervisor Type | Type-1 | Type-2 |
| Virtualization Model | Bare-metal | Hosted |
| Main Technology | KVM | VMware Virtualization |
| Host Environment | Directly on physical hardware | Runs over a host operating system |

### Type-1 Hypervisor

A Type-1 hypervisor operates directly on the physical hardware of the computer. It manages virtual machines and allocates hardware resources without requiring a conventional host operating system between the hypervisor and hardware.

**Proxmox VE** is used as the Type-1 platform in this experiment and uses **KVM** for virtualization.

### Type-2 Hypervisor

A Type-2 hypervisor operates as software on top of an existing operating system. The host operating system remains responsible for managing the physical hardware.

**VMware Workstation** is used as the Type-2 platform in this experiment.

### Basic Architecture

#### Proxmox VE – Type-1

```text
+----------------------+
|      Ubuntu VM       |
+----------+-----------+
           |
           v
+----------------------+
|   Proxmox VE / KVM   |
+----------+-----------+
           |
           v
+----------------------+
|  Physical Hardware   |
+----------------------+
