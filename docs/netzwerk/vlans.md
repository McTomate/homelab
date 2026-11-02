# VLAN- und IP-Adresskonzept

## Eingerichtete Netzsegmente

| VLAN / Segment | Bezeichnung | Subnetz | Gateway | Status |
|---|---|---|---|---|
| 10 | MGMT | `10.10.10.0/24` | `10.10.10.1` | Aktiv |
| 20 | SERVER | `10.10.20.0/24` | `10.10.20.1` | Aktiv |
| 40 | CLIENT/WLAN | `10.10.40.0/24` | `10.10.40.1` | Aktiv |
| 50 | IOT | `10.10.50.0/24` | `10.10.50.1` | Aktiv |
| 60 | GUEST | `10.10.60.0/24` | `10.10.60.1` | Eingerichtet |
| 70 | LAB | `10.10.70.0/24` | `10.10.70.1` | Aktiv |
| – | APMGMT | `10.10.11.0/24` | Separates Managementsegment | Aktiv |
| – | WireGuard | `10.10.90.0/24` | VPN-Tunnel | Aktiv |

Das AP-Managementnetz ist separat zu betrachten und darf nicht mit einem bereits vorhandenen VLAN 11 gleichgesetzt werden, solange dessen genaue Switch- und OPNsense-Zuordnung nicht dokumentiert ist.

## Nicht eingerichtete VLANs

**VLAN 30:** Ursprünglich für kabelgebundene Clients vorgesehen, jedoch bisher nicht als produktives Segment bestätigt.

**VLAN 80:** Nicht eingerichtet.

**VLAN 90:** Nicht eingerichtet. Die entsprechende IP-Range ist für WireGuard reserviert.

## Segmentierungsprinzip

**MGMT – VLAN 10**

Enthält zentrale Verwaltungsoberflächen und Infrastrukturkomponenten. Zugriffe sollen auf vertrauenswürdige Administratorgeräte beschränkt bleiben.

**SERVER – VLAN 20**

Beinhaltet zentrale Anwendungen wie DNS, Monitoring, Passwortmanager und Home Assistant. Server erhalten nur die benötigten ausgehenden Verbindungen.

**CLIENT/WLAN – VLAN 40**

Enthält reguläre Endgeräte. Für den Zugriff auf Ressourcen anderer VLANs werden gezielte Freigaben benötigt.

**IOT – VLAN 50**

Beinhaltet Geräte mit begrenzter Administrierbarkeit oder geringerem Vertrauensniveau. Der Zugriff auf Management- und Servernetze wird grundsätzlich eingeschränkt.

**GUEST – VLAN 60**

Für nicht vertrauenswürdige Gäste vorgesehen. Ziel ist ausschließlich benötigter Internetzugriff ohne Zugriff auf interne Ressourcen. Die vollständige Durchsetzung dieser Vorgabe ist bei Bedarf erneut zu testen.

**LAB – VLAN 70**

Abgeschottete Testumgebung für Active Directory, Windows-Clients, Linux-Server und Automatisierung. Das Lab soll keine unkontrollierten Zugriffe auf das produktive Managementnetz erhalten.

## Systeminventar

### Infrastruktur

| System | DNS-Name | Adresse | Segment |
|---|---|---|---|
| OPNsense | `fw01.home.arpa` | `10.10.10.1` | MGMT |
| Managed Switch | `sw01.home.arpa` | `10.10.10.2` | MGMT |
| Proxmox | `pve.home.arpa` | `10.10.10.10` | MGMT |

### Server und Dienste

| Dienst | DNS-Name | Adresse | VLAN |
|---|---|---|---|
| AdGuard Home | `adguard.home.arpa` | `10.10.20.31` | 20 |
| Uptime Kuma | Noch zu dokumentieren | `10.10.20.40` | 20 |
| OpenSpeedTest | Noch zu dokumentieren | `10.10.20.50` | 20 |
| Vaultwarden | Noch zu dokumentieren | `10.10.20.70` | 20 |
| Home Assistant | `home-assistant.home.arpa` | `10.10.20.132` | 20 |
| LAB-DC01 | `LAB-DC01` | `10.10.70.10` | 70 |

Alle hier aufgeführten IPv4-Adressen wurden im bisherigen Aufbau verwendet. Ob jede Adresse bereits über eine statische Konfiguration oder DHCP-Reservierung abgesichert ist, sollte anhand von OPNsense und den einzelnen VMs überprüft werden.
