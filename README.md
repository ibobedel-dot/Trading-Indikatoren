# Trading – Indikatoren

Eigene TradingView-Indikatoren (Pine Script v6) für Pepperstone-Märkte:
GER40, US500, NAS100, US30, XAUUSD, XAGUSD, SPOTCRUDE.

## Ibo LTF Entry System 1.1

Datei: `indikatoren/ibo-ltf-entry-system-1.1.pine` (Version 1.0 liegt weiter daneben) · Zeitrahmen: M1, M2, M5

**Ablauf**
1. **Liquidität:** Signifikante Swing-Hochs (BSL) und Swing-Tiefs (SSL). Jedes Level wird nur einmal gesweept.
2. **Sweep:** *Grab* heißt, die Kerze nimmt das Level und schließt wieder dahinter. *Sweep* heißt, der Preis bleibt mindestens X Minuten jenseits des Levels und höchstens Y Minuten.
3. **Plan:** Die erste FVG in Gegenrichtung nach dem Sweep wird zum Plan mit Entry, SL und TP. Pro Sweep gibt es einen Plan.
4. **Entry:** Obere Kante, Mitte oder untere Kante der FVG. Der SL liegt hinter der FVG, mit Puffer und Spread. Der TP liegt am nächsten signifikanten Swing, mit Mindest-RR.
5. **Ende:** Der Plan endet mit der Berührung des Limits oder wird ungültig (TP vor der Berührung erreicht oder Zeit abgelaufen). Danach wird das Ergebnis (TP/SL) als Historie gezeigt.

**Filter & Extras**
- Trendfilter per Strukturbruch: Aus, M5, M15, H1 (Standard) oder H4
- Profile: Auto (M1/M2/M5) oder Manuell
- Noten A/B/C, Alarme als Klartext oder JSON (Setup, Update, Nähe, Touch, Ungültig)
- Status-Tabelle oben rechts, optional mit Lot-Rechner und Statistik

Alle Signale kommen nur auf Kerzenschluss. Die Zeiten gelten für Europe/Vienna.

## Versionen

| Version | Änderung |
|---|---|
| 1.0 | Erste Version auf GitHub |
| 1.1 | **Trend-Filter:** Gegen-Trend-Setups werden nur markiert (⚠ GEGEN-TREND, graues Label) statt gesperrt; Alarme nur für Mit-Trend-Setups; Trend-Pivot-Stärke 5, getrennt von den Setup-Swings. **Tabelle:** Standardgröße „small“, neue Einstellung „Tabellengröße“. **Sweep:** Close-Back innerhalb von 1–3 Kerzen (Grab), Tiefe 0,1–1 × ATR, Levels nach Stärke gewichtet (+1 Note bei starkem Level, optional nur starke Levels), Reaktion per Verdrängungskerze ≥ 0,7 × ATR, abgeholte Levels sind verbraucht. Alle Werte einstellbar. |
| 1.2 | Kurze Labels (nur offene Pläne) und kurze Alarme für Watchlists, Plan ungültig bei Bruch der FVG, Schlüssel-Levels (Vortag, Vorwoche, Asia), Session-Filter für Alarme (London, NY AM, NY PM), Zähler inkl. Ergebnis in R, 26 Einstellungen, kein Spread, Standard: Trend H4 und FVG 0,3 × ATR (auf XAUUSD M5 optimiert). |

## In TradingView verwenden

Den Inhalt der `.pine`-Datei kopieren, im Pine-Editor einfügen und auf **Zum Chart hinzufügen** klicken.
