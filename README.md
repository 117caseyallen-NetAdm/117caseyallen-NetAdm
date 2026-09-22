# Casey Allen

### Multi-vendor network lab — routing, security, and automation on physical hardware

Network engineering and administration projects, designed, built and run on
physical hardware at home: two firewalled sites, four network operating systems,
joined by a route-based IKEv2 IPsec tunnel into one OSPF area.

Both sites share one shelf and one internet uplink — the tunnel runs between the
firewalls' outside interfaces across the home router's LAN, which stands in for a
WAN. The routing and the vendor behaviour are real; the distance is not.

## Projects

| Repo | What it is |
|---|---|
| **[casey-lab](https://github.com/117caseyallen-NetAdm/casey-lab)** | The hub. Topology, fabric reference, and the command output behind every claim. Start here. |
| **[homelab-tacacs-aaa](https://github.com/117caseyallen-NetAdm/homelab-tacacs-aaa)** | Centralized device AAA. One TACACS+ server backed by Active Directory authenticates and authorizes all six devices across four vendors, with per-command accounting, a tested fail-safe matrix, and console break-glass verified on every box. |
| **[homelab-config-backup](https://github.com/117caseyallen-NetAdm/homelab-config-backup)** | Oxidized on the management VLAN backing up six devices — PAN-OS, Junos, IOS 15 and 12.1, EOS — to self-hosted Gitea, as a read-only TACACS+ service account. Hourly poll, commit on change, unattended push. |
| **[homelab-domain-services](https://github.com/117caseyallen-NetAdm/homelab-domain-services)** | AD DS, DNS, and DHCP. A single DHCP server addressing a remote subnet across OSPF and an IPsec tunnel, plus cross-site domain join. |
| **[homelab-wireguard](https://github.com/117caseyallen-NetAdm/homelab-wireguard)** | Routed, non-NATed WireGuard VPN. The client pool is redistributed into OSPF so it is reachable fleet-wide. |

## The lab

![CASEY-LAB topology](topology/CA-LAB-Topo.png)

| Layer | Design |
|---|---|
| **Routing** | Flat OSPF area 0 across a route-based IKEv2 IPsec tunnel (PA-440 ⇄ SRX345). Both firewalls inject default routes as Type-5 LSAs. |
| **Aggregation** | LACP between the firewalls, distribution switches, and the Arista — three bundles. Static EtherChannel to the Catalyst 2940, whose IOS image has no LACP support. |
| **Addressing** | Separate ranges for data, management (`10.99.x.x`), and transit (`10.255.x.x`). |
| **Access** | Dual-homed jumpboxes per site. Management access to network devices restricted to those jumpboxes and the management plane, enforced across four vendors. |
| **AAA** | TACACS+ on every device, backed by AD: named logins, group-based privilege, per-command accounting. Local accounts are break-glass only. |
| **Operations** | Every device's running config backed up hourly to self-hosted Git, committed only on change. One NTP authority for the fabric. Every server guest backed up nightly to a second machine. |

Claims on this page have [command output behind them](https://github.com/117caseyallen-NetAdm/casey-lab/blob/main/docs/verification.md) — including the device that took an hour to join the time hierarchy, and why the tool reporting it was the wrong one.

Physical hardware, not GNS3 or EVE-NG:

| | |
|:--:|:--:|
| ![The lab](photos/lab-rack-wide.jpg) | ![The lab, closer](photos/lab-rack-detail.jpg) |

## Working with

- **Network** — Palo Alto PAN-OS · Cisco IOS · Juniper Junos · Arista EOS
- **Routing & switching** — OSPF · IKEv2 IPsec · 802.1Q · LACP / EtherChannel · VLAN and SVI design · WireGuard
- **Network operations** — multi-vendor config backup (Oxidized) · self-hosted Git (Gitea) · NTP hierarchy design · management-plane access control · centralized syslog (rsyslog)
- **AAA** — TACACS+ (`tac_plus-ng`) · AD / LDAP integration · per-command authorization and accounting · break-glass design
- **Platform** — Proxmox VE · LXC · Windows Server · Active Directory · DNS · DHCP · Linux · systemd
- **Tooling** — PowerShell · Bash · Git

## Certifications

`JNCIA-SEC` · `JNCIA-Junos` · `AZ-700 Azure Network Engineer` · `CompTIA Security+` ·
`CompTIA CySA+` · `CompTIA Network+` · `CompTIA A+` · `ISC2 CC` ·
`AWS Cloud Practitioner` · `Splunk Core Certified User`

In progress: **CCNA**

## Next

NetBox as source of truth, SNMPv3 and monitoring (Telegraf, VictoriaMetrics,
Grafana), 802.1X, and a NetDevOps pipeline with Batfish validation. Detail in the
[hub roadmap](https://github.com/117caseyallen-NetAdm/casey-lab#roadmap).

## Connect

[LinkedIn](https://www.linkedin.com/in/casey-allen-6612a7133)
