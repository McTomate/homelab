# Dienste

## Proxmox-Host

| | |
|---|---|
| Version | Proxmox VE 9.1, Kernel 6.17.2-1-pve |
| Hardware | Intel Core i5-6500 (4C/4T), 32 GB RAM |
| Netzwerk | VLAN-aware Bridge `vmbr0`, Trunk mit VLAN 10, 20 und 70 |
| Adresse | `pve.home.arpa` (`10.10.10.10`) |

VMs und Container bekommen ihr VLAN direkt am virtuellen Netzwerkadapter. Die 4 Kerne ohne Hyper-Threading begrenzen, wie viele Windows-VMs gleichzeitig laufen können. Das Lab wird deshalb schrittweise ausgebaut.

## Übersicht

| Dienst | Typ | Adresse | VLAN |
|---|---|---|---|
| AdGuard Home | LXC | `10.10.20.31` | 20 |
| Uptime Kuma | Container | `10.10.20.40` | 20 |
| OpenSpeedTest | Container | `10.10.20.50` | 20 |
| Vaultwarden | Container | `10.10.20.70` | 20 |
| Home Assistant | VM 200 (HAOS, 2 vCPU, 4 GiB) | `10.10.20.132` | 20 |
| LAB-DC01 | VM 300 (Windows Server 2022, 2 vCPU, 4 GiB) | `10.10.70.10` | 70 |

## Monitoring

Uptime Kuma überwacht die Erreichbarkeit wichtiger Komponenten und Dienste. Statusänderungen gehen über Home Assistant als Push-Benachrichtigung aufs Smartphone. Meldungen bei Ausfall und Wiederherstellung sind getestet.
