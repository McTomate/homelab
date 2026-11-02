# Jellyfin (geplant)

## Ziel

Jellyfin soll später als zentraler Medienserver bereitgestellt werden.

Mögliche Clients sind insbesondere der Samsung-TV und weitere Geräte im Heimnetz.

## Geplante Architektur

```text
NAS oder lokaler Medienspeicher → Jellyfin-VM/LXC → freigegebene Client-Netze → Wiedergabegeräte
```

## Technische Anforderungen

- Getrennte VM oder LXC.
- Eigener Speicherbereich für Medien.
- Zugriff auf Medienbibliothek.
- Definierte Firewallfreigaben.
- Überwachung durch Uptime Kuma.
- Geeignetes Backup-Konzept für Konfiguration und Metadaten.

Die Unterstützung von Direct Play und gegebenenfalls Hardware-Transcoding soll bei der Bereitstellung geprüft werden.

## Priorität

Jellyfin besitzt gegenüber dem Windows-Lab, Ansible, Storage und Backup derzeit eine niedrigere Priorität.

Das Projekt bleibt geplant, ist jedoch nicht Bestandteil der nächsten Pflichtarbeiten.
