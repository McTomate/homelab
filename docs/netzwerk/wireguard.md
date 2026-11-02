# WireGuard und Remote Access

## VPN-Architektur

WireGuard wird auf OPNsense betrieben.

Das verwendete Tunnelnetz lautet `10.10.90.0/24`. Es handelt sich ausdrücklich nicht um ein VLAN.

Ein externer Zugriff über das Mobilfunknetz wurde erfolgreich getestet.

## Freigegebene interne Ressourcen

| Ziel | IP | Zugriff |
|---|---|---|
| AdGuard Home | `10.10.20.31` | Erlaubt |
| Vaultwarden | `10.10.20.70` | Erlaubt |
| Home Assistant | `10.10.20.132` | Erlaubt |
| Proxmox | `10.10.10.10` | Gesperrt |
| Managed Switch | `10.10.10.2` | Gesperrt |
| Access Point | Managementsegment | Gesperrt |

Die Einschränkung auf einzelne benötigte Dienste ist beabsichtigt.

## Sicherheit

Der Zugriff auf administrative Infrastruktur wird nicht pauschal durch den VPN-Tunnel freigegeben.

Das Konzept orientiert sich an minimalen Berechtigungen.

Weitere administrative VPN-Freigaben sollten erst erfolgen, wenn ein tatsächlicher Bedarf besteht.

## Externe Erreichbarkeit

Die Remote-Access-Lösung nutzt die vorhandene Speedport-/OPNsense-Infrastruktur und eine konfigurierte DDNS-Erreichbarkeit.

Die genauen Parameter für DNS-Hostname, WireGuard-Port, Peer-IPs und erlaubte Tunnelziele werden in einer separaten, zugriffsgeschützten Konfigurationsdokumentation geführt.

Private Schlüssel und Zugangsdaten werden nicht in der allgemeinen Homelab-Dokumentation abgelegt.
