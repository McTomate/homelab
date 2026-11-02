# Projektplanung

## Priorität 1 – Windows Active Directory abschließen

- [ ] AD-Domäne verifizieren.
- [ ] Windows-DNS konfigurieren.
- [ ] Forwarder zu AdGuard einrichten.
- [ ] LAB-DHCP auf AD-DNS umstellen.
- [ ] DNS-SRV-Einträge überprüfen.
- [ ] Domänencontroller-Zustand mit `dcdiag` testen.
- [ ] Windows-11-Testclient bereitstellen.
- [ ] Client zur Domäne hinzufügen.

## Priorität 2 – Active Directory und Gruppenrichtlinien

- [ ] OU-Struktur entwickeln.
- [ ] Benutzer und Gruppen erstellen.
- [ ] AGDLP-Berechtigungskonzept umsetzen.
- [ ] Dateiserver installieren.
- [ ] NTFS- und Shareberechtigungen einrichten.
- [ ] Gruppenrichtlinien erstellen und testen.
- [ ] Anmelde- und DNS-Fehlerszenarien simulieren.

## Priorität 3 – Ansible-Automatisierung

- [ ] Linux-Testsystem bereitstellen.
- [ ] SSH-Zugriff einrichten.
- [ ] Ansible-Inventar erstellen.
- [ ] Erstes Playbook entwickeln.
- [ ] Automatisierte Softwareinstallation testen.
- [ ] Windows-Verwaltung mit Ansible evaluieren.
- [ ] Git-Repository für Automatisierung einrichten.

## Priorität 4 – Backup und Storage

- [ ] Datenträgerinventar aktualisieren.
- [ ] SSDs prüfen und geeignete Einsatzbereiche definieren.
- [ ] Proxmox-Backup-Ziel festlegen.
- [ ] Automatische Backups einrichten.
- [ ] Restore-Test einer VM oder eines Containers durchführen.
- [ ] NAS-Architektur planen.
- [ ] Optional Proxmox Backup Server bereitstellen.

## Priorität 5 – Netzwerk und Security

- [ ] Finale Switch-Portkonfiguration dokumentieren.
- [ ] AP-Managementkonfiguration erfassen.
- [ ] DHCP-Bereiche und Reservierungen vervollständigen.
- [ ] Firewallregelwerk als Konfigurationsstand sichern.
- [ ] Nicht mehr verwendete Regeln identifizieren.
- [ ] Netzwerksegmentierung erneut gezielt testen.
- [ ] Optional OPNsense Insight/NetFlow evaluieren.
- [ ] Optional Suricata IDS testen.
- [ ] Optional Zenarmor untersuchen.

## Priorität 6 – Weitere Anwendungen

- [ ] Zentrale Infrastrukturmetriken erweitern.
- [ ] Jellyfin-Testsystem bereitstellen.
- [ ] NAS-Medienablage integrieren.
- [ ] Weitere Linux- und Windows-Testsysteme aufbauen.

## Offene Bestandsdaten

Die folgenden Informationen sollten bei Gelegenheit ergänzt werden, um die Dokumentation vollständig reproduzierbar zu machen.

| Information | Status |
|---|---|
| Vollständige Proxmox-VM-/CT-IDs | Offen |
| Proxmox-Storage- und Datenträgerzuordnung | Offen |
| Aktuelle SSD-SMART-Daten | Offen |
| Genaue Switch-Trunk-/PVID-Konfiguration | Offen |
| AP-Management-IP | Offen |
| SSID-Namen und Sicherheitsprofile | Offen |
| DHCP-Ranges für alle VLANs | Teilweise dokumentiert |
| Vollständige DNS-Upstream-Konfiguration | Offen |
| Firewallregelwerk mit Reihenfolge | Teilweise dokumentiert |
| Tatsächlicher AD-Domänenname | Noch zu verifizieren |
| LAB-DC01 DNS- und AD-Health-Check | Offen |
| Off-Host-Backup und Restore-Nachweis | Offen |
| Monitoring-Inventar | Teilweise dokumentiert |
