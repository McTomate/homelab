# Sicherheits- und Betriebsstandards

## Grundsätze

Für den weiteren Ausbau sollen folgende Standards gelten:

- Verwaltungsoberflächen nur für berechtigte Systeme.
- Keine unnötigen VLAN-übergreifenden Freigaben.
- Eigene Dienstkonten, wo sinnvoll.
- Zentrale und nachvollziehbare DNS-Konfiguration.
- Feste beziehungsweise reservierte Serveradressen.
- Regelmäßige Updates.
- Getrennte Sicherung von Konfigurationen und Nutzdaten.
- Dokumentation aller Änderungen.
- Regelmäßige Prüfung von Firewall-Testregeln.
- Überwachung kritischer Infrastruktur.

## Konfigurationssicherung

Wichtige zu sichernde Konfigurationen:

| System | Sicherungsinhalt |
|---|---|
| OPNsense | Firewall, Interfaces, DHCP, VPN, DNS |
| Proxmox | Host-Konfiguration, VM-/CT-Backups |
| Managed Switch | VLAN- und Portkonfiguration |
| Access Point | SSIDs, VLAN-Zuordnung, Management |
| AdGuard | DNS-Einstellungen, Filter, Rewrites |
| Home Assistant | HA-Backups und Automationen |
| Windows Server | System State / AD-relevante Sicherung |
| Ansible | Playbooks, Inventar, Konfiguration |

Die tatsächliche Umsetzung dieser Sicherungen ist teilweise noch offen und darf nicht mit einer bereits vorhandenen Backup-Strategie gleichgesetzt werden.

## Dokumentationsstandard

Bei jeder zukünftigen Änderung sollten dokumentiert werden:

- Datum.
- Betroffenes System.
- Ursprünglicher Zustand.
- Durchgeführte Änderung.
- Technischer Grund.
- Testergebnis.
- Eventuell entstandene offene Aufgaben.
- Rückfallplan bei sicherheitsrelevanten Änderungen.
