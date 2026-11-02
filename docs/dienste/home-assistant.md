# Home Assistant

!!! success "Projektstatus: Abgeschlossen am 01.11.2026"
    Die geplanten Home-Assistant-Arbeiten wurden einschließlich Dashboard, Sprachsteuerung, Geräteintegration und Monitoring-Benachrichtigungen fertiggestellt.

## VM-Konfiguration

| Eigenschaft | Wert |
|---|---|
| VM-ID | 200 |
| Name | `home-assistant` |
| Betriebssystem | Home Assistant OS |
| VLAN | 20 |
| IPv4 | `10.10.20.132` |
| vCPU | 2 |
| RAM | 4 GiB |
| Festplatte | 32 GB |
| BIOS | OVMF |
| Maschinentyp | q35 |
| Netzwerk | `vmbr0`, VLAN 20 |

Zusätzlich besitzt die VM eine IPv6-ULA-Adresse aus dem Präfix des SERVER-VLANs. Der Zugriff auf die Weboberfläche erfolgt im internen Netz über Port 8123.

## Geräteintegration

Home Assistant dient als zentrale Plattform zur Steuerung der eingebundenen Smart-Home-Geräte.

Umgesetzt wurden:

- Govee-Lampen.
- Matter-Integration.
- VLAN-übergreifende Kommunikation.
- Gerätesteuerung über das Dashboard.
- Lokale Sprachsteuerung.

## Matter Server

Der Matter Server wurde als Add-on eingerichtet.

| Parameter | Wert |
|---|---|
| Matter Server Add-on | 1.4.0 |
| Port | 5580 |
| Interface | `enp6s18` |
| Bluetooth LE | Deaktiviert |

Die Gerätekommunikation erfolgt über das Netzwerk und benötigt keine lokale Bluetooth-Verbindung zum Home-Assistant-Server.

## Dashboard

Das Lenovo Tab M10 Gen 3 wurde als Home-Assistant-Dashboard eingerichtet.

Das Tablet übernimmt insbesondere:

- Bedienung der Smart-Home-Geräte.
- Anzeige relevanter Home-Assistant-Informationen.
- Nutzung der lokalen Sprachsteuerung.

Das Dashboard wurde erfolgreich in Betrieb genommen.

## Netzwerkzugriffe

Home Assistant verbleibt dauerhaft im SERVER-VLAN 20.

Ein zuvor betrachteter Umzug in VLAN 50 wurde verworfen.

Die erforderlichen Verbindungen zu den IoT-Geräten werden stattdessen gezielt über OPNsense zugelassen.

Auch der gewünschte Zugriff aus dem entsprechenden IoT-WLAN auf Home Assistant wurde eingerichtet.

## Abgeschlossene Nacharbeiten

- Weitere Govee-Lampen eingebunden.
- Matter-Kommunikation funktionsfähig.
- Nicht mehr benötigte Testregeln bereinigt.
- Dashboard fertiggestellt.
- Sprachsteuerung eingerichtet.
- Zugriff über WireGuard getestet.
- Uptime-Kuma-Benachrichtigungen integriert.

Für dieses Teilprojekt bestehen nach dem zuletzt bestätigten Stand keine offenen Pflichtaufgaben mehr.
