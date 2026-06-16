# GoMausi 🐭

Persönlicher Trainings-Tracker mit **Fokus auf sichtbaren Fortschritt** — gebaut für eine ambitionierte Athletin.

Single-File-PWA (HTML/JS/CSS, Vanilla, keine Build-Tools), mobile-first, offline-fähig, rein lokale Datenhaltung (LocalStorage). Komplett unabhängig von der SUB4-App (eigener Speicher-Key, eigene PWA).

## Trainingsbereiche

- **Leichtathletik** (Di + Do, opt. So) — pro Einheit Schwerpunkt(e) erfassen (Sprint, Start, Technik, Hürden …) → Historie pro Schwerpunkt. Sprint-Zeiten (30/60/100/150/200 m) werden als Verlaufschart getrackt (schneller = Fortschritt).
- **Kraft / Studio** (3×/Woche) — Übung + Gewicht + Sätze + Wdh. Pro Übung Verlauf von Top-Satz, geschätztem 1RM und Volumen.
- **Zone-2-Lauf** (1–2×/Woche) — Herzstück: Pace, Ø-/Max-Puls, Distanz, Dauer.
  - **Pace @ Ziel-Puls** (auf den Zone-2-Ziel-Puls normalisierte Pace) als Headline — sinkt über Wochen = Fortschritt.
  - **Effizienz-Faktor** (Meter/Min pro Schlag) als robuster Trend.
  - **Zone-2-Disziplin** (Ø-Puls vs. Ziel, opt. Zeit im Zielbereich).

## Dashboard

Wochenübersicht Soll vs. Ist je Bereich, Konsistenz-Streak, und das zentrale Effizienz-Erfolgs-Feedback ("X % schneller bei Puls Y als vor 4 Wochen").

## Lokal starten

```bash
node server.js   # http://localhost:4180
```

## Einstellungen

Beim ersten Start **Zone-2-Ziel-Puls** setzen (Default 150; Helfer „180 − Alter" = MAF). Wochen-Soll, Schwerpunkte und Sprint-Distanzen sind editierbar. Daten lassen sich als JSON exportieren/importieren.
