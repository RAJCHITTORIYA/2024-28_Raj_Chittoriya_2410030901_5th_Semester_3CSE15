# 2024-28_Raj_Chittoriya_2410030901_5th_Semester_3CSE15



# Cisco–AICTE Virtual Internship 2026: Cyber Security Project

# Secure Hybrid Datacenter Network Architecture & Multi-Tier Cloud Segmentation
### *Zero Trust Architecture, AWS Multi-VPC Isolation, IAM Least Privilege, Kubernetes Micro-segmentation & Threat Mitigation*

---

## 1. Project Overview
This repository contains the complete design, declarative configurations, security matrices, threat models, validation scripts, and report documentation for the **Cisco–AICTE Virtual Internship Program 2026 (Cyber Security Domain)**.

- **Author / Intern**: Individual Cyber Security Intern
- **Domain**: Cyber Security
- **Track**: Cisco–AICTE Virtual Internship 2026
- **Architecture Model**: Zero Trust Hybrid Enterprise Network (Private Datacenter + AWS Multi-VPC Cloud + Multi-Tenant Kubernetes)
- **Primary Deliverables**: Architecture Blueprint, Declarative Security Group/IAM/Kubernetes configs, Automated 10-Point Security Test Engine, Threat Matrix (STRIDE), and Comprehensive Internship Report.

---

## 2. Official Problem Statement
> "After your impressive audit in Part 1, the college IT department has invited you to contribute to a new project: working on the data center security.
> Many applications are hosted in the enterprise datacenter as well as public cloud today... Since data has to exit the private data center to reach the public cloud, there must be strong network security and segmentation...
> Faculty members also now work flexibly from home or campus, and require uninterrupted, secure access to teaching tools, research repositories, and internal services...
> Your task is to design a secure hybrid datacenter network architecture that supports applications connecting or using services between private datacenter and public cloud."

---

## 3. High-Level Hybrid Architecture Diagram

```
                              [ PUBLIC INTERNET ]
                                      |
                     [ AWS WAF / Ingress Security (TLS 1.3) ]
                                      |
         +----------------------------+----------------------------+
         |                            |                            |
  [ Student VPC ]              [ Teaching VPC ]             [ Research VPC ]
  (10.100.0.0/16)              (10.101.0.0/16)             (10.102.0.0/16)
  +------------------+         +------------------+        +------------------+
  | Public ALB Subnet|         | Public ALB Subnet|        | NO Public Subnet |
  | (10.100.1.0/24)  |         | (10.101.1.0/24)  |        | (Air-Gapped In)  |
  +--------+---------+         +--------+---------+        +--------+---------+
           |                            |                           |
  +--------v---------+         +--------v---------+        +--------v---------+
  | App Pods Subnet  |         | App Pods Subnet  |        | HPC Compute      |
  | (10.100.10.0/24) |         | (10.101.10.0/24) |        | (10.102.10.0/24) |
  +--------+---------+         +--------+---------+        +--------+---------+
           |                            |                           |
  +--------v---------+         +--------v---------+        +--------v---------+
  | DB Tier Subnet   |         | DB Tier Subnet   |        | Encrypted Data DB|
  | (10.100.20.0/24) |         | (10.101.20.0/24) |        | (10.102.20.0/24) |
  +------------------+         +------------------+        +------------------+
         |                            |                            |
         +----------------------------+----------------------------+
                                      |
                           [ Transit Gateway (TGW) ]
                                      |
                       [ Security & Monitoring Hub VPC ]
                               (10.103.0.0/16)
                       - Central SIEM / Log Aggregator
                       - MFA-Gated Bastion Host
                                      |
              ==================================================
                 HYBRID IPsec VPN TUNNEL (AES-256-GCM / IKEv2)
              ==================================================
                                      |
                        [ Datacenter Edge Firewall ]
                                      |
                     [ Enterprise Private Datacenter ]
                               (172.16.0.0/16)
                     - Identity Services (LDAP / AD: 172.16.10.10)
                     - Enterprise Core DB & ERP (172.16.20.50)
💡 Learning Outcomes

Cybersecurity

Ethical hacking fundamentals

Security principles and defense in depth

Vulnerability Assessment and Penetration Testing

STRIDE threat modelling

Cloud & Network Security

AWS VPC isolation

Security Groups and NACLs

Transit Gateway routing

IPsec VPN concepts

WAF and controlled ingress

CloudTrail and VPC Flow Logs

Identity Security

IAM least privilege

MFA

STS temporary credentials

Explicit Deny policies

Kubernetes

Namespace isolation

RBAC

NetworkPolicy

Non-root workloads

Read-only filesystem

Reduced service-account exposure

Automation

Python-based security verification

Repeatable ALLOW/DENY validation

Evidence-driven policy checking

🔭 Future Scope

Integrate Trivy and Checkov into CI/CD security workflows.

Add Cilium and Falco for runtime Kubernetes security monitoring.

Evaluate AWS Direct Connect with MACsec for dedicated encrypted connectivity.

Extend the Python engine into continuous automated security regression testing.

Add richer incident-response and centralized observability workflows.

🙏 Acknowledgement

I express my sincere gratitude to AICTE, EduSkills Foundation, Cisco Networking Academy, and IILM University, Greater Noida for providing the opportunity to participate in the AICTE–EduSkills Virtual Internship Program 2026.

I am especially thankful to Mr. Abhinav Raghav, Instructor, Cisco Networking Academy, IILM University, for his guidance and mentorship throughout the internship.

🔗 Reference Links

Cisco Networking Academy

Cisco Packet Tracer

AWS Documentation

Kubernetes Documentation

OWASP

IETF RFC 1918

NIST Zero Trust Architecture
