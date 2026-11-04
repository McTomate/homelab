# Windows-AD-Lab

**Status:** Grundkonfiguration abgeschlossen und getestet (04.11.2026)

Isolierte Windows-Unternehmensumgebung mit eigener AD-Domäne zum Üben von Windows Server, Active Directory, DNS, Gruppenrichtlinien, Dateidiensten und IT-Sicherheit.

## Umgebung

| | |
|---|---|
| Netz | VLAN 70, `10.10.70.0/24`, DHCP `.100–.199` über OPNsense |
| Domäne | `lab.test` (NetBIOS `LAB`), Funktionsebene Windows Server 2016 |
| DNS | Windows-DNS auf LAB-DC01, externe Namen über AdGuard Home |
| Firewall | DNS zu AdGuard und Internet erlaubt, alle anderen privaten Netze gesperrt |

| VM | System | RAM | Rolle | Adresse |
|---|---|---|---|---|
| 300 · LAB-DC01 | Windows Server 2022 | 6 GB | DC, DNS, Global Catalog | `10.10.70.10` |
| 301 · LAB-W11 | Windows 11 Enterprise | 8 GB | Domänenclient | DHCP |
| 302 · LAB-SRV01 | Windows Server 2022 | 4 GB | SMB-Dateiserver | `10.10.70.11` |

Alle VMs laufen mit VirtIO-Treibern, QEMU Guest Agent und aktuellem Patchstand.

## Benutzer, Gruppen und Freigaben

OUs: `Clients`, `Servers`, `Users`, `Groups`, `ServiceAccounts`. Testbenutzer gibt es für IT, Personal und Vertrieb. Berechtigungen werden nach **AGDLP** vergeben:

```text
Benutzer → GG_<Abteilung> (global) → DL_FS_<Abteilung>_M (domänenlokal) → Freigabe
```

| Freigabe | Gruppen | Laufwerk |
|---|---|---|
| `\\LAB-SRV01\IT` | GG_IT → DL_FS_IT_M | `I:` |
| `\\LAB-SRV01\Personal` | GG_Personal → DL_FS_Personal_M | `P:` |
| `\\LAB-SRV01\Vertrieb` | GG_Vertrieb → DL_FS_Vertrieb_M | `V:` |

- NTFS *Modify* und SMB *Change* für die DL-Gruppe, Administratoren und SYSTEM *Full Control*
- Access-Based Enumeration aktiv
- **Getestet:** Berechtigte Benutzer können lesen und schreiben, andere erhalten keinen Zugriff. Nach Entzug der Gruppenmitgliedschaft und neuer Anmeldung sind die Rechte weg.

## Gruppenrichtlinien

| GPO | Wirkung |
|---|---|
| GPO-USER-DriveMaps | Netzlaufwerke je nach Gruppe (Item-Level Targeting), Entfernen nach Gruppenwechsel |
| GPO-COMPUTER-WindowsLAPS | Lokales Administratorkennwort über Windows LAPS |
| GPO-COMPUTER-AutoLock-10min | Bildschirmsperre nach 10 Minuten |
| GPO-USER-Taskbar-PowerShell | PowerShell an die Taskleiste anheften |

## Windows LAPS

Das Kennwort des lokalen Administratorkontos auf den Clients verwaltet Windows LAPS: 20 Zeichen, Wechsel alle 30 Tage, verschlüsselt in Active Directory gespeichert. Dafür wurde das AD-Schema erweitert, und die Computerobjekte der OU `Clients` haben Schreibrechte erhalten.

**Getestet:** GPO-Verarbeitung, Speicherung in AD, Abruf über die AD-Verwaltung und manuelle Rotation.

## Nächste Schritte

- [ ] Windows Server Backup mit System-State-Sicherung und Restore-Tests
- [ ] Zweiter Domänencontroller mit AD- und DNS-Replikation
- [ ] Lokale Administratorgruppen zentral verwalten, weitere GPO-Härtung
- [ ] AD-Verwaltung per PowerShell
- [ ] Linux-Server und Ansible einbinden
