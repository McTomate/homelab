# Smart Home über VLAN-Grenzen

**Status:** abgeschlossen am 01.11.2026

## Ausgangslage

Home Assistant läuft im SERVER-VLAN 20, die Smart-Home-Geräte und der TV im IoT-VLAN 50. Die IoT-Geräte sollen isoliert bleiben und trotzdem steuerbar sein.

**Entscheidung:** Ein Umzug von Home Assistant ins IoT-VLAN wurde verworfen. Stattdessen sind nur die nötigen Verbindungen gezielt in OPNsense freigegeben. So bleibt der Server von den weniger vertrauenswürdigen IoT-Geräten getrennt.

## Probleme und Lösungen

| Problem | Lösung |
|---|---|
| mDNS für die Geräteerkennung (Matter, AirPlay) wird nicht über VLAN-Grenzen geroutet | Netflector (noch unveröffentlichtes OPNsense-Plugin) leitet die Discovery-Pakete zwischen den VLANs weiter |
| Matter benötigt IPv6 | Router Advertisements auf OPNsense für VLAN 20 und 50, ULA-Präfixe mit VLAN-ID im Subnetz (`fdxx:…:20::/64`, `fdxx:…:50::/64`) |
| Die Matter-Regel galt nur für ein einzelnes Gerät | Regel auf das gesamte IoT-IPv6-Präfix erweitert (UDP 5540 von Home Assistant) |
| AirPlay zum TV von VLAN 40 nach VLAN 50 | Zur Fehlersuche kurzzeitig alle Ports freigegeben, danach die breite Regel deaktiviert. AirPlay läuft mit den gezielten Regeln weiter |

## Ergebnis

- Govee-Lampen über Matter steuerbar (Ein/Aus, Helligkeit, Farbe) und nach einem Neustart wieder erreichbar
- Samsung-TV über AirPlay und SmartThings steuerbar
- Dashboard auf einem Tablet mit lokaler Sprachsteuerung
- Zugriff von unterwegs über WireGuard
- Uptime-Kuma-Benachrichtigungen eingebunden, Testregeln bereinigt

## Technische Eckdaten

| | |
|---|---|
| Home Assistant | HAOS-VM 200, 2 vCPU, 4 GiB RAM, 32 GB, q35/OVMF |
| Matter Server | Add-on 1.4.0, Port 5580, Bluetooth LE deaktiviert (reine Netzwerkkommunikation) |
