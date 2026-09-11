# SBT-DF203 Lab 3 — SYN Flood Pattern Investigation Using TShark

## Overview

This repository contains my practical work for **SBT-DF203: Basic Networking Skills for Digital Forensics — Lab 3**.

The aim of the lab was to investigate repeated TCP SYN activity against a local Apache web service and compare it with a normal TCP connection.

Rather than simply looking for SYN packets and assuming an attack had occurred, the practical focused on understanding the full TCP handshake, identifying incomplete connections, measuring the traffic with TShark, preserving the evidence correctly, and explaining what the packet capture does and does not prove.

The investigation was completed entirely inside an authorised Kali Linux virtual-machine environment.

---

## Student Information

**Student:** Athanasius Alekwe  
**Registration Number:** 2025/FWSD/11230  
**Course:** Basic Networking Skills for Digital Forensics  
**Course Code:** SBT-DF203  
**Lab:** Lab 3 — SYN Flood Pattern Investigation Using TShark  
**Environment:** Kali Linux / VMware Workstation  

---

## Objectives

The practical was completed to demonstrate the ability to:

- identify a normal TCP three-way handshake;
- distinguish complete and incomplete TCP connections;
- filter SYN, SYN-ACK, ACK and RST packets with TShark;
- create a normal HTTP baseline;
- perform the authorised four-SYN bounded simulation;
- calculate SYN counts and unique source ports;
- examine server response behaviour;
- build a packet-level forensic timeline;
- preserve evidence and verify integrity with SHA-256 hashes;
- compare normal traffic with suspicious/incomplete connection behaviour;
- explain the limitations of the evidence; and
- recommend appropriate detection and mitigation controls.

---

## Laboratory Environment

The practical was carried out on a Kali Linux virtual machine running in VMware Workstation.

### Tools Used

| Tool | Version / Purpose |
|---|---|
| Kali Linux | Forensic analysis environment |
| Apache HTTP Server | 2.4.68 — local test web server |
| TShark | 4.4.7 — packet capture and analysis |
| Wireshark | 4.4.7 — packet inspection |
| Scapy | 2.6.1 — controlled SYN packet generation |
| curl | Generated normal HTTP traffic |
| SHA-256 | Evidence integrity verification |
| VMware Workstation | Isolated virtual laboratory |

Apache was hosted locally on:

`127.0.0.1:80`

---

## Safety and Authorisation

This exercise was performed only inside an authorised laboratory environment.

The SYN simulation was deliberately restricted to:

- **Target:** `127.0.0.1`
- **Destination port:** `80`
- **Packet count:** `4`
- **TCP flag:** `SYN`

No public systems, third-party hosts, production networks or external services were targeted.

The simulation script was executed once and traffic generation stopped immediately after the required evidence was captured.

---

## Repository Structure

```text
SBT-DF203-Lab3/
│
├── SBT-DF203-Lab3_2025-FWSD-11230_ATHANASIUS_ALEKWE.pdf
│
├── evidence/
│   ├── mySYNFloodCapture.pcap
│   ├── normal_http.pcapng
│   └── bounded_syn_activity.pcapng
│
├── working/
│   └── bounded_syn_activity_working.pcapng
│
├── reports/
│   ├── ack_reset_candidates.tsv
│   ├── bounded_capture_hashes.txt
│   ├── expert_info.txt
│   ├── forensic_timeline.tsv
│   ├── forensic_timeline_summary.txt
│   ├── initial_syns.tsv
│   ├── normal_http_sha256.txt
│   ├── normal_vs_bounded.txt
│   ├── syn_ack_responses.tsv
│   ├── syn_capture_sha256.txt
│   ├── syn_counts_by_pair.txt
│   ├── tcp_analysis_events.tsv
│   └── unique_syn_source_ports.txt
│
├── screenshots/
│   └── Extracted practical evidence screenshots
│
└── scripts/
    └── syn_probe_lab.py
