# Homelab

Virtualisierte, segmentierte Testumgebung nach dem Vorbild einer kleinen bis mittelständischen Unternehmens-IT. Sie dient dazu, Netzwerk- und Firewall-Konzepte, Linux- und Windows-Server sowie Automatisierung praktisch umzusetzen. Wo möglich, kommen kostenlose Lösungen und Community-Editionen zum Einsatz.

**Stand:** 04.11.2026

## Highlights

- **6 VLANs** mit restriktivem Firewall-Konzept auf OPNsense: Management, Server, Clients, IoT, Gäste und Lab
- **Smart Home über VLAN-Grenzen:** Matter über IPv6 und mDNS zwischen Server- und IoT-Netz
- **WireGuard-VPN mit minimalen Rechten:** nur ausgewählte Dienste, keine Admin-Oberflächen
- **Monitoring:** Uptime Kuma meldet Ausfälle über Home Assistant aufs Smartphone
- **Active-Directory-Lab:** Domäne mit Dateiserver, AGDLP-Berechtigungen, Gruppenrichtlinien und Windows LAPS in einem isolierten VLAN

## Netzwerkplan

```mermaid
flowchart TB
    internet((Internet)) --- speedport[Speedport]
    speedport --- fw[OPNsense fw01<br>Routing · Firewall · DHCP]
    vpn([WireGuard-Clients<br>10.10.90.0/24]) -. VPN .-> fw
    fw ===|Trunk| sw[Managed Switch sw01]
    sw ---|VLAN 10| desk[Admin-Desktop]
    fw ===|VLAN 40/50/60| ap
    sw ===|Trunk| pve

    subgraph pve[Proxmox-Host]
        subgraph v20[VLAN 20 · SERVER]
            svc[AdGuard Home<br>Uptime Kuma<br>Vaultwarden<br>OpenSpeedTest]
            ha[Home Assistant]
        end
        subgraph v70[VLAN 70 · LAB]
            lab[LAB-DC01<br>LAB-SRV01<br>LAB-W11]
        end
    end

    subgraph ap[Access Point]
        w40[VLAN 40 · Clients]
        w50[VLAN 50 · IoT<br>TV, Lampen]
        w60[VLAN 60 · Gäste]
    end

    ha -. Matter / IPv6 .- w50
```

## Technologien

| Bereich | Technologie |
|---|---|
| Virtualisierung | Proxmox VE 9.1 |
| Firewall, Routing, DHCP, VPN | OPNsense mit dnsmasq und WireGuard |
| Netzwerk | UGREEN Managed Switch, TP-Link Access Point |
| DNS | AdGuard Home, Windows Server DNS |
| Windows | Windows Server 2022, Windows 11, Active Directory, Gruppenrichtlinien, Windows LAPS |
| Monitoring | Uptime Kuma |
| Smart Home | Home Assistant, Matter |
| Passwortverwaltung | Vaultwarden |
| Automatisierung | Ansible (im Aufbau) |

## Status

| Bereich | Stand |
|---|---|
| Netzwerk und Virtualisierung | ✅ funktionsfähig |
| Smart Home | ✅ abgeschlossen am 01.11.2026 |
| Windows-AD-Lab | ✅ Grundkonfiguration abgeschlossen am 04.11.2026 |
| Ansible, Storage, Backup | 📋 geplant |
