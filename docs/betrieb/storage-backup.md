# Storage und Datensicherung

## Aktueller Zustand

Proxmox verfügt über lokalen Speicher für Betriebssystem, Container und VMs.

Ein separates produktives NAS ist noch nicht dokumentiert.

Weitere SSDs sollen auf ihren technischen Zustand und ihre Eignung geprüft werden.

## Geplantes Storage-Konzept

**Kurzfristig:**

- Vorhandene SSDs inventarisieren.
- SMART-Werte auswerten.
- Temperaturverhalten prüfen.
- Verfügbare Kapazitäten bestimmen.
- Geeignete Datenträger für weniger kritische Tests verwenden.

**Mittelfristig:**

- NAS bereitstellen.
- Zentralen Storage einrichten.
- Proxmox-Backups auf separates Ziel schreiben.
- Backup-Aufbewahrung definieren.
- Wiederherstellung regelmäßig testen.

## SSD-Zustandsprüfung

Bei den zuletzt geprüften NVMe-SSDs traten in der Vergangenheit Systemabstürze ohne aussagekräftige Protokolle auf.

Während eines Wipe-Vorgangs wurden Temperaturen oberhalb von 70 °C beobachtet.

Vor einem produktiven Einsatz sollten daher durchgeführt werden:

- SMART-/NVMe-Health-Analyse.
- Prüfung auf Media Errors und Critical Warnings.
- Prüfung des Error Information Log.
- Belastungs- und Temperaturtests.
- Test mit geeigneter passiver oder aktiver Kühlung.
- Längerer I/O-Test unter kontrollierten Bedingungen.

Ein Kühlkörper kann ein thermisches Problem verbessern, beseitigt aber nicht zwangsläufig bereits vorhandene Hardwarefehler.

## Backup-Konzept

Als Zielbild wird eine 3-2-1-orientierte Sicherungsstrategie angestrebt:

- Produktivdaten auf der ursprünglichen Plattform.
- Mindestens eine zusätzliche lokale Sicherung.
- Eine weitere Kopie auf einem unabhängigen beziehungsweise externen Speicherziel.

Für Proxmox kommen insbesondere geplante VM-/Container-Backups und später Proxmox Backup Server infrage.

Snapshots sind nicht als Ersatz für unabhängige Backups zu betrachten.

!!! warning "Status"
    Eine vollständig nachgewiesene Off-Host-Backup- und Restore-Strategie steht noch aus.
