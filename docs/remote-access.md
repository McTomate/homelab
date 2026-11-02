# Remote Access

WireGuard läuft auf OPNsense und ist per DDNS erreichbar. Das Tunnelnetz ist `10.10.90.0/24`. Der Zugriff über das Mobilfunknetz ist getestet.

## Minimale Rechte

VPN-Clients erreichen nur die Dienste, die unterwegs gebraucht werden:

| Ziel | Zugriff |
|---|---|
| AdGuard Home | ✅ erlaubt |
| Vaultwarden | ✅ erlaubt |
| Home Assistant | ✅ erlaubt |
| Proxmox | ❌ gesperrt |
| Managed Switch | ❌ gesperrt |
| Access Point | ❌ gesperrt |

Admin-Oberflächen werden erst freigegeben, wenn ein konkreter Bedarf besteht. Schlüssel, Port und Hostname sind getrennt und nicht öffentlich dokumentiert.
