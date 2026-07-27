# cybersecurity-home-lab
Documentation of my hands-on cybersecurity home lab — SOC analyst training

## Lab Environment

**Host machine:** Dell XPS 15 9530 — Intel i9-13900H, 64GB RAM, Windows 11 Pro
**Hypervisor:** VMware Workstation Pro (26H1)

### Virtual Machines
| VM | OS | Role | Network |
|----|----|------|---------|
| Kali Linux | Kali 2026.2 | Attacker / analyst workstation | NAT |

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
