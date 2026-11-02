# Uptime Kuma und Monitoring

## Dienst

Uptime Kuma befindet sich im SERVER-VLAN unter `10.10.20.40`.

Der Dienst dient der Erreichbarkeits- und Verfügbarkeitsüberwachung von ausgewählten Netzwerkkomponenten und Anwendungen.

## Home-Assistant-Integration

Die Anbindung an Home Assistant wurde inzwischen fertiggestellt.

Der implementierte Ablauf ermöglicht die Weitergabe relevanter Statusänderungen an Home Assistant und die Benachrichtigung auf dem Smartphone.

Der Empfang von Benachrichtigungen für Ausfälle und Wiederherstellungen wurde erfolgreich getestet.

Auf dem Dashboard-Tablet werden diese Benachrichtigungen bewusst nicht ausgegeben.

## Zukünftige Erweiterungen

Mögliche spätere Monitoring-Erweiterungen:

- Überwachung von Proxmox-Ressourcen.
- CPU- und RAM-Auslastung.
- Temperatur- und SMART-Monitoring.
- Speicherplatzüberwachung.
- Zertifikatslaufzeiten.
- Backup-Erfolgsstatus.
- Überwachung von DNS und DHCP.
- Optional SNMP-Monitoring von Switch und Access Point.

Diese Erweiterungen gehören nicht zum abgeschlossenen Home-Assistant-Projekt.
