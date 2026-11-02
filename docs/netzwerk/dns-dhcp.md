# DNS- und DHCP-Architektur

## Infrastruktur-DNS

Für die allgemeine Homelab-Infrastruktur wird die Domain `home.arpa` verwendet.

Die Namensauflösung erfolgt über AdGuard Home und die lokalen DNS-Einträge von OPNsense.

Das bisherige Grundkonzept sieht folgende Auflösungskette vor:

```text
Client → AdGuard Home (10.10.20.31) → OPNsense/dnsmasq für lokale Namen
                                     → konfigurierte Upstream-Resolver für externe Domains
```

Welche Upstream-Resolver AdGuard momentan tatsächlich verwendet, ist für die endgültige Ist-Dokumentation noch einmal zu prüfen.

## AdGuard Home

AdGuard Home übernimmt:

- DNS-Anfragen der Clients.
- DNS-Filterung.
- Weiterleitung beziehungsweise Auflösung interner Namen.
- Protokollierung und Auswertung von DNS-Anfragen.

Der Dienst befindet sich unter `10.10.20.31` im SERVER-VLAN.

## OPNsense / dnsmasq

Dnsmasq übernimmt insbesondere:

- DHCP in den konfigurierten VLANs.
- Lokale Hosteinträge.
- Infrastruktur-Namensauflösung.
- Zuordnung von Hostnamen und statischen Adressen.

Die früheren doppelten Namensauflösungen durch zusätzlich eingelesene `/etc/hosts`-Einträge wurden bereits bereinigt.

## DHCP

| Segment | DHCP-Konzept |
|---|---|
| MGMT | Feste IPs und Reservierungen bevorzugt |
| SERVER | Feste IPs bzw. DHCP-Reservierungen |
| CLIENT/WLAN | OPNsense dnsmasq |
| IOT | OPNsense dnsmasq |
| GUEST | OPNsense dnsmasq |
| LAB | OPNsense dnsmasq |

**Bekannte DHCP-Bereiche:**

- VLAN 50: `10.10.50.100–10.10.50.199`
- VLAN 70: `10.10.70.100–10.10.70.199`

Die DHCP-Bereiche der anderen Netze sind aus der aktuellen OPNsense-Konfiguration zu ergänzen.

## Besondere DNS-Anforderungen des Windows-Labs

Für Active Directory wird zusätzlich ein Windows-DNS-Server betrieben.

Geplantes Schema:

```text
Domänenclient im VLAN 70 → Windows DNS auf LAB-DC01 (10.10.70.10)
                         → AdGuard als Forwarder für externe bzw. nicht autoritative Namen
```

Dabei gilt:

- Active-Directory-Clients verwenden den AD-DNS-Server.
- Der Domänencontroller verwendet seinen eigenen DNS-Dienst.
- Für externe DNS-Anfragen wird ein Forwarder konfiguriert.
- Die Infrastruktur-Domain `home.arpa` bleibt getrennt von der Windows-Domäne.
- Für Zugriffe aus anderen Netzen kann später eine gezielte bedingte DNS-Weiterleitung zur AD-Domäne eingerichtet werden.

!!! warning
    Eine Weiterleitung darf keine DNS-Schleife zwischen AdGuard und dem Domänencontroller erzeugen.
