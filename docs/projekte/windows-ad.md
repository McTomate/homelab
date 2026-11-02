# Windows-AD-Lab

**Status:** im Aufbau

Ziel ist eine kleine Unternehmensdomäne zum Üben von Active Directory, DNS, Gruppenrichtlinien, Rechteverwaltung und PowerShell.

## Umgebung

| | |
|---|---|
| Netz | VLAN 70, `10.10.70.0/24`, DHCP `.100–.199` |
| Domänencontroller | LAB-DC01: Windows Server 2022, VM 300, 2 vCPU, 4 GiB RAM, 64 GiB |
| Domäne | `lab.test` (NetBIOS `LAB`) |
| Isolation | Internet erlaubt, Management-VLAN gesperrt |

## Erledigt

- Windows Server 2022 mit VirtIO-Treibern und statischer IP installiert
- Internet und DNS-Auflösung über AdGuard getestet
- AD DS installiert und den Server zum ersten Domänencontroller heraufgestuft
- Sperre zur Proxmox-Oberfläche aus dem Lab getestet

## DNS-Konzept

```text
Domänenclient (VLAN 70) → Windows-DNS auf LAB-DC01 → AdGuard Home als Forwarder
```

- Die Infrastruktur-Domain `home.arpa` und die AD-Domain `lab.test` bleiben getrennt.
- Zwischen AdGuard und dem Domänencontroller darf keine DNS-Schleife entstehen.

## Nächste Schritte

- [ ] DNS auf LAB-DC01 umstellen, Forwarder zu AdGuard einrichten
- [ ] DHCP-Option 6 im Lab auf `10.10.70.10` setzen
- [ ] Zustand prüfen mit `dcdiag /v` und den SRV-Einträgen
- [ ] Windows-11-Client in die Domäne aufnehmen
- [ ] OU-Struktur, Benutzer und Gruppen nach AGDLP anlegen
- [ ] Dateiserver mit NTFS- und Freigabeberechtigungen aufsetzen
- [ ] Gruppenrichtlinien testen, z. B. Netzlaufwerke per GPO
- [ ] DNS-, Kerberos- und Anmeldefehler gezielt simulieren
