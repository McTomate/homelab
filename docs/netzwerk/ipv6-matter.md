# IPv6, Multicast und Matter

## IPv6-Konzept

Für die erfolgreiche Integration von Matter wurde IPv6 zwischen VLAN 20 und VLAN 50 eingerichtet und getestet.

Die OPNsense-Konfiguration verwendet für die betroffenen VLANs Router Advertisements, während der Interface-Konfigurationstyp weiterhin auf „None“ steht.

Verwendet werden IPv6-ULA-Präfixe, bei denen die VLAN-ID im Subnetzteil der Adresse steht:

| VLAN | Präfix |
|---|---|
| 20 – SERVER | `fdxx:xxxx:xxxx:20::/64` |
| 50 – IOT | `fdxx:xxxx:xxxx:50::/64` |

Auf Testgeräten wurden zusätzlich globale IPv6-Adressen aus dem Präfix des Providers beobachtet.

Das Routing und die IPv6-Kommunikation zwischen den betreffenden Netzen wurden erfolgreich getestet.

## Multicast und mDNS

Matter und AirPlay verwenden für die Erkennung beziehungsweise Kommunikation teilweise Multicast-basierte Protokolle.

Da normales VLAN-Routing mDNS nicht automatisch über VLAN-Grenzen transportiert, wurde Netflector für die benötigte Discovery-Kommunikation eingesetzt.

## Matter-Firewallregeln

Für den Matter-Betrieb ist insbesondere folgende Verbindung relevant:

| Quelle | Ziel | Protokoll |
|---|---|---|
| Home Assistant, VLAN 20 | IoT-IPv6-Präfix, VLAN 50 | UDP 5540 |

Die ursprüngliche Regel mit einem einzelnen Matter-Gerät als Ziel wurde auf das IoT-IPv6-Präfix erweitert.

Dies ermöglicht die Kommunikation mit mehreren entsprechenden Matter-Geräten, ohne jedes Gerät einzeln als Zieladresse eintragen zu müssen.

## Ergebnis

Die Govee-Lampe H6008 konnte erfolgreich über die VLAN-Grenze hinweg mit Home Assistant verbunden werden.

Folgende Funktionen wurden getestet:

- Ein- und Ausschalten.
- Helligkeitsregelung.
- Farbsteuerung.
- Erneute Erreichbarkeit nach Neustart des Geräts.

Die übrigen vorgesehenen Govee-Lampen wurden später ebenfalls in Home Assistant eingebunden.
