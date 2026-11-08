# Änderungen (Launcher)

> Aktuelle stabile Version: **1.21.0** (seit 08.11.2026). Die vorherige stabile Version **1.17.3** bleibt als Rückfallversion auf der Release-Seite. Die Versionen 1.17.4 bis 1.20.1 wurden nur intern gebaut und geprüft und nie veröffentlicht – ihre Änderungen sind in 1.21.0 enthalten (das Optik-Paket aus 1.18/1.19 ist seit 1.20.0 wieder entfernt).

## 1.21.0 – International Roleplay 0.9 Beta – stabile Version
- Status: auf Windows 11 geprüft (Fenster, Selbsttest, Startprüfung, Verbindungstest, signierte Update-Liste, Windows-Defender-Prüfung ohne Befund) und auf einem Spiele-PC getestet (Download und Start ohne Windows-Meldung, Spielstart über SPIELEN, Beitritt zum Server). Vom 08.11.2026 an zunächst als Testversion (Vorabversion) veröffentlicht, danach zur stabilen Version erklärt.
- **Eine einzige Datei:** `International-Roleplay-Launcher.exe` statt ZIP mit `Launcher.exe` und `WebView2Loader.dll`. Es wird keine DLL mitgeliefert, eingebettet, entpackt oder aus dem Speicher geladen: Das Launcher-Fenster nutzt die auf dem PC installierte Microsoft Edge WebView2-Laufzeit und lädt deren eigene, von Microsoft signierte Datei aus dem Programme-Ordner der Laufzeit.
- Fehlt die WebView2-Laufzeit, erklärt eine Meldung das und öffnet den offiziellen Microsoft-Download. Der Launcher lädt selbst keine Installer herunter und startet keine.
- Einstellungen und Protokolle liegen in `%LOCALAPPDATA%\IRPLauncher` – neben der heruntergeladenen Datei entstehen keine weiteren Dateien. Liegt die Datei in einem bisherigen Launcher-Ordner mit `launcher.json`, bleibt dieser Ordner wie bisher in Gebrauch.
- Startprüfung enthält jetzt zusätzlich den Verbindungstest (vorher `verbindungstest.bat`).
- Fehler beim Erzeugen des Fensters führen zu einer Meldung mit Grund statt zu einem stillen Programmende.
- Unverändert: Design, Start aus dem GTA-Ordner, gleiche Adressen, gleiche Signaturprüfung (Ed25519).

## 1.20.1 – nicht veröffentlicht (Änderungen in 1.21.0 enthalten)
- Sicherheitsüberarbeitung: Die Microsoft-Datei `WebView2Loader.dll` ist nicht mehr in der `Launcher.exe` eingebettet und wird nicht mehr mit einem eigenen Lader aus dem Speicher gestartet. Sie liegt jetzt offen (von Microsoft signiert) neben der `Launcher.exe` und wird nur aus diesem Ordner geladen. Die dafür genutzte Bibliothek (go-webview2) ist im Projekt angepasst; der Speicher-Lader (go-winloader) ist entfernt.
- Links werden über die Windows-Funktion zum Öffnen von Adressen gestartet (vorher `rundll32`) und nur für freigegebene Adressen (GitHub-Releaseseite, WebView2-Download bei Microsoft).
- Kein Zugriff mehr auf die Zwischenablage: Startprüfung „Bericht öffnen“ statt „Bericht kopieren“.
- `Launcher.exe` mit Versionsangaben, Programmsymbol und Manifest (`asInvoker`, keine Administratorrechte).
- Klare Meldung, wenn `WebView2Loader.dll` fehlt; Selbsttest prüft die Datei und die installierte WebView2-Laufzeit.
- Unverändert: Start aus dem GTA-Ordner, gleiche Adressen, gleiche Signaturprüfung (Ed25519), Design und Bildlauf.

## 1.20.0 – nicht veröffentlicht (Änderungen in 1.21.0 enthalten)
- Das Spiel startet immer aus dem GTA-Ordner des Spielers. Das frühere Optik-Paket (eigenes Spielprofil, Schalter, Teile-Liste, „Modpack prüfen/installieren“) ist entfernt; der Launcher schreibt nichts mehr in den GTA-Ordner oder ein Profil.
- Behoben: Mit eingeschaltetem Optik-Paket und „Launcher nach dem Start schließen“ blieb der SA-MP-Spielpfad (`gta_sa_exe` in der Windows-Registry) auf dem Launcher-Profil stehen; SA-MP startete danach auch ohne Launcher das Profil. Der Launcher setzt den Eintrag beim Start und vor jedem Spielen auf den GTA-Ordner zurück (Vermerk in `start_log.txt`) und stellt den Spielpfad nicht mehr um.
- Alte Optik-Paket-Dateien werden nicht ungefragt gelöscht: Einstellungen zeigen „Alte Optik-Paket-Dateien (ca. … MB)“ mit „Entfernen“ (Rückfrage). Gelöscht wird nur `modpack\profile` im Launcher-Ordner (Markerdatei geprüft); Hardlinks werden nur ausgehängt, das Original-GTA bleibt.
- Neu: Startprüfung (Einstellungen → Startprüfung, `startpruefung.bat`) für Startprobleme wie „SA-MP: An exception occurred“: GTA-Version (1.0 US), SA-MP-Client 0.3.7-R5, Registry-Spielpfad, ASI-Lader/-Plugins, Grafik-Mods, Mod Loader, CLEO, altes Profil, letzter SA-MP-Absturz (`crashinfo.txt`), `sa-mp.cfg`, letzter Spielstart. Verändert nichts; Bericht `startpruefung.txt` ohne Passwörter, Benutzerordner als `%USERPROFILE%`, nur „Bericht kopieren“ (Zwischenablage) – kein Versand.
- Updates: Aus der signierten Liste werden nur noch Dateien für den Launcher-Ordner übernommen. Ist eine neuere Launcher-Version signiert, zeigt der Launcher einen Hinweis mit Link auf die Download-Seite (die Programmdatei wird nie automatisch ersetzt).
- Sprach-Übergabe an den Server nur noch Name und Sprache. Einstellungen: veraltete Optionen entfernt; geblieben sind Updates beim Start, Hinweise, Schließen nach dem Start und die SA-MP-Optionen (nur wirksam, wenn eingeschaltet). Texte in 10 Sprachen.
- Unverändert: gleiche Adressen (Spiel über den DDoS-Schutz, Launcher-Dienst über HTTPS), gleiche Signaturprüfung (Ed25519), Design und Bildlauf.

## 1.19.0 – nicht veröffentlicht (Optik-Paket, ab 1.20.0 wieder entfernt)
- Modpack: Statt der drei Grafikprofile Standard/HD/Ultra gibt es nur noch **ein optionales „International Roleplay Optik-Paket“ mit einem Schalter aus/an** (eigene Ladebildschirme, HD-Handysymbole – nur Optik, kein Spielvorteil, jederzeit abschaltbar oder vollständig entfernbar). Ohne Paket spielst du wie bisher mit deinem unveränderten GTA.
- Bestehende Installationen bleiben gültig: Eine frühere Auswahl „HD“ oder „Ultra“ wird still als „Paket an“ übernommen; einzelne Teile lassen sich weiterhin in der Liste an- und abschalten. Beim Einschalten werden fehlende Dateien automatisch geladen.
- Abgeschaltete oder aus der Liste entfernte Teile hinterlassen keine Dateien mehr beim Spieler: Sie werden aus dem Launcher-Profil und dem Ablageordner `modpack/disabled` gelöscht (nur innerhalb des Launcher-Ordners – nie im Original-GTA). Hinweistexte sprechen jetzt vom „Optik-Paket“ statt von HD/Ultra.
- Ein zweites Launcher-Fenster desselben Launcher-Ordners wird mit kurzer Meldung beendet, damit es laufende Updates des ersten Fensters nicht stören kann.
- Unverändert: gleiche Adressen, gleiche Signaturprüfung (Ed25519), keine fremden Mods.

## 1.18.0 – nicht veröffentlicht (Optik-Paket, ab 1.20.0 wieder entfernt)
- Modpack: neuer optionaler Teil „HD-Handysymbole“ (eigene, scharfe App-Symbole für das Handy im Spiel, nur Optik). Wird mit dem Grafikprofil HD/Ultra installiert und liegt nur im Modpack-Profil – das Original-GTA bleibt unverändert.
- Grafikprofil startet jetzt auch ohne Mod Loader, wenn die eingeschalteten Teile ihn nicht brauchen (Mod Loader nur bei Dateien unter `modloader/`, ASI-Loader nur bei `.asi`-Dateien). Silent's ASI Loader wird erkannt.
- Der Launcher meldet dem Spielserver beim Start, ob die HD-Handysymbole vorhanden sind (das Handy schaltet die Symbole passend). Es werden weiterhin nur Spielername und Sprache übertragen – kein Passwort.
- Sicherheit (Prüfung November 2026): strengere Pfadprüfung für Update-Dateien, Erlaubnisliste für Dateiendungen auch im Modpack-Profil, erweiterte Fairness-Sperrliste (u. a. `vehicles.ide`, `carmods.dat`, `timecyc_24h.dat`, `water.dat`, `pedgrp.dat`, `cargrp.dat`, `ped.ifp`), keine Umleitung der Statusabfrage auf fremde Rechner, nur ein Update-Vorgang gleichzeitig, abgebrochene Updates werden beim nächsten Start zurückgenommen, Sicherung/Rückweg auch über Laufwerksgrenzen (GTA auf einem anderen Laufwerk), Download-Adressen mit Sonderzeichen korrekt kodiert.
- Unverändert: gleiche Adressen, gleiche Signaturprüfung (Ed25519), keine fremden Mods.

## 1.17.4 – nicht veröffentlicht (Änderungen in 1.21.0 enthalten)
- Einstellungen und alle anderen Seiten lassen sich wieder vollständig scrollen (Mausrad, Bildlaufleiste, Tastatur) – auch bei kleinen Fenstern und 125/150 % Windows-Skalierung.
- Mausrad über einem ausgewählten Zahlenfeld (FPS, Chatzeilen) verändert den Wert nicht mehr versehentlich, sondern scrollt die Seite.
- Das Fenster lässt sich jetzt vergrößern, verkleinern und maximieren und startet auf kleinen Bildschirmen passend im sichtbaren Bereich (vorher lag die Unterkante teils unter der Taskleiste).
- Keine weiteren Änderungen: gleiche Adressen, gleiche Update-Prüfung, keine Mods.

## 1.17.3 – International Roleplay 0.9 Beta – vorherige stabile Version (Rückfallversion)
- Status: Launcher auf Windows geprüft; vollständiger Spielstart mit GTA über diese Version noch nicht bestätigt.
- Kontonamen mit Punkt (z. B. umbenannte Konten) werden akzeptiert; neue Spieler wählen im Spiel weiter `Vorname_Nachname`.
- Status, Neuigkeiten und Updates nur über HTTPS (Cloudflare); Spielverbindung nur über den DDoS-Schutz.
- Mehrere Abfrageversuche, wenn der Schutzdienst die erste Abfrage nach einer Pause verwirft.
- Verständlichere Fehlermeldungen, Verbindungstest (`verbindungstest.bat`).
