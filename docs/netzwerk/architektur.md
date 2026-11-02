# Physische Netzwerkarchitektur

## Netzwerkübersicht

```text
Internet
  → Speedport (192.168.2.1)
  → OPNsense / fw01 (WAN per DHCP)
  → OPNsense LAN-Trunk igc0
  → UGREEN CM933 / sw01
```

Am Managed Switch sind folgende Systeme angebunden:

| Port | Verbindung | Funktion |
|---|---|---|
| 1 | OPNsense | VLAN-Trunk |
| 2 | Reserve / später NAS | Noch keine endgültige Zuordnung |
| 3 | TP-Link Access Point | WLAN-VLANs und AP-Management |
| 4 | Proxmox-Host | VLAN-Trunk |
| 5 | Management-Desktop | Access VLAN 10 |

Die exakte Liste der getaggten VLANs und PVIDs sollte bei der nächsten Switch-Konfigurationssicherung exportiert werden.

## OPNsense als Netzwerkknoten

Die OPNsense-Firewall übernimmt:

- Inter-VLAN-Routing.
- Stateful Packet Filtering.
- DHCP-Dienste.
- DNS-Infrastrukturdienste über dnsmasq.
- Source NAT für Internetzugriffe.
- WireGuard-VPN.
- IPv6 Router Advertisements und zugehörige Firewallregeln.
- Steuerung erlaubter Verbindungen zwischen Netzsegmenten.

Das bisherige Bootstrap-Netz `192.168.1.0/24` wurde außer Betrieb genommen.

Das WAN befindet sich weiterhin hinter dem Speedport im Netz `192.168.2.0/24`. Dadurch ergibt sich für ausgehende IPv4-Verbindungen typischerweise eine doppelte NAT-Struktur.
