# Windows-Server-Lab (VLAN 70)

## Projektziel

Das Windows-Lab soll eine eigenständige kleine Unternehmensdomäne simulieren.

Geplant sind insbesondere:

- Active Directory Domain Services.
- Zentrale DNS-Namensauflösung.
- Windows-Clientverwaltung.
- Gruppenrichtlinien.
- Benutzer-, Gruppen- und Rechteverwaltung.
- Dateifreigaben.
- PowerShell-Administration.
- Ansible-Automatisierung.

Das Lab verwendet VLAN 70 und bleibt vom produktiven Infrastruktur-Management getrennt.

## Netzwerkkonfiguration

| Parameter | Wert |
|---|---|
| VLAN | 70 |
| Name | LAB |
| Netzwerk | `10.10.70.0/24` |
| Gateway | `10.10.70.1` |
| DHCP | `10.10.70.100–199` |
| Domänencontroller | `10.10.70.10` |
| IPv6 | Nicht eingerichtet |
| Internetzugriff | Erlaubt |
| MGMT-Zugriff | Eingeschränkt |

## LAB-DC01

Die erste VM wurde erfolgreich installiert.

| Eigenschaft | Wert |
|---|---|
| VM-ID | 300 |
| Hostname | `LAB-DC01` |
| Betriebssystem | Windows Server 2022 |
| Installation | Desktop Experience |
| vCPU | 2 |
| RAM | 4 GiB |
| Systemdisk | 64 GiB |
| Netzwerk | `vmbr0`, VLAN 70 |
| IPv4 | `10.10.70.10/24` |
| Gateway | `10.10.70.1` |

Die VirtIO-Treiber wurden eingerichtet und die Netzwerkverbindung getestet.

## Durchgeführte Konfiguration

Abgeschlossen:

- Windows Server 2022 installiert.
- VirtIO-Treiber eingerichtet.
- Rechnernamen auf LAB-DC01 geändert.
- Statische IPv4-Adresse konfiguriert.
- Gateway eingerichtet.
- Internetzugriff getestet.
- DNS-Auflösung über AdGuard getestet.
- Zeitzone auf W. Europe Standard Time korrigiert.
- Zugriff auf die Proxmox-Managementoberfläche aus dem LAB-VLAN erfolgreich blockiert.
- Active Directory Domain Services installiert.
- Server zum ersten Domänencontroller heraufgestuft.

## Active-Directory-Konzept

Für die neue Gesamtstruktur wurde folgende isolierte Testdomäne vorgesehen:

| Eigenschaft | Wert |
|---|---|
| AD-Domäne | `lab.test` |
| NetBIOS-Name | `LAB` |
| Erster DC | `LAB-DC01` |
| DNS-Server | `10.10.70.10` |

Der tatsächliche AD-Domänenname und der Zustand der DNS-Registrierungen sollen nach der Heraufstufung noch verifiziert werden.

## Offene DNS-Konfiguration

Zum letzten bekannten Zeitpunkt stand die endgültige Integration des Windows-DNS-Dienstes noch aus.

Notwendige Schritte:

1. Installierte AD-Domäne überprüfen.
2. Funktionsfähigkeit des Windows-DNS-Dienstes prüfen.
3. DNS-Client-Konfiguration von LAB-DC01 auf den eigenen DNS-Dienst `10.10.70.10` umstellen.
4. DNS-Forwarder auf AdGuard `10.10.20.31` konfigurieren.
5. DHCP-Option 6 im LAB-VLAN auf `10.10.70.10` umstellen.
6. Domänenspezifische DNS-SRV-Einträge kontrollieren.
7. Firewall-Kommunikation zwischen LAB-DC01 und AdGuard prüfen.
8. Namensauflösung interner und externer Ziele testen.

## Empfohlene Prüfkommandos

**Active Directory**

```powershell
Get-ADDomain
Get-ADForest
dcdiag /v
```

**DNS**

```powershell
Get-DnsServerForwarder
Get-DnsServerZone
Resolve-DnsName lab.test
Resolve-DnsName -Type SRV _ldap._tcp.dc._msdcs.lab.test
```

**Clientkonfiguration**

```powershell
ipconfig /all
ipconfig /registerdns
nslookup lab.test 10.10.70.10
```

## Geplante Windows-Lab-Erweiterung

| System | Rolle | Status |
|---|---|---|
| LAB-DC01 | Domain Controller, DNS | Installiert |
| WIN11-01 | Windows 11 Domänenclient | Geplant |
| LAB-FS01 | Dateiserver | Geplant |
| Weiterer Linux-Server | SSH, Automatisierung, Dienste | Geplant |

Der Windows-11-Client soll als Nächstes der Domäne beitreten.

Anschließend können Benutzer, Sicherheitsgruppen, OUs und Gruppenrichtlinien erstellt und getestet werden.

## Geplante Active-Directory-Übungen

- OU-Struktur entwerfen.
- Benutzer- und Gruppenkonten anlegen.
- Globale und domänenlokale Gruppen einsetzen.
- AGDLP-Prinzip umsetzen.
- NTFS- und Freigabeberechtigungen konfigurieren.
- GPO-Vererbung und Prioritäten testen.
- Administrative Vorlagen verwenden.
- Passwort- und Kontosperrrichtlinien untersuchen.
- Netzlaufwerke über GPO zuweisen.
- PowerShell-Skripte für die Benutzerverwaltung entwickeln.
- DNS-, Kerberos- und Anmeldeprobleme gezielt simulieren.
