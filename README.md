# 📦 Kisten-Tracker

Ein kleiner Tracker für Fortnite (Treasure Hunters): Zähle pro Runde, wie viele Truhen du geöffnet hast, wie viele Gizmos und Pirate Shop Token du bekommen hast. Die Seite rechnet dir Gesamtzahlen, Durchschnitt pro Runde und die Gizmo-Chance pro Kiste aus.

Es ist eine einzelne Datei (`index.html`), ohne Server, ohne Konto, ohne Installation.

## Funktionen

- **Runden:** Runde starten, Kisten per Tippen zählen, Gizmos und Pirate Shop Token mit + zählen, Runde beenden.
- **Abschlussseite** mit den Zahlen der Runde und dem neuen Gesamtstand.
- **Statistik:** Kisten, Gizmos und Token insgesamt, Ø pro Runde und Gizmo-Chance pro Kiste in %.
- **Rundenliste** mit Bearbeiten (falls du etwas vergessen hast) und Löschen.
- **Startwerte:** Zahlen, die du schon vor dem Tracking hattest.
- **Eigener Name (optional):** Daten werden online unter einem selbst gewählten Namen gesichert und überall damit zurückgeholt.
- **Wiederherstellungs-Code:** ein Text, mit dem du alle Daten auf jedem Gerät zurückholst.
- **Sichern und Laden** als Datei als zweite Möglichkeit.

## Auf GitHub veröffentlichen (GitHub Pages)

1. Auf GitHub ein neues Repository anlegen, zum Beispiel `kisten-tracker`.
2. `index.html` und `README.md` hochladen (Add file → Upload files).
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

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | die ganze App |
| `config.js` | Zugangsdaten für die Online-Sicherung (optional, zunächst leer) |
| `setup.sql` | richtet die Online-Sicherung in Supabase ein (optional) |
| `README.md` | diese Anleitung |

Ohne `config.js`-Werte funktioniert alles wie beschrieben, nur ohne Online-Sicherung. Dann gelten Wiederherstellungs-Code und Datei-Sicherung.

## Online-Sicherung mit eigenem Namen (optional, einmalige Einrichtung)

Damit kann sich jeder einen Namen wie `kyle-kisten-26` aussuchen und seine Daten auf jedem Gerät damit zurückholen. Dafür braucht es einen kleinen Online-Speicher. Hier mit **Supabase** (hat einen kostenlosen Tarif, prüfe die aktuellen Bedingungen auf der Seite):

1. Auf [supabase.com](https://supabase.com) ein Konto anlegen und ein **neues Projekt** erstellen (Name und Datenbank-Passwort frei wählen, Region EU).
2. Im Projekt links **SQL Editor → New query**. Den kompletten Inhalt von `setup.sql` einfügen und **Run** drücken. Es muss „Success“ erscheinen.
3. **Project Settings → API**: dort stehen die **Project URL** (`https://….supabase.co`) und der Schlüssel **anon public**.
4. In `config.js` beide Werte zwischen die Anführungszeichen eintragen und die Datei auf GitHub speichern (Commit).
5. Nach ein bis zwei Minuten ist die Online-Sicherung auf der Seite unter **Startwerte & Sicherung → Mein Name** aktiv.

So nutzt man es:

- **Name anlegen:** Name eintippen, „Name anlegen“. Ab dann sichert die Seite jede Änderung automatisch online (oben steht „☁ Online gesichert“).
- **Auf neuem Gerät:** Name eintippen, „Mit Namen laden“. Die Daten werden geholt und das Gerät bleibt verbunden.
- **Mehrere Geräte:** Wer sich mit demselben Namen verbindet, sieht denselben Stand. Es gilt jeweils der zuletzt gespeicherte. Zwei Geräte gleichzeitig zu bedienen wird deshalb nicht empfohlen. Die Seite holt beim Öffnen und beim Zurückkehren in den Tab den neuesten Stand.
- **Offline:** Ohne Netz bleibt alles lokal gespeichert. Die Seite sichert später automatisch online nach.
- **Trennen:** Beendet die Verbindung auf diesem Gerät. Der Online-Eintrag bleibt bestehen.

**Sicherheit, bitte ehrlich lesen:**

- Der Name ist wie ein Passwort. Es gibt keine PIN. Wer deinen Namen kennt oder errät, kann deine Daten sehen und überschreiben. Wähle also nichts wie `kyle`, sondern etwas Eigenes.
- Niemand kann eine Liste aller Namen auslesen. Man kann nur mit einem exakt richtigen Namen etwas abrufen.
- Der Dienst speichert zu jedem Namen zusätzlich einen älteren Stand (mindestens 1 Stunde alt). Hat jemand deine Daten überschrieben, findest du ihn im Supabase-Dashboard unter **Table Editor → trackers → Spalte `prev`**.
- Der Schlüssel `anon public` in `config.js` ist dafür gedacht, öffentlich zu sein. Der direkte Zugriff auf die Tabelle ist gesperrt, nur die drei Funktionen aus `setup.sql` sind erlaubt.
- Im kostenlosen Supabase-Tarif können Projekte nach längerer Inaktivität pausiert werden (aktuelle Regeln stehen in der Supabase-Dokumentation). Im Dashboard lässt sich ein pausiertes Projekt wieder starten. Sichere trotzdem zusätzlich mit dem Code.

## Daten sichern und auf ein neues Gerät holen (ohne Online-Speicher)

Am einfachsten geht es mit dem **Wiederherstellungs-Code**:

1. Auf der Startseite unten **Startwerte & Sicherung** öffnen.
2. **Code erzeugen** und **Kopieren** tippen.
3. Den Code irgendwo speichern: Notizen-App, Chat mit dir selbst oder Mail. Er ist ein langer Text, der mit `KT1.` beginnt (bei 400 Runden etwa 2000 Zeichen).
4. Auf einem neuen Gerät oder nach einem Datenverlust: Seite öffnen, bei **Code einfügen** den Code einfügen und **Wiederherstellen** tippen.

Die Wiederherstellung ersetzt die Daten auf dem Gerät. Hat das Gerät schon Daten, fragt die Seite vorher nach. Ein unvollständig kopierter Code wird erkannt und abgelehnt. Zeilenumbrüche, die Chat-Apps einfügen, stören nicht.

Als zweite Möglichkeit gibt es **Sichern (Datei)** und **Laden**. Das ist dasselbe, nur als `.json`-Datei.

Dieser Code und die Datei-Sicherung bleiben auf deinem Gerät. Es gibt dabei keinen Server und kein Konto. Wer den Code hat, kann die Daten lesen, bewahre ihn also nur dort auf, wo du ihn auch sonst aufbewahren würdest. Der Code enthält Zahlen und Zeitpunkte deiner Runden, sonst nichts.

## Hinweise

- Die **Gizmo-Chance** ist Gizmos geteilt durch Kisten. Gizmos kommen auch aus Quests und anderen Quellen, nicht nur aus Truhen. Zählst du alle mit, fällt die Chance höher aus als für Truhen allein.
- Das Zählen ist bewusst manuell. Automatisches Auslesen des Spiels ist nicht erlaubt und kann zur Kontosperre führen.
- Fan-Projekt, nicht mit Epic Games verbunden. Fortnite ist eine Marke von Epic Games.
