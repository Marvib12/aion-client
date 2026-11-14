# Aion Client

Kleiner Hintergrund-Client für Aion 2. Er liest die Daten deiner Aion-2-Tools auf dem PC und schickt alle 10 Minuten Energie, Charaktere, Währungen und ausgewählte Bosse an den Server. Du bekommst dann per ntfy eine Nachricht vor deinen Weltenbossen und wenn ein Charakter bald volle Energie hat.

Keine Installation, kein Fenster, keine Meldungen.

## Unterstützte Tools

Der Client erkennt selbst, welche Tools installiert sind, und nimmt pro Charakter immer den neuesten Stand. Du brauchst mindestens eins davon.

| Funktion | [Questlog](https://questlog.gg/aion-2) | [A2Tools](https://a2tools.app) | [Nyerk](https://github.com/xCROv/aion2-nyerk) |
| --- | :---: | :---: | :---: |
| Energie (normal und aufgeladen) | ✓ | ✓ | ✓ |
| Max-Energie (Mitgliedschaft) | ✓ | ✓ | ✓ |
| Klasse und Level | ✓ | ✓ | – |
| Kina, Kina (gebunden), Abyss-Punkte | ✓ | – | – |
| Ausgewählte Bosse für die Warnungen | ✓ | – | – |
| Boss-Zeiten | ✓ | ✓ | – |

Hinweise:

- **A2Tools:** Energie kommt aus dem Plugin **Roster / Content Overview**, es muss installiert sein. Die Boss-Zeiten holt der Server direkt bei A2Tools, dafür muss der Client nicht laufen.
- **Nyerk:** Energie kommt aus dem Addon **Task List**.
- **Ohne Questlog** bleibt deine zuletzt gesendete Boss-Auswahl erhalten.

Unabhängig von den Tools kennt der Server für europäische Server die festen Zeiten von Watcher Kaira, Argo, Nahma, den Executors und der Artefakt-Belagerung.

## Einrichtung

1. Lade `AionClient.exe` unter [Releases](../../releases/latest) herunter.
2. Lege sie in einen eigenen Ordner, in dem du Schreibrechte hast, zum Beispiel `C:\Users\<Name>\AionClient`. Nicht unter `C:\Program Files`, sonst funktionieren Updates nicht.
3. Rechtsklick auf den Desktop → **Neu** → **Verknüpfung**.
4. Trage als Speicherort ein, beide Pfade in Anführungszeichen:

   ```
   "C:\Users\<Name>\AionClient\AionClient.exe" "C:\Pfad\zu\Questlog.exe"
   ```

5. Vergib einen Namen, zum Beispiel `Questlog`, und starte Questlog ab jetzt über diese Verknüpfung.

Du findest den Pfad zu Questlog so: Rechtsklick auf deine bisherige Questlog-Verknüpfung → **Eigenschaften** → **Ziel**. Nutzt du kein Questlog, trag nur die `AionClient.exe` ohne zweiten Pfad ein und starte deine Tools wie gewohnt selbst. A2Tools braucht zum Beispiel Administratorrechte, die kann der Client nicht anfordern.

Die Verknüpfung startet Questlog und den Client. Läuft Questlog oder der Client schon, wird nichts doppelt gestartet. Der Client läuft weiter, wenn du Questlog schließt.

## Deine ID finden

Der Client erstellt beim ersten Start eine feste ID mit 6 Zeichen, zum Beispiel `abc123`. Du brauchst sie für die Benachrichtigungen.

1. Starte den Client einmal über deine Verknüpfung.
2. Drücke **Windows-Taste + R**, gib `%APPDATA%\AionTool` ein und bestätige mit **Enter**.
3. Öffne die Datei `user-id.txt`. Darin steht deine ID.

Die ID bleibt immer gleich, auch nach Updates. Löschst du den Ordner `%APPDATA%\AionTool`, bekommst du beim nächsten Start eine neue ID.

Fehlt die Datei, lief der Client noch nicht. Prüfe im Task-Manager, ob `AionClient.exe` läuft, und schau in `client.log` im selben Ordner nach einem Fehler.

## Benachrichtigungen

Installiere die ntfy-App, stelle als Server `https://ntfy.marvib.de` ein und abonniere mit deiner ID:

| Thema | Inhalt |
| --- | --- |
| `boss-<ID>` | 30 Minuten vor deinen ausgewählten Bossen, mit allen gewählten Bossen der nächsten Stunde in einer Nachricht. Die Artefakt-Belagerung kommt für alle. |
| `char-<ID>` | Täglich um 6 Uhr: Charaktere, die innerhalb von 24 Stunden voll sind. Außerdem eine Nachricht, wenn ein neuer Charakter erfasst wurde. |

Auf Android: Aktiviere beim Abonnieren **Sofortige Zustellung** und nimm ntfy von der Akku-Optimierung aus.

## Updates

Der Client prüft beim Start und alle 6 Stunden, ob es eine neue Version gibt. Er aktualisiert sich selbst und läuft danach ohne Neustart weiter.

## Beenden und Entfernen

Beende `AionClient.exe` im Task-Manager. Lösche dann die Exe, die Verknüpfung und den Ordner `%APPDATA%\AionTool`.

## Windows-Warnung

Die Datei ist nicht signiert. Windows SmartScreen oder dein Virenscanner können beim ersten Start warnen.
