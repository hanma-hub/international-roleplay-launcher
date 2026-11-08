# International Roleplay – Launcher

Offizieller Launcher für **International Roleplay 0.9 Beta** (GTA San Andreas, open.mp-Server).

> **International Roleplay ist in der öffentlichen Beta.** Die Registrierung neuer Konten ist während der Beta geschlossen. Probleme bitte im Forum melden.

**Download:** [Neueste Version (1.21.1)](https://github.com/hanma-hub/international-roleplay-launcher/releases/latest) – **eine einzige Datei** `International-Roleplay-Launcher.exe`
Forum, Support und Benutzerkonto: <https://forum.international-roleplay.net>

## Voraussetzungen
- GTA San Andreas für PC (Version 1.0 US) mit SA-MP-Client 0.3.7-R5 oder einem kompatiblen open.mp-Client
- Windows 10 oder 11 (64 Bit). Keine Administratorrechte nötig.
- Microsoft Edge WebView2-Laufzeit (für das Launcher-Fenster) – bei Windows 11 vorinstalliert, bei Windows 10 fast immer über Windows-Updates vorhanden. Fehlt sie, öffnet der Launcher den offiziellen Microsoft-Download.

## Installation und Start
1. `International-Roleplay-Launcher.exe` von der Release-Seite laden (z. B. in *Downloads* oder auf den Desktop) – **nicht** in den GTA-Ordner. Es gibt nichts zu entpacken.
2. Datei starten und beim ersten Start den GTA-San-Andreas-Ordner wählen (dort liegen `gta_sa.exe` und `samp.exe`).
3. Spielernamen eintragen (neue Spieler: `Vorname_Nachname`), Sprache wählen, **SPIELEN**. Das Passwort gibst du erst im Spiel ein; der Launcher speichert keine Passwörter.

Das Spiel startet immer aus deinem GTA-Ordner; der Launcher verändert ihn nicht. Er setzt nur – wie der SA-MP-Client selbst – Spielernamen und GTA-Pfad in den SA-MP-Einstellungen von Windows.
Einstellungen und Protokolle legt der Launcher in `%LOCALAPPDATA%\IRPLauncher` ab (nicht neben der Datei).
**Update von einer älteren Version (ZIP mit `Launcher.exe`):** Die neue Datei einfach starten. Willst du Name, Sprache und GTA-Ordner übernehmen, lege sie in den bisherigen Launcher-Ordner (neben `launcher.json`). `WebView2Loader.dll` aus älteren Paketen wird nicht mehr benötigt.

## Datei prüfen
Jede Release-Seite nennt die SHA-256-Prüfsumme (zusätzlich als `.sha256`-Datei).
```powershell
Get-FileHash .\International-Roleplay-Launcher.exe -Algorithm SHA256
```

## Verbindungen
Der Launcher baut nur diese Verbindungen auf (fest eingebaut, kein Rückfall auf andere Adressen):
| Zweck | Ziel |
|---|---|
| Spiel (UDP) | `193.239.179.144:7777` – DDoS-Schutz |
| Status, Neuigkeiten, Updates (HTTPS) | `https://launcher.international-roleplay.net` (Cloudflare) |
| Downloads | GitHub Releases |

Hinweise auf neue Versionen kommen über eine mit Ed25519 signierte Liste; die Programmdatei ersetzt sich nie selbst.

## Häufige Probleme
- **Windows SmartScreen** („Der Computer wurde durch Windows geschützt“, „unbekannter Herausgeber“): Das ist keine Virenmeldung, sondern fehlende Bekanntheit – der Launcher ist (noch) nicht mit einem Code-Signing-Zertifikat signiert. Lade ihn nur von dieser Release-Seite und vergleiche die Prüfsumme; ob du ihn dann über „Weitere Informationen“ startest, entscheidest du.
- **Windows Defender meldet einen Virus**: Datei nicht wiederherstellen und keine Ausnahme eintragen, sondern im Forum-Support melden – mit dem Namen der Erkennung aus *Windows-Sicherheit → Schutzverlauf*.
- **Status „Online (ohne Ping)“**: Der Launcher-Dienst meldet den Server als online, aber die direkte Statusabfrage dieses PCs über den DDoS-Schutz bekam (noch) keine Antwort – meist kurz nach einem Serverneustart. **SPIELEN funktioniert trotzdem**; mit dem Kreispfeil oben neu abfragen.
- **Spiel startet nicht / „SA-MP: An exception occurred“ / „Server nicht erreichbar“**: Im Launcher *Einstellungen → Startprüfung → Prüfen*. Die Prüfung verändert nichts und nennt u. a. GTA- und SA-MP-Version, ASI-/Grafik-Mods, Mod Loader, CLEO, den letzten SA-MP-Absturz und das Ergebnis eines Verbindungstests. Den Bericht („Bericht öffnen“) nur im Support zeigen, wenn du möchtest – er enthält Ordner- und Mod-Dateinamen, aber keine Passwörter.
- **Fenster bleibt leer oder Meldung zur WebView2-Laufzeit**: Windows-Updates installieren oder die Laufzeit über den angezeigten Microsoft-Link neu installieren.
- **GTA-Ordner nicht erkannt**: Im Launcher den Ordner mit `gta_sa.exe` auswählen.

## Zurück zur vorherigen Version
Die vorherige Version **1.21.0** bleibt als Rückfallversion auf der [Release-Seite](https://github.com/hanma-hub/international-roleplay-launcher/releases) (ebenso die ältere 1.17.3). Empfohlen ist die aktuelle Version.

## Sicherheit
Siehe [SECURITY.md](SECURITY.md). Dieses Repository enthält nur den veröffentlichten Launcher und seine Dokumentation – keinen Servercode, keine Konfigurationen, keine Zugangsdaten.

---
*International Roleplay ist ein Fan-Projekt und steht in keiner Verbindung zu Rockstar Games oder Take-Two Interactive.*
