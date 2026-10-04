# CC Experiment 01 — Hypervisor Performance Comparison

## Performance Evaluation of Type-1 and Type-2 Hypervisors

---

## 1. Objectives

1. To study the working of Type-1 and Type-2 hypervisors.
2. To configure and run a virtual machine using a Type-1 hypervisor.
3. To configure and run a virtual machine using a Type-2 hypervisor.
4. To execute the same CPU benchmark on both virtual machines.
5. To compare the performance of both virtualization environments based on execution time, CPU throughput, and latency.

---

# 2. Type-1 Hypervisor — Proxmox VE

## 2.1 Configuration

The Type-1 virtualization environment was created using **Proxmox VE**.

| Parameter | Configuration |
|---|---|
| Hypervisor | Proxmox VE |
| Hypervisor Type | Type-1 |
| Virtualization | KVM |
| VM Name | CC-Exp1-Type1 |
| Guest OS | Ubuntu 22.04.5 LTS |
| CPU | 2 vCPU |
| CPU Type | x86-64-v2-AES |
| Memory | 2048 MiB |
| Storage | 20 GB |
| Network | VirtIO / vmbr0 |
| Benchmark | Sysbench CPU 1.0.20 |
| Prime Number Limit | 20000 |
| Number of Threads | 1 |

---

## 2.2 Architecture

Proxmox VE is a **Type-1 (bare-metal) hypervisor**. It runs directly on the physical hardware and uses KVM for virtualization.

```text
+--------------------------------------+
|       Ubuntu 22.04.5 LTS VM          |
|                                      |
|       2 vCPU | 2 GB RAM | 20 GB     |
+--------------------------------------+
|              KVM                     |
|       Virtualization Layer           |
+--------------------------------------+
|          Proxmox VE                  |
|          Type-1 Hypervisor           |
+--------------------------------------+
|       Physical Hardware              |
|        CPU | RAM | Storage           |
+--------------------------------------+
