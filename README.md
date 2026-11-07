# 📦 Kisten-Tracker

Ein kleiner Tracker für Fortnite (Treasure Hunters): Zähle pro Runde, wie viele Truhen du geöffnet hast, wie viele Gizmos und Pirate Shop Token du bekommen hast. Die Seite rechnet dir Gesamtzahlen, Durchschnitt pro Runde und die Gizmo-Chance pro Kiste aus.

Es ist eine einzelne Datei (`index.html`), ohne Server, ohne Konto, ohne Installation.

## Funktionen

- **Runden:** Runde starten, Kisten per Tippen zählen, Gizmos und Pirate Shop Token mit + zählen, Runde beenden.
- **Abschlussseite** mit den Zahlen der Runde und dem neuen Gesamtstand.
- **Statistik:** Kisten, Gizmos und Token insgesamt, Ø pro Runde und Gizmo-Chance pro Kiste in %.
- **Rundenliste** mit Bearbeiten (falls du etwas vergessen hast) und Löschen.
- **Startwerte:** Zahlen, die du schon vor dem Tracking hattest.
- **Wiederherstellungs-Code:** ein Text, mit dem du alle Daten auf jedem Gerät zurückholst.
- **Sichern und Laden** als Datei als zweite Möglichkeit.

## Auf GitHub veröffentlichen (GitHub Pages)

1. Auf GitHub ein neues Repository anlegen, zum Beispiel `kisten-tracker`.
2. `index.html` hochladen (die `README.md` ist optional) (Add file → Upload files).
3. Im Repository: **Settings → Pages**.
4. Bei „Build and deployment“ als Source **Deploy from a branch** wählen, Branch `main`, Ordner `/ (root)`, speichern.
5. Nach ein bis zwei Minuten ist die Seite erreichbar unter `https://DEIN-NAME.github.io/kisten-tracker/`.

Diesen Link kannst du an Freunde schicken. Auf dem Handy lässt er sich im Browser über „Zum Home-Bildschirm hinzufügen“ wie eine App ablegen.

## Wo liegen die Daten?

Jeder, der die Seite öffnet, hat **seine eigenen Daten**. Sie werden im Browser des jeweiligen Geräts gespeichert (`localStorage`) und sind für niemand anderen sichtbar. Das heißt auch:

- Ein anderes Gerät oder ein anderer Browser startet bei 0.
- Löschst du die Browserdaten, sind die Zahlen weg. Sichere deshalb ab und zu.
- Die Seite erinnert dich daran, wenn die letzte Sicherung mehr als 7 Tage her ist. „Später“ blendet den Hinweis für 7 Tage aus.
- Im privaten Modus des Browsers kann das Speichern blockiert sein. Dann steht oben „Speichern nicht möglich“.

## Daten sichern und auf ein neues Gerät holen

Am einfachsten geht es mit dem **Wiederherstellungs-Code**:

1. Auf der Startseite unten **Startwerte & Sicherung** öffnen.
2. **Code erzeugen** und **Kopieren** tippen.
3. Den Code irgendwo speichern: Notizen-App, Chat mit dir selbst oder Mail. Er ist ein langer Text, der mit `KT1.` beginnt (bei 400 Runden etwa 2000 Zeichen).
4. Auf einem neuen Gerät oder nach einem Datenverlust: Seite öffnen, bei **Code einfügen** den Code einfügen und **Wiederherstellen** tippen.

Die Wiederherstellung ersetzt die Daten auf dem Gerät. Hat das Gerät schon Daten, fragt die Seite vorher nach. Ein unvollständig kopierter Code wird erkannt und abgelehnt. Zeilenumbrüche, die Chat-Apps einfügen, stören nicht.

Als zweite Möglichkeit gibt es **Sichern (Datei)** und **Laden**. Das ist dasselbe, nur als `.json`-Datei.

Es gibt keinen Server und kein Konto. Die Daten verlassen dein Gerät nur, wenn du den Code oder die Datei selbst weitergibst. Wer den Code hat, kann die Daten lesen, bewahre ihn also nur dort auf, wo du ihn auch sonst aufbewahren würdest. Der Code enthält Zahlen und Zeitpunkte deiner Runden, sonst nichts.

## Hinweise

- Die **Gizmo-Chance** ist Gizmos geteilt durch Kisten. Gizmos kommen auch aus Quests und anderen Quellen, nicht nur aus Truhen. Zählst du alle mit, fällt die Chance höher aus als für Truhen allein.
- Das Zählen ist bewusst manuell. Automatisches Auslesen des Spiels ist nicht erlaubt und kann zur Kontosperre führen.
- Fan-Projekt, nicht mit Epic Games verbunden. Fortnite ist eine Marke von Epic Games.
