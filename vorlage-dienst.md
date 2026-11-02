# Vorlage: Dienst

Kleine Dienste: nur eine Zeile in `docs/dienste.md` ergänzen.
Größere Projekte: diese Datei nach `docs/projekte/` kopieren (z. B. `jellyfin.md`)
und in `mkdocs.yml` unter `nav` → `Projekte` eintragen.

> **Die Doku ist öffentlich.** Nie hinein: Passwörter, API-Keys, WireGuard-Schlüssel,
> öffentliche IP, DynDNS-Adressen, nach außen offene Ports.

## Was macht der Dienst?

Ein, zwei Sätze.

## Wo läuft er?

- **Host:** server-01 (LXC 101)
- **Adresse:** `http://192.168.10.20`
- **Zugangsdaten:** Bitwarden → Homelab → Dienstname

## Installation

```bash
# Die Befehle, die du zum Einrichten benutzt hast
docker compose up -d
```

## Backup

Was wird gesichert, wohin, wie oft?

## Probleme & Lösungen

??? note "Dienst startet nicht nach Update"
    Was war die Ursache, was hat geholfen?
