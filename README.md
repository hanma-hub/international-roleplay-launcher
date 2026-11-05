# International Roleplay – Launcher

Offizieller Launcher für **International Roleplay 0.9 Beta** (GTA San Andreas, open.mp-Server).

> **Öffentliche Beta-Testversion.** Der Launcher wurde auf Windows gestartet und geprüft (Serverstatus, Neuigkeiten,
> signierte Updates, Netzwerkziele, Prüfsummen). **Ein vollständiger Spielstart mit GTA über diese Version ist noch nicht
> bestätigt** – das holen wir in den nächsten Tagen nach. Die Registrierung neuer Konten ist während der Beta geschlossen.
> Probleme bitte im Forum melden.

**Download:** [Releases](https://github.com/hanma-hub/international-roleplay-launcher/releases/latest) – Datei `IRP_Launcher_0.9_Beta_<Version>.zip`
Forum, Support und Benutzerkonto: <https://forum.international-roleplay.net>

## Voraussetzungen
- GTA San Andreas für PC (Version 1.0) mit SA-MP-Client 0.3.7 oder einem kompatiblen open.mp-Client
- Windows 10 oder 11 (64 Bit). Keine Administratorrechte nötig.

## Installation
1. ZIP-Datei von der Release-Seite laden und an einen beliebigen Ort entpacken – **nicht** in den GTA-Ordner.
2. `Launcher.exe` starten und beim ersten Start den GTA-San-Andreas-Ordner wählen (dort liegen `gta_sa.exe` und `samp.exe`).
3. Spielernamen eintragen (neue Spieler: `Vorname_Nachname`), Sprache wählen, **SPIELEN**. Das Passwort gibst du erst im Spiel ein; der Launcher speichert keine Passwörter.

## Datei prüfen
Jede Release-Seite nennt die SHA-256-Prüfsumme der ZIP-Datei (zusätzlich als `.sha256`-Datei).
```powershell
Get-FileHash .\IRP_Launcher_0.9_Beta_1.17.3.zip -Algorithm SHA256
```

## Verbindungen
Der Launcher baut nur diese Verbindungen auf (fest eingebaut, kein Rückfall auf andere Adressen):
| Zweck | Ziel |
|---|---|
| Spiel (UDP) | `193.239.179.144:7777` – DDoS-Schutz |
| Status, Neuigkeiten, Updates (HTTPS) | `https://launcher.international-roleplay.net` (Cloudflare) |
| Downloads | GitHub Releases |

Update-Dateien werden nur mit gültiger Ed25519-Signatur und passender Prüfsumme übernommen.

## Häufige Probleme
- **Windows SmartScreen** („unbekannter Herausgeber“): Der Launcher ist nicht mit einem kostenpflichtigen Code-Signing-Zertifikat signiert. Prüfsumme kontrollieren, dann „Weitere Informationen“ → „Trotzdem ausführen“.
- **„Server nicht erreichbar“**: `verbindungstest.bat` im Launcher-Ordner starten und `verbindungstest.txt` im Support zeigen.
- **GTA-Ordner nicht erkannt**: Im Launcher den Ordner mit `gta_sa.exe` auswählen.

## Zurück zur vorherigen Version
Ältere Versionen bleiben auf der [Release-Seite](https://github.com/hanma-hub/international-roleplay-launcher/releases). Ordner der alten Version behalten oder die ältere ZIP-Datei erneut entpacken.

## Sicherheit
Siehe [SECURITY.md](SECURITY.md). Dieses Repository enthält nur den veröffentlichten Launcher und seine Dokumentation – keinen Servercode, keine Konfigurationen, keine Zugangsdaten.

---
*International Roleplay ist ein Fan-Projekt und steht in keiner Verbindung zu Rockstar Games oder Take-Two Interactive.*
