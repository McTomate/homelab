# Roadmap

## 1. Windows-AD-Lab abschließen

Siehe [Nächste Schritte im Windows-AD-Lab](projekte/windows-ad.md#nachste-schritte).

## 2. Ansible-Automatisierung

Control Node: MacBook Air mit Ubuntu und Ansible Core 2.16.3

- [ ] Linux-Testsystem mit SSH-Zugriff bereitstellen
- [ ] Inventar und erstes Playbook erstellen (Updates, Softwareinstallation)
- [ ] Playbooks in Git versionieren, Ansible Vault einsetzen
- [ ] Windows-Verwaltung über WinRM testen

## 3. Backup und Storage

Ziel ist eine 3-2-1-Strategie. Snapshots ersetzen keine Backups.

- [ ] Datenträger inventarisieren, SSDs per SMART und Temperaturtest prüfen
- [ ] Backup-Ziel festlegen, automatische Proxmox-Backups einrichten
- [ ] Restore einer VM testen
- [ ] NAS planen, optional Proxmox Backup Server

## 4. Netzwerk und Security

- [ ] Konfigurationen von OPNsense, Switch und Access Point exportieren und sichern
- [ ] DHCP-Bereiche, Reservierungen und Switch-VLANs vollständig dokumentieren
- [ ] Ungenutzte Firewallregeln entfernen, Segmentierung erneut testen (u. a. Gästenetz)
- [ ] Optional: Suricata IDS, Zenarmor, NetFlow

## 5. Weitere Dienste

- [ ] Monitoring erweitern: Proxmox-Ressourcen, SMART, Zertifikate, Backup-Status
- [ ] Jellyfin-Medienserver nach dem NAS
