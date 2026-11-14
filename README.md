# Aion Client

Kleiner Hintergrund-Client für Aion 2. Er liest deine lokalen Questlog-Daten und schickt alle 10 Minuten Energie, Charaktere und ausgewählte Bosse an den Server. Du bekommst dann per ntfy eine Nachricht vor deinen Weltenbossen und wenn ein Charakter bald volle Energie hat.

Keine Installation, kein Fenster, keine Meldungen.

## Einrichtung

1. Lade `AionClient.exe` unter [Releases](../../releases/latest) herunter.
2. Lege sie in einen eigenen Ordner, in dem du Schreibrechte hast, zum Beispiel `C:\Users\<Name>\AionClient`. Nicht unter `C:\Program Files`, sonst funktionieren Updates nicht.
3. Rechtsklick auf den Desktop → **Neu** → **Verknüpfung**.
4. Trage als Speicherort ein, beide Pfade in Anführungszeichen:

   ```
   "C:\Users\<Name>\AionClient\AionClient.exe" "C:\Pfad\zu\Questlog.exe"
   ```

5. Vergib einen Namen, zum Beispiel `Questlog`, und starte Questlog ab jetzt über diese Verknüpfung.

Du findest den Pfad zu Questlog so: Rechtsklick auf deine bisherige Questlog-Verknüpfung → **Eigenschaften** → **Ziel**.

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
| `boss-<ID>` | 30 Minuten vor deinen ausgewählten Bossen |
| `char-<ID>` | Täglich um 6 Uhr: Charaktere, die innerhalb von 24 Stunden voll sind |

## Updates

Der Client prüft beim Start und alle 6 Stunden, ob es eine neue Version gibt. Er aktualisiert sich selbst und läuft danach ohne Neustart weiter.

## Beenden und Entfernen

Beende `AionClient.exe` im Task-Manager. Lösche dann die Exe, die Verknüpfung und den Ordner `%APPDATA%\AionTool`.

## Windows-Warnung

Die Datei ist nicht signiert. Windows SmartScreen oder dein Virenscanner können beim ersten Start warnen.
