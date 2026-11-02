# Netzwerk

!!! warning "Diese Doku ist öffentlich"
    **Nie** hier rein: Passwörter, API-Keys, WireGuard-Schlüssel, deine öffentliche IP,
    DynDNS-Adressen oder welche Ports nach außen offen sind.
    Schreib nur, *wo* Zugangsdaten liegen (z. B. „Bitwarden → Homelab → Proxmox“).
    Interne IPs wie `192.168.x.x` sind unkritisch, die sind von außen nicht erreichbar.

## Übersicht

| Netz / VLAN | Bereich | Zweck |
|---|---|---|
| Heimnetz | 192.168.1.0/24 | PCs, Handys |
| Server | 192.168.10.0/24 | Homelab-Dienste |

## Wichtige Adressen

| Gerät | IP | Erreichbar über |
|---|---|---|
| Router | 192.168.1.1 | Weboberfläche |
| server-01 | 192.168.10.10 | `https://192.168.10.10:8006` |
