# Vorlage: Dienst

Kopiere diese Datei für jeden neuen Dienst (z. B. `pihole.md`, `jellyfin.md`).

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
