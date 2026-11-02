# WLAN und Access Point

## Aktueller Zustand

Der TP-Link Access Point wurde zwischenzeitlich in Betrieb genommen.

Er ermöglicht die Zuordnung verschiedener WLAN-Clients zu getrennten Netzen.

| WLAN-Bereich | VLAN | Zweck |
|---|---|---|
| Internes WLAN | 40 | Vertrauenswürdige Clients |
| IoT-WLAN | 50 | Fernseher und Smart-Home-Geräte |
| Gäste-WLAN | 60 | Gäste und fremde Geräte |

## Management

Für das Management des Access Points existiert das separate Netz `10.10.11.0/24`.

Der Zugriff auf die Managementoberfläche sollte von regulären Clients und IoT-Geräten getrennt bleiben.

Die konkrete AP-IP-Adresse und die aktuelle Managementanbindung sind in einer späteren Konfigurationsaufnahme zu ergänzen.

## Samsung-TV

Der Samsung-TV befindet sich im IoT-VLAN 50.

Bereits funktionsfähig:

- Netzwerkzugang über WLAN.
- AirPlay aus dem VLAN 40.
- Samsung SmartThings.
- Steuerung trotz VLAN-Segmentierung.

Zu Beginn war eine temporäre Freigabe mit allen Protokollen/Ports für die Fehlersuche erforderlich.

Die temporäre breite Regel wurde später deaktiviert. AirPlay funktionierte nach einem erneuten Test weiterhin mit den verbliebenen Regeln.

Das genaue finale Regelwerk sollte über einen OPNsense-Konfigurationsexport archiviert werden.
