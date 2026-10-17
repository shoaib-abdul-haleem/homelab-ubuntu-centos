# 🖥️ homelab-ubuntu-centos

> A two-server virtual lab for learning Linux administration and networking, built on Oracle VirtualBox.

```text
LAB AT A GLANCE
────────────────────────────────────────────────
Hypervisor : Oracle VM VirtualBox
Servers    : Ubuntu_Server, Centos_Server
RAM        : 2 GB each
Disk       : 25 GB (Ubuntu), 20 GB (CentOS)
Networking : NAT (internet) + Host-only (internal)
────────────────────────────────────────────────
```

## Why I built this

Real company infrastructure rarely runs one operating system. This lab gives me a small mixed environment (Debian-based and RHEL-based) where I can practice the daily work of system integration: connecting machines, configuring networks, and fixing things when they break.

## Architecture

```text
                    Internet
                       │
                      NAT
           ┌───────────┴───────────┐
           │                       │
    Ubuntu_Server            Centos_Server
           │                       │
           └─── Host-only network ─┴─── Host PC
```

| Adapter | Type | Purpose |
|---|---|---|
| 1 | NAT | Internet access for updates and downloads |
| 2 | Host-only | Private network for SSH and VM-to-VM traffic |

## Machines

| | Ubuntu_Server | Centos_Server |
|---|---|---|
| Family | Debian-based (apt) | RHEL-based (yum/dnf) |
| RAM | 2 GB | 2 GB |
| Disk | 25 GB | 20 GB |
| Extras | Guest Additions, `before-docker` snapshot | — |

## Done so far

- [x] Created both VMs in VirtualBox
- [x] Configured NAT + Host-only adapters on each
- [x] Installed Guest Additions on Ubuntu
- [x] Took a snapshot before Docker experiments (safe rollback)

## Up next

- [ ] Static IP configuration on both VMs
- [ ] Internal DNS resolution between the servers
- [ ] SSH key-based login, password login disabled
- [ ] Cross-distro Bash script for user provisioning
- [ ] Basic monitoring

## Key takeaways

- NAT and Host-only serve different purposes, so using both gives internet access and a private lab network.
- Snapshots make it safe to try risky changes like installing Docker.
- apt and yum/dnf do the same job with different commands.
