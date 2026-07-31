# cybersecurity-home-lab
Documentation of my hands-on cybersecurity home lab — SOC analyst training

## Lab Environment

**Host machine:** Dell XPS 15 9530 — Intel i9-13900H, 64GB RAM, Windows 11 Pro
**Hypervisor:** VMware Workstation Pro (26H1)

### Virtual Machines
| VM | OS | Role | Network |
|----|----|------|---------|
| Kali Linux | Kali 2026.2 | Attacker / analyst workstation | NAT |
| Windows 11 Target | Win 11 Enterprise (Eval) | Victim endpoint | NAT |

**Lab IP addresses:**
- Kali (attacker): `192.168.42.128`
- Windows target: `192.168.42.130`
- Gateway (VMware NAT router): `192.168.42.2`
  
## Day 1 — Lab Setup
- Installed VMware Workstation Pro and verified the Kali image via SHA256 checksum before importing.
- Booted Kali, ran system updates (`apt update && apt full-upgrade`).
- Explored the network configuration:
  - Interface `eth0` on the `192.168.42.0/24` NAT subnet
  - Default gateway `192.168.42.2` (VMware NAT router)
  - Confirmed the `00:0c:29` MAC prefix identifies the VM as VMware-hosted

## Skills Practiced
- Virtualization setup and VM management
- File integrity verification (SHA256)
- Linux CLI basics and network reconnaissance (`ip a`, `ip route`)

## Day 3 — Adding a Windows Target
- Downloaded the Windows 11 Enterprise 90-day evaluation ISO from Microsoft's Evaluation Center.
- Built a Windows 11 VM in VMware (UEFI + Secure Boot + virtual TPM to meet Win11 requirements).
- Created a **local account** instead of a Microsoft account — a lab target shouldn't be tied to a real identity.
- Confirmed both machines share the `192.168.42.0/24` subnet and can reach each other directly.
- Next step: isolate both on a Host-Only network before running traffic captures.

## Day 4 - Security Fundamentals — Notes

**Vulnerability vs. Threat vs. Risk**
- *Vulnerability* — a weakness (e.g., an unpatched server).
- *Threat* — what could exploit it (e.g., a ransomware group scanning for that flaw).
- *Risk* — likelihood × impact of a threat hitting a vulnerability.
- You can't eliminate threats, only reduce vulnerabilities and manage risk.

**CIA Triad**
- *Confidentiality* — only authorized access (broken by a data breach).
- *Integrity* — data is accurate and unaltered (broken by tampering).
- *Availability* — systems are up when needed (broken by DDoS or outage).
