# GoMausi 🐭

Persönlicher Trainings-Tracker mit **Fokus auf sichtbaren Fortschritt** — gebaut für eine ambitionierte Athletin. Alle Sparten gleichwertig: **Gym, Leichtathletik, Lauf** + allgemeine Fitness.

Single-File-PWA (HTML/JS/CSS, Vanilla, keine Build-Tools), mobile-first, offline-fähig, rein lokale Datenhaltung (LocalStorage). Komplett unabhängig von der SUB4-App.

**Live:** https://jduscher-netizen.github.io/gomausi/

## Bereiche

- **Dashboard** — „Diese Woche – das fehlt dir noch" (Soll − Ist je Sparte + wiederkehrende Einheiten, antippbar zum Eintragen), Wochen-Ringe, Trainingslast (Zeit + Ø-Puls), Fortschritt je Bereich, Körper/Zyklus.
- **Lauf** — Zone-2: Pace @ Ziel-Puls + Effizienz-Faktor, Pace/Puls-Verlauf, „Zeit im Ziel-Puls".
- **Kraft** — Übung + Gewicht + Sätze + Wdh → Top-Satz/1RM/Volumen-Verlauf je Übung; HF + Zeit.
- **Leichtathletik** — Schwerpunkt(e) + Sprint-Zeiten (30–200 m) als Verlauf; HF + Zeit.
- **Körper** — Gewichts-Verlauf + **Zyklus** (Phase, Ø-Länge, Vorhersage; phasenbewusste Hinweise zu Energie/Leistung).
- **Sonstige** — flexibler Typ (Rad, Padel, Schwimmen …) + wiederkehrende Wocheneinheiten.

## Apple-Watch-Daten importieren

Apple Health hat **keinen direkten Web-Zugriff** (Apple-Plattformgrenze). Drei kostenlose Wege:

1. **Strava** (Mehr → Strava verbinden): zieht neue Aktivitäten automatisch beim Öffnen, du wählst je Aktivität den Bereich. Läufe inkl. Pace/Puls + „Zeit im Ziel-Puls".
2. **GPX/TCX-Datei** (Mehr → Datei importieren): aus Health/Drittanbieter-Apps.
3. **Apple-Kurzbefehl → JSON** (Mehr → Apple Health (JSON)): siehe unten.

### Kurzbefehl bauen (einmalig, ~10 min)

In der **Kurzbefehle**-App einen Shortcut „GoMausi Export" erstellen:

1. **„Health-Beispiele suchen"** (Find Health Samples) → *Workouts*, sortiert nach Enddatum, Limit z. B. 10.
2. **„Health-Beispiele suchen"** → *Körpergewicht* (Body Mass), Limit z. B. 5.
3. Beides mit **„Text"** / **„Wörterbuch"** in dieses JSON formen:
   ```json
   {
     "workouts": [
       {"type":"Run","date":"2026-06-16","durationSec":1800,"distanceKm":4.2,"avgHr":150,"maxHr":165,"name":"Lauf"}
     ],
     "weight": [
       {"date":"2026-06-16","kg":62.4}
     ]
   }
   ```
4. Am Ende **„In die Zwischenablage kopieren"** (dann in GoMausi unter *Mehr → Apple Health (JSON)* einfügen → Einlesen) **oder** **„Datei speichern"** (.json) und in GoMausi laden.
5. Optional als **Automation** „Wenn ein Workout endet → diesen Kurzbefehl ausführen".

Felder sind tolerant: `durationMin`/`distanceM`/`hr` etc. werden auch erkannt. **Gewichte/Sätze/Wdh & Sprint-Zeiten** erfasst die Watch nicht — die bleiben manuell. Import liefert **HF + Zeit** (+ beim Lauf Pace/Distanz).

## Lokal starten

```bash
node server.js   # http://localhost:4180
```

## Einstellungen

Beim ersten Start **Zone-2-Ziel-Puls** setzen (Default 150; „180 − Alter" = MAF). Wochen-Soll, wiederkehrende Einheiten, Schwerpunkte, Sprint-Distanzen und Zyklus-Tracking sind editierbar/abschaltbar. Daten als JSON exportier-/importierbar.
