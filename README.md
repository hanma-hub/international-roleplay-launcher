# International Roleplay – Launcher

Offizieller Launcher für **International Roleplay 0.9 Beta** (GTA San Andreas, open.mp-Server).

> **Öffentliche Beta.** Die Registrierung neuer Konten ist während der Beta geschlossen. Probleme bitte im Forum melden.

## Download

| | Version | Datei |
|---|---|---|
| **Stabil (empfohlen)** | **1.17.3** | [Release „Latest“](https://github.com/hanma-hub/international-roleplay-launcher/releases/latest) – `IRP_Launcher_0.9_Beta_1.17.3.zip` |
| Testversion (Vorabversion) | 1.21.0 | [Release v1.21.0](https://github.com/hanma-hub/international-roleplay-launcher/releases/tag/v1.21.0) – `International-Roleplay-Launcher.exe` (eine einzige Datei) |

Die **Testversion** ist für Tester gedacht: Sie wurde auf Windows 11 geprüft (Fenster, Selbsttest, Startprüfung, Verbindungstest, signierte Update-Liste, Windows-Defender-Prüfung ohne Befund), ein vollständiger Spielstart mit GTA auf einem Spiele-PC ist aber **noch nicht bestätigt**. Zum normalen Spielen bitte die stabile Version verwenden. Die Testversion ersetzt die stabile Version nicht automatisch.

Forum, Support und Benutzerkonto: <https://forum.international-roleplay.net>

## Voraussetzungen
- GTA San Andreas für PC (Version 1.0 US) mit SA-MP-Client 0.3.7-R5 oder einem kompatiblen open.mp-Client
- Windows 10 oder 11 (64 Bit). Keine Administratorrechte nötig.
- Nur für die Testversion 1.21.0: Microsoft Edge WebView2-Laufzeit (bei Windows 11 vorinstalliert). Fehlt sie, öffnet der Launcher den offiziellen Microsoft-Download.

## Installation
**Stabile Version 1.17.3**
1. ZIP-Datei von der Release-Seite laden und an einen beliebigen Ort entpacken – **nicht** in den GTA-Ordner.
2. `Launcher.exe` starten und beim ersten Start den GTA-San-Andreas-Ordner wählen (dort liegen `gta_sa.exe` und `samp.exe`).
3. Spielernamen eintragen (neue Spieler: `Vorname_Nachname`), Sprache wählen, **SPIELEN**. Das Passwort gibst du erst im Spiel ein; der Launcher speichert keine Passwörter.

**Testversion 1.21.0**
1. `International-Roleplay-Launcher.exe` laden (z. B. in *Downloads* oder auf den Desktop) – **nicht** in den GTA-Ordner. Es gibt nichts zu entpacken.
2. Datei starten, GTA-Ordner wählen, Namen eintragen, **SPIELEN**. Einstellungen liegen in `%LOCALAPPDATA%\IRPLauncher`. Willst du Name, Sprache und GTA-Ordner der bisherigen Version übernehmen, lege die Datei in den bisherigen Launcher-Ordner (neben `launcher.json`).

Das Spiel startet immer aus deinem GTA-Ordner; der Launcher verändert ihn nicht.

## Datei prüfen
Jede Release-Seite nennt die SHA-256-Prüfsumme (zusätzlich als `.sha256`-Datei).
```powershell
Get-FileHash .\IRP_Launcher_0.9_Beta_1.17.3.zip -Algorithm SHA256
Get-FileHash .\International-Roleplay-Launcher.exe -Algorithm SHA256
```

## Verbindungen
Der Launcher baut nur diese Verbindungen auf (fest eingebaut, kein Rückfall auf andere Adressen):
| Zweck | Ziel |
|---|---|
| Spiel (UDP) | `193.239.179.144:7777` – DDoS-Schutz |
| Status, Neuigkeiten, Updates (HTTPS) | `https://launcher.international-roleplay.net` (Cloudflare) |
| Downloads | GitHub Releases |

Die Update-Liste ist mit Ed25519 signiert; unsignierte oder veränderte Angaben werden abgelehnt. Die Programmdatei ersetzt sich nie selbst.

## Häufige Probleme
- **Windows SmartScreen** („Der Computer wurde durch Windows geschützt“, „unbekannter Herausgeber“): Das ist keine Virenmeldung, sondern fehlende Bekanntheit – der Launcher ist (noch) nicht mit einem Code-Signing-Zertifikat signiert. Lade ihn nur von dieser Release-Seite oder über den Download im Forum und vergleiche die Prüfsumme; ob du ihn dann startest, entscheidest du.
- **Windows Defender meldet einen Virus**: Datei nicht wiederherstellen und keine Ausnahme eintragen, sondern im Forum-Support melden – mit dem Namen der Erkennung aus *Windows-Sicherheit → Schutzverlauf*.
- **„Server nicht erreichbar“ / Spiel startet nicht**: Version 1.17.3: `verbindungstest.bat` im Launcher-Ordner starten und `verbindungstest.txt` im Support zeigen. Testversion 1.21.0: *Einstellungen → Startprüfung → Prüfen* (verändert nichts, enthält auch den Verbindungstest).
- **GTA-Ordner nicht erkannt**: Im Launcher den Ordner mit `gta_sa.exe` auswählen.

## Zurück zur vorherigen Version
Alle veröffentlichten Versionen bleiben auf der [Release-Seite](https://github.com/hanma-hub/international-roleplay-launcher/releases).

## Sicherheit
Siehe [SECURITY.md](SECURITY.md). Dieses Repository enthält nur den veröffentlichten Launcher und seine Dokumentation – keinen Servercode, keine Konfigurationen, keine Zugangsdaten.

---
*International Roleplay ist ein Fan-Projekt und steht in keiner Verbindung zu Rockstar Games oder Take-Two Interactive.*
