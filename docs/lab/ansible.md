# Ansible und Linux-Automatisierung

## Control Node

Das MacBook Air 2013 wurde für die Linux-basierte Administration und Ansible-Automatisierung vorbereitet.

Der zuletzt dokumentierte Linux-Stand verwendet Ubuntu mit Ansible Core 2.16.3. In der älteren Dokumentationsversion war noch Linux Mint angegeben.

## Geplante Aufgaben

- SSH-Schlüsselverwaltung.
- Aufbau eines Ansible-Inventars.
- Einrichtung von Hostgruppen.
- Playbooks für Linux-Updates.
- Installation und Konfiguration von Diensten.
- Benutzer- und Gruppenverwaltung.
- Firewall-Konfiguration auf Linux-Hosts.
- Konfigurationsdateien zentral verwalten.
- Einsatz von Ansible Vault.
- Optional Windows-Automatisierung über WinRM.

## Zielarchitektur

```text
Ansible Control Node → VLAN 70 → Linux- und Windows-Testserver
```

Für einen sauberen Sicherheitsaufbau sollten nur die benötigten Verbindungen zwischen dem jeweiligen Control Node und den Zielsystemen geöffnet werden.

Ein späterer Einsatz von Git zur Versionsverwaltung der Playbooks wird empfohlen.
