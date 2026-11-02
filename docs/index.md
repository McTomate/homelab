# Homelab-Dokumentation

**Dokumentationsstand:** 02.11.2026  
**Plattformen:** Proxmox VE 9.1, OPNsense, AdGuard Home, Windows Server 2022, Home Assistant

!!! abstract "Gesamtstatus zum 02.11.2026"
    Netzwerk- und Virtualisierungsbasis funktionsfähig; Smart-Home-Teilprojekt abgeschlossen; Windows-/AD-Lab im Aufbau; Automatisierung, Storage und Backup als nächste Entwicklungsbereiche vorgesehen.

## Ziel des Homelabs

Das Homelab dient dem Aufbau einer virtualisierten, segmentierten und möglichst realitätsnahen IT-Infrastruktur, die sich an den Anforderungen einer kleinen bis mittelständischen Unternehmensumgebung orientiert.

Die Umgebung verfolgt mehrere Ziele:

- Aufbau und Administration einer strukturierten Netzwerkarchitektur mit VLANs.
- Umsetzung eines restriktiven Firewall- und Berechtigungskonzepts.
- Bereitstellung zentraler Serverdienste unter Linux und Windows.
- Einrichtung einer Active-Directory-Testumgebung.
- Erlernen von Virtualisierung, Automatisierung und Infrastructure as Code.
- Aufbau einer sicheren Remote-Access-Infrastruktur.
- Überwachung der Infrastruktur durch zentrale Monitoring-Dienste.
- Integration von Smart-Home-Geräten unter Berücksichtigung der Netzwerksicherheit.
- Umsetzung einer geeigneten Backup- und Wiederherstellungsstrategie.

Bei der Softwareauswahl werden möglichst kostenlose Lösungen beziehungsweise Community-Editionen bevorzugt.

## Eingesetzte Technologien

| Bereich | Technologie |
|---|---|
| Virtualisierung | Proxmox VE |
| Firewall und Routing | OPNsense |
| Switching | UGREEN Managed Switch |
| WLAN | TP-Link Access Point |
| DNS-Filterung | AdGuard Home |
| DHCP und Infrastruktur-DNS | OPNsense / dnsmasq |
| Windows-Domäne | Active Directory Domain Services |
| Windows-DNS | Windows Server DNS |
| Netzwerküberwachung | Uptime Kuma |
| Smart Home | Home Assistant |
| IoT-Protokolle | Matter, IPv6, mDNS |
| VPN | WireGuard |
| Passwortverwaltung | Vaultwarden |
| Automatisierung | Ansible |
| Storage und Backup | In Planung beziehungsweise Erweiterung |

## Zusammenfassung des Projektstands

Das Homelab hat sich seit dem 12.10.2026 deutlich weiterentwickelt.

Die grundlegende Infrastruktur für Routing, VLAN-Segmentierung, Virtualisierung, DNS, WLAN und sicheren externen Zugriff ist vorhanden.

Mit Home Assistant wurde außerdem eine VLAN-übergreifende IoT-Infrastruktur einschließlich IPv6, Matter, mDNS, zentraler Steuerung und Monitoring-Integration erfolgreich umgesetzt.

Das Windows-Lab stellt den nächsten Schwerpunkt dar. Mit VLAN 70 und dem ersten Windows Server 2022 wurde die technische Grundlage geschaffen. Der weitere Ausbau konzentriert sich auf Active Directory, DNS, Clientverwaltung, Gruppenrichtlinien und Automatisierung.

Langfristig soll aus dem Homelab eine vollständige, dokumentierte und reproduzierbare Testumgebung entstehen, mit der sich typische Aufgaben der Systemadministration, Netzwerkadministration und IT-Sicherheit praktisch durchführen lassen.
