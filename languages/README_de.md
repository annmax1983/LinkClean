# LinkClean - Link-Reiniger

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Vor dem Teilen den Tracking-Ballast entfernen. Link einfügen, und LinkClean nennt jeden entfernten Parameter, packt Weiterleitungen und AMP-Seiten aus und gibt einen sauberen Link zurück. Alles läuft auf deinem Gerät — kein Link verlässt den Browser.

## Funktionen

- **Ein Einfügen, ein sauberer Link** — URL einfügen oder den aktuellen Tab übernehmen.
- **Nichts verschwindet still** — jeder entfernte Parameter wird mit Namen genannt, samt dem Wert, den die Seite erhalten hätte.
- **Kopie als URL oder Markdown** — Markdown entsteht aus dem echten Seitentitel: `[Titel](URL)`.
- **Stapelmodus** — nimmt eine Liste von URLs, aber auch einen Absatz, eine E-Mail oder einen Chatverlauf. Nur die Links werden ersetzt, der Text drumherum bleibt unverändert.
- **Funktionsparameter bleiben** — entfernt werden nur 61 bekannte Tracking-Namen und 12 Präfix-Familien (`utm_`, `ga_`, `mtm_`, `piwik_`, `_hs` und weitere).
- **Pro: Weiterleitungen auflösen** — Google, YouTube, Facebook, Reddit, DuckDuckGo, LinkedIn, Zhihu, Douban, Jianshu, SSPAI, VK, Slack, Outlook Safe Links, Skimlinks, Tumblr, Medium, Pocket sowie Bing, Weibo, Proofpoint und die allgemeine Form `/redirect?url=` — lokal, rekursiv, höchstens drei Sprünge.
- **Pro: AMP auflösen** — `cdn.ampproject.org/c/s/`, `google.com/amp/s/` und ein abschließendes `/amp` führen zur kanonischen Seite zurück.
- **Pro: Seitenregeln** — `amazon.com` behält `th` und `psc`, alles andere wird gestrichen. Die spezifischste Domain gewinnt, Subdomains erben sie. Ein Klick auf einen entfernten Parameter hält ihn dauerhaft auf dieser Seite.
- **Pro: Verlauf und Zähler** — Verlauf nach Link, Titel oder Domain durchsuchen, Originallink zurückkopieren, als JSON exportieren; dazu Zähler für bereinigte Links und entfernte Parameter.

## Free vs. Pro

| | Free | Pro |
|---|---|---|
| Einzelne Links bereinigen (volle eingebaute Liste) | ✅ | ✅ |
| Markdown-Kopie / Zwischenablage / Fragment-Schalter | ✅ | ✅ |
| Automatisches Kopieren nach dem Bereinigen | ✅ | ✅ |
| Stapelgröße | 10 Links | unbegrenzt |
| TXT-Export | ✅ | ✅ |
| CSV- / JSON-Export | — | ✅ |
| Absätze mit mehreren Links | bis 10 | ✅ |
| Weiterleitungen und AMP auflösen | nur Hinweis | ✅ |
| Seitenregeln + Ein-Klick-Behalten | — | ✅ |
| Verlauf | 10 Einträge | 100, mit Suche und Original-Link |
| Regelpakete importieren/exportieren | — | ✅ |
| Aufschlüsselung der meistgenutzten Seiten | — | ✅ |

Ein Lizenzschlüssel aktiviert zwei Browser; entfernst du ihn, wird der Platz wieder frei. Prüfung etwa alle zwei Stunden, offline gilt die zwischengespeicherte Lizenz; eine fehlgeschlagene Prüfung sperrt nichts.

## So funktioniert es

1. Auf das LinkClean-Symbol klicken. Trägt die aktuelle Seite Tracking-Parameter, ist das Feld bereits gefüllt.
2. Auf „Link bereinigen" drücken. Das Ergebnis zeigt die saubere URL, jeden entfernten Parameter als Chip und — mit Lizenz und bei einer Weiterleitung — die aufgelöste Kette.
3. Link kopieren, als Markdown kopieren, öffnen oder denselben Link in den Stapelmodus geben.
4. Soll ein Parameter bleiben: im Ergebnis anklicken, und er landet dauerhaft auf der Behalten-Liste dieser Seite.

## Datenschutz

- Links verlassen den Browser nie. Jede Regel ist eine lokale String-Operation; **es wird keine Weiterleitung abgerufen, um ihr Ziel zu erfahren**.
- Keine Analyse, keine Telemetrie, keine Werbe-IDs, keine Tracking-Pixel.
- Verlauf, Einstellungen und Zähler liegen in `chrome.storage.local` und lassen sich jederzeit löschen.
- Die einzige Netzwerkanfrage ist die Lizenzprüfung: Schlüssel, zufällige Installationskennung, Plugin-ID und grundlegende Browser-Metadaten.
- Die Zwischenablage wird nur beim Drücken von „Einfügen" gelesen und nur beim Kopieren oder bei aktiviertem automatischem Kopieren geschrieben.

## Berechtigungen

| Berechtigung | Zweck |
|---|---|
| `storage` | Einstellungen, eigene Regeln, Verlauf und Lizenzstatus lokal speichern |
| `activeTab` | Die URL der aktuellen Seite lesen, erst nach einem Klick auf das Symbol |
| `clipboardWrite` | Den sauberen Link beim Kopieren oder bei automatischer Kopie schreiben |
| `clipboardRead` | Die Zwischenablage nur beim Drücken von „Einfügen" lesen, nie im Hintergrund |
| `https://api.annmax1983.com/*` | Nur Lizenzaktivierung und -prüfung, niemals ein Link |

Kein Content-Skript, kein `<all_urls>`-Hostzugriff, keine `tabs`- und keine `downloads`-Berechtigung — LinkClean kann den Text keiner Seite sehen.

## Unterstützte Browser

Chrome und Edge (Manifest V3, Chrome 116+). Eine Firefox-Version ist geplant.

## Entwicklung

```bash
npm install        # nur Entwicklungsabhängigkeit: terser
npm run locales    # erzeugt die sechs _locales aus tools/make-locales.js
npm run icons      # erzeugt die Icons
npm test           # node --test: Bereinigen, Weiterleitungen, Seitenregeln, i18n, Popup-Verdrahtung
npm run build      # minifizieren + packen → publish/linkclean-v{version}.zip
node tools/shoot.js  # 1280×800-Store-Screenshots und Promo-Bild im echten Chrome rendern
```

> Dieses Repository dient der Projektvorstellung; der vollständige Quellcode wird nicht veröffentlicht. Bitte installiere LinkClean über die offiziellen Browserstores.

## Links

- Website: https://annmax1983.com
- Erweiterungsseite: https://annmax1983.com/extensions/linkclean
- Lizenz und Preis: https://annmax1983.com/checkout?plugin=linkclean
