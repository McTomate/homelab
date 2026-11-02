# Hardwareinventar

## Aktive Infrastruktur

| Gerät | Technische Daten | Aufgabe | Status |
|---|---|---|---|
| N150 Mini-PC | Intel N150, 8 GB RAM, 2 × RJ45 | OPNsense Firewall | Aktiv |
| Lenovo ThinkCentre | Intel Core i5-6500, 4C/4T, 32 GB RAM | Proxmox-Host | Aktiv |
| UGREEN CM933 | Managed Switch, 5 Ports | VLAN-Switching | Aktiv |
| TP-Link TL-7AP5100HC-PoE/DC | Access Point | WLAN und SSIDs | Aktiv |
| Speedport | Telekom-Router | Internet-Uplink | Aktiv |
| MacBook Air 2013 | Intel i5, 4 GB RAM | Linux-/Ansible-Control-Node | Vorbereitet |
| Desktop-PC | VLAN 10 | Management-Client | Aktiv |

## Weitere Geräte

| Gerät | Verwendung | Status |
|---|---|---|
| HP Notebook, Ryzen 3 3200U, 8 GB | Zusätzlicher Client/Testrechner | Verfügbar |
| Sony Vaio, Intel i3-3227U, 4 GB | Linux- oder Testsystem | Verfügbar |
| Lenovo Tab M10 Gen 3 | Home-Assistant-Dashboard | Aktiv |
| Samsung-TV | AirPlay und SmartThings | Aktiv |
| Smartphone | WLAN, WireGuard, HA-Benachrichtigungen | Aktiv |

## Datenträger

Dokumentierter Hardwarebestand des Proxmox-Hosts:

- Zwei SSDs mit jeweils ungefähr 256 GB.
- Eine HDD mit ungefähr 1 TB.
- Zusätzliche SSDs mit 500 GB und 256 GB wurden für eine mögliche Erweiterung vorgesehen.

Die tatsächliche Zuordnung der Datenträger zu Proxmox-Storage, freiem Speicher und möglichen Zusatzlaufwerken muss vor einer Neuplanung anhand von `lsblk`, SMART und der Proxmox-Storage-Übersicht abgeglichen werden.

## Geplanter Hardwareausbau

- Separates NAS für zentrale Daten und Backups.
- Optional zusätzliche Speicherkapazität für VM- und Container-Datenträger.
- Gegebenenfalls leistungsfähigere Virtualisierungshardware.
- Optional eine weitere Backup-Zielhardware zur besseren Ausfallsicherheit.
