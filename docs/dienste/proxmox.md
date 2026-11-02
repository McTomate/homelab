# Proxmox VE

## Hostkonfiguration

| Eigenschaft | Wert |
|---|---|
| Hostname | `pve` |
| IP | `10.10.10.10/24` |
| Gateway | `10.10.10.1` |
| CPU | Intel Core i5-6500 |
| CPU-Kerne / Threads | 4 / 4 |
| RAM | 32 GB |
| Betriebssystem | Proxmox VE 9.1 |
| PVE-Manager | 9.1.1 |
| Linux-Kernel | 6.17.2-1-pve |
| Bridge | `vmbr0`, VLAN-aware |

## Netzwerkanbindung

Der Host wird über Port 4 des UGREEN-Switches angebunden. Seine VLAN-aware Bridge ermöglicht den direkten Anschluss von VMs und Containern an unterschiedliche VLANs.

Die Trunk-Verbindung transportiert inzwischen nicht mehr ausschließlich VLAN 10 und VLAN 20, sondern auch die für die Windows-Lab-VM benötigte VLAN-70-Verbindung.

Für virtuelle Gäste kann der VLAN-Tag direkt am virtuellen Netzwerkadapter festgelegt werden.

## Virtuelle Maschinen und Container

| System | ID | Typ | VLAN | Status |
|---|---|---|---|---|
| AdGuard Home | Zu erfassen | LXC | 20 | Aktiv |
| Uptime Kuma | Zu erfassen | Dienst/Container | 20 | Aktiv |
| OpenSpeedTest | Zu erfassen | CT | 20 | Aktiv |
| Vaultwarden | Zu erfassen | Dienst/Container | 20 | Aktiv |
| Home Assistant | 200 | VM | 20 | Aktiv |
| LAB-DC01 | 300 | VM | 70 | Aktiv |

Die fehlenden VM-/CT-IDs können über die Proxmox-Oberfläche oder die Befehle `qm list` und `pct list` nachgetragen werden.

## Ressourcenplanung

Der Proxmox-Host eignet sich für mehrere kleinere Serverdienste und eine begrenzte Windows-Testumgebung.

Die CPU mit vier Kernen ohne Hyper-Threading bildet jedoch bei mehreren gleichzeitig aktiven Windows-VMs einen möglichen Engpass.

Bei der Bereitstellung weiterer VMs sind insbesondere zu beachten:

- Gesamte Speicherauslastung.
- CPU-Ready-/CPU-Wartezeiten und Hostlast.
- Disk-I/O und freier Storage.
- Gleichzeitige Aktivität von Windows-Update, Defender und Hintergrunddiensten.
- Speicherbedarf und Performance von Home Assistant.

Für das Windows-Lab ist zunächst ein schrittweiser Ausbau zweckmäßig.
