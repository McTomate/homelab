# Firewall- und Sicherheitskonzept

## Sicherheitsprinzip

Die Netzwerksicherheit basiert auf Stateful Filtering und Netzwerksegmentierung.

Verbindungen sollen grundsätzlich nur dort zugelassen werden, wo sie funktional notwendig sind.

Für restriktiv konfigurierte Netze gilt:

1. Notwendige Infrastruktur-Dienste explizit erlauben.
2. Gezielte dienstbezogene Zugriffe auf andere VLANs erlauben.
3. Unerwünschten Zugriff auf interne Netzbereiche blockieren.
4. Erforderlichen Internetverkehr zulassen.
5. Übrigen Verkehr gemäß gewünschter Richtlinie blockieren.

Dabei ist die tatsächliche Reihenfolge der OPNsense-Regeln entscheidend. Ein RFC1918-Block muss insbesondere vor allgemeinen Internet-Freigaben stehen, wenn diese nicht bereits selbst auf öffentliche Zielnetze begrenzt sind.

## SERVER-VLAN

Dokumentierte Freigaben umfassen unter anderem:

| Quelle | Ziel | Dienst |
|---|---|---|
| SERVER | OPNsense | DNS TCP/UDP 53 |
| SERVER | OPNsense | NTP UDP 123 |
| SERVER | OPNsense | ICMP |
| SERVER | Internet | HTTP 80 |
| SERVER | Internet | HTTPS 443 |
| SERVER | Internet | ICMP |

Weitere dienstbezogene Freigaben, insbesondere für Home Assistant und Matter, wurden separat ergänzt.

## Managementschutz

Administrative Oberflächen von OPNsense, Proxmox und Switch sollen nur von ausdrücklich autorisierten Geräten erreicht werden.

Ein bereits verifiziertes Sicherheitsprinzip ist die Trennung zwischen dem LAB-VLAN und MGMT.

Der Windows-Lab-Server kann auf benötigte Dienste zugreifen, während ein Zugriff auf die Proxmox-Managementoberfläche aus VLAN 70 blockiert wurde.

## IoT-Segmentierung

Das IoT-VLAN wird für weniger vertrauenswürdige Geräte verwendet.

Funktional notwendige Freigaben betreffen insbesondere:

- Home Assistant und Matter.
- AirPlay zum Samsung-TV.
- SmartThings-Steuerung.
- Druckzugriffe auf den Netzwerkdrucker.
- Erforderliche Internetdienste der IoT-Geräte.

Die Regeln sollen so weit wie möglich auf einzelne Hosts, Protokolle und Ports eingeschränkt bleiben.

## WLAN-Client zum Netzwerkdrucker

Für den Zugriff eines WLAN-Clients im VLAN 40 auf den Netzwerkdrucker in VLAN 50 wurde eine hostbezogene OPNsense-Regel mit folgenden TCP-Ports angelegt:

| Port | Dienst |
|---|---|
| 515 | LPD/LPR |
| 631 | IPP |
| 9100 | Raw Printing / JetDirect |

Die erfolgreiche Druckausgabe selbst wurde noch nicht abschließend dokumentiert.

Eine direkte Druckereinrichtung über dessen IP-Adresse ist unabhängig von einer automatischen Bonjour-Erkennung möglich, soweit der Drucker das gewählte Druckprotokoll unterstützt.
