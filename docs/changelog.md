# Änderungen seit dem 12.10.2026

| Bereich | Änderung | Status |
|---|---|---|
| Proxmox | Aktualisierung auf VE 9.1; Arbeitsspeicher auf 32 GB | Abgeschlossen |
| WLAN | Access Point in Betrieb genommen | Abgeschlossen |
| VLAN 40 | Internes Client-/WLAN-Netz eingerichtet | Abgeschlossen |
| VLAN 50 | IoT-Netz eingerichtet | Abgeschlossen |
| VLAN 60 | Gästenetz eingerichtet | Eingerichtet |
| VLAN 70 | Isoliertes Windows-/Linux-Labor eingerichtet | Abgeschlossen |
| WireGuard | Externer VPN-Zugriff mit eingeschränkten Berechtigungen | Abgeschlossen |
| Vaultwarden | Passwortmanager über VPN erreichbar | Abgeschlossen |
| Uptime Kuma | Monitoring und Benachrichtigungen | Abgeschlossen |
| Home Assistant | HAOS als Proxmox-VM eingerichtet | Abgeschlossen |
| Matter | Gerätekommunikation zwischen VLAN 20 und 50 | Abgeschlossen |
| AirPlay | Kommunikation zum Samsung-TV über VLAN-Grenzen | Abgeschlossen |
| SmartThings | Steuerung des Samsung-TV | Abgeschlossen |
| Dashboard | Lenovo Tab M10 Gen 3 eingerichtet | Abgeschlossen |
| Sprachsteuerung | Lokale Steuerung über Home Assistant | Abgeschlossen |
| Windows Server | LAB-DC01 installiert, AD DS eingerichtet | Abgeschlossen |
| Active Directory | Abschließende DNS- und DHCP-Integration | Offen |
| Storage | Zusätzliche Datenträger evaluieren | Offen |
| Jellyfin | Medienserver bereitstellen | Geplant |

!!! note "Hinweis"
    Das Netz `10.10.90.0/24` ist das WireGuard-Tunnelnetz. Ein VLAN 90 wurde nicht eingerichtet. Für das Windows- und Linux-Lab wird VLAN 70 genutzt.
