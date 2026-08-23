# Casey Allen

### Network & Network Security Engineer — multi-vendor infrastructure, automation, and the lab I break things in

> **Built in public, and still building.** This page, the
> [lab hub](https://github.com/117caseyallen-NetAdm/casey-lab), and every project
> repo are living documents — updated as the environment grows, not written once
> and abandoned. The commit histories are the changelog.

I run a **dual-site enterprise network on real hardware** — no GNS3, no EVE-NG — and
document it publicly as I build. Two firewalled sites joined into a single OSPF
routing domain across an IPsec tunnel, with separated data and management planes,
aggregated uplinks, and a services layer that grows every month.

Everything here is homelab work, built and broken by me — designed, configured,
debugged, and documented end to end.

---

## 🔬 The Lab

![CASEY-LAB Topology](https://raw.githubusercontent.com/117caseyallen-NetAdm/casey-lab/main/topology/CA-LAB-Topo.svg)

**Four network operating systems in one fabric:** Palo Alto PAN-OS, Cisco IOS,
Juniper Junos, Arista EOS — plus Proxmox VE and Debian on the compute side.

| | |
|---|---|
| **Routing** | Flat OSPF area 0 unified across a route-based IKEv2 IPsec tunnel (PA-440 ⇄ SRX345); firewalls inject defaults as Type-5 LSAs |
| **Aggregation** | LACP where both ends support it, static EtherChannel where the hardware predates it — capability-matched, not copy-pasted |
| **Addressing** | Deliberate plan: data / management / transit planes on separate ranges, consistent fleet-wide |
| **Access** | Dual-homed jumpboxes per site, redundant trunked access switching, routed remote-access VPN |

## 📦 Projects

| Repo | What it is |
|---|---|
| **[casey-lab](https://github.com/117caseyallen-NetAdm/casey-lab)** | The hub — living topology diagram, fabric overview, and the full build roadmap. Start here. |
| **[homelab-wireguard](https://github.com/117caseyallen-NetAdm/homelab-wireguard)** | Routed (non-NATed) WireGuard remote-access VPN. Client pool redistributed into OSPF for fleet-wide reachability across the IPsec tunnel. Build notes + a real troubleshooting log. |

> Every repo ships with the debugging story, not just the working config. The
> four hours where it *didn't* work are the part worth reading.
>
> Each project links back to the [hub](https://github.com/117caseyallen-NetAdm/casey-lab),
> and the hub carries the topology every project plugs into — so you can start
> anywhere and find your way around.

## 🛠️ Working with

**Network** — Palo Alto PAN-OS · Cisco IOS · Juniper Junos & SRX · Arista EOS · Juniper Mist · Fortinet
**Routing & switching** — OSPF · IPsec (IKEv2) · 802.1Q · LACP / EtherChannel · VLAN & SVI design · WireGuard
**Platform** — Proxmox VE · VMware vSphere/ESXi · LXC · Windows Server · Active Directory · Linux
**Cloud & security** — AWS · Azure · GCP · Splunk · Microsoft Sentinel · CrowdStrike · Nessus · Okta
**Automation** — Python · PowerShell · Git · Ansible *(Batfish, Suzieq, Nornir/NAPALM in progress)*

## 📜 Certifications

`JNCIA-SEC` · `JNCIA-Junos` · `AZ-700 Azure Network Engineer` · `CompTIA Security+` ·
`CompTIA CySA+` · `CompTIA Network+` · `CompTIA A+` · `ISC2 CC` ·
`AWS Cloud Practitioner` · `Splunk Core Certified User`

**In progress:** CCNA

## 🗺️ What's next in the lab

Building toward a complete, automated enterprise environment:

1. **Platform** — Proxmox cluster, quorum device, backup server
2. **Identity & core services** — AD DS / DNS / DHCP, internal PKI, 802.1X wired auth via RADIUS across all four switch vendors
3. **Network operations** — Oxidized config backup → self-hosted Git, NetBox as source of truth, LibreNMS, centralized syslog
4. **Security operations** — SIEM, Suricata IDS on a mirrored port, per-client VPN policy, guest/IoT segmentation
5. **NetDevOps** — Batfish snapshot validation + Suzieq runtime state in a CI pipeline: config change → PR → behavioral diff → automated deploy → post-change validation

Each phase ships as its own documented repo.

## 📫 Connect

[LinkedIn](https://www.linkedin.com/in/casey-allen-6612a7133)
