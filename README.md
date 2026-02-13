# Azure VNet Peering & Cross-VNet Connectivity Lab

## 📌 Project Overview

This project demonstrates how to establish private communication between
two Azure Virtual Networks using **VNet Peering**.

The lab focuses on validating cross-VNet connectivity between two virtual
machines and troubleshooting ICMP (ping) failure caused by operating system
firewall configuration.

---

## 🧠 Architecture

- VNet-A (10.0.0.0/16)
  - Subnet-A (10.0.1.0/24)
  - VM-A

- VNet-B (10.1.0.0/16)
  - Subnet-B (10.1.1.0/24)
  - VM-B

- Bi-directional VNet Peering enabled

Both VNets were deployed in the same Azure region with non-overlapping
address spaces.

---

## 🛠️ Technologies Used

- Microsoft Azure
- Azure Virtual Networks
- VNet Peering
- Windows Virtual Machines
- Private IP Communication

---

## 🔧 Implementation Steps

1. Created two Virtual Networks with different address spaces
2. Deployed one virtual machine in each VNet
3. Configured bidirectional VNet Peering
4. Verified peering status was connected
5. Tested private IP connectivity between VMs

---

## ❌ Issue Encountered

Ping from VM-A to VM-B over private IP failed
even though VNet Peering was successfully configured.

---

## 🧠 Root Cause

ICMP traffic was blocked by the Windows Defender Firewall
on the destination virtual machine.

Azure networking and VNet Peering were configured correctly.
However, the operating system firewall was not allowing
ICMP Echo Requests.

---

## ✅ Resolution

- Accessed the destination virtual machine
- Enabled "File and Printer Sharing (Echo Request – ICMPv4-In)"
  in Windows Defender Firewall
- Retested connectivity
- Confirmed successful ping response between VNets

---

## 📘 Key Learnings

- VNet Peering enables private cross-network communication
- Successful cloud connectivity requires validation at both
  the Azure networking layer and the operating system layer
- ICMP is blocked by default in Windows environments
- Troubleshooting must include both infrastructure and OS validation

---

## 📷 Screenshots Included

- VNet-A configuration
- VNet-B configuration
- Peering status (Connected)
- Initial ping failure
- Windows Firewall ICMP rule enabled
- Successful ping response

