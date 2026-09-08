# Warum du jetzt ein Ziel bist — Web-Fassung

Quelle: `Warum du jetzt ein Ziel bist - Essay.html` (A4-Seitenfassung, 794 × 1123 px,
51 `<section class="page">`, zweispaltiger Satz, absolut positionierte Kopf- und Fußzeilen).

## Dateien

| Datei | Zweck |
|---|---|
| `warum-du-jetzt-ein-ziel-bist.html` | Standalone, in sich geschlossen (Bilder als Data-URI) |
| `warum-du-jetzt-ein-ziel-bist.cms.html` | Reiner Inhaltsblock, alle Selektoren unter `.essay` |
| `bilder/reisepass.webp`, `bilder/portraet.webp` | die beiden Rasterbilder als Einzeldateien, falls das CMS lieber Uploads als Data-URIs will |

Die auf assecura.xyz ausgelieferte Fassung entsteht aus derselben Vorlage; sie
liegt im Projekt der Webseite und bindet Bilder und Stylesheet als eigene
Dateien ein statt als Data-URI.

## Was aus der Seitenfassung entfallen ist

1. **Seitenformat.** Die 51 festen A4-Seiten (`794 × 1123 px`) sind zu 16 Kapitel-Sections
   plus Kopf, Inhaltsverzeichnis, Abgrenzung, vier Teil-Zwischentiteln, Schluss und Anhang
   zusammengeführt. Kapitel, die über mehrere Seiten liefen (z. B. `kap-3`, `kap-3-b`,
   `kap-3-ai`, `kap-3-ai-int`, `kap-3-ai-ext`, `kap-3-ai-files`, `kap-3-ai2`), sind jetzt
   eine Section `#kapitel-03`.
2. **Laufende Kopfzeilen.** 46 × „WARUM DU JETZT EIN ZIEL BIST · KAPITEL 0X".
3. **Fußzeilen und Seitenzahlen.** 45 × „0XTHANER × ASSECURA · KAPITEL 0X · 17"
   sowie die Fußzeile der Inhaltsseite („ESSAY / ANALYSE · SEPTEMBER 2026 · …​ · SEITE 2").
4. **Seitenrand-Marker.** 14 × der angeschnittene Kapitelreiter am rechten Blattrand
   (`showEdgeMarks`).
5. **Dekorative Riesenziffern** auf den vier Teil-Trennseiten (150 px, `#1b1c22`, hinter
   dem Text). Die Kapitelnummer selbst bleibt — im Kapitelkopf und im Inhaltsverzeichnis.
6. **Titel-Cover im Seitenformat.** Titel, Untertitel, Autorzeile, Version und Lesedauer
   stehen jetzt als normaler Seitenkopf im Textfluss; der radiale Farbverlauf des Covers
   entfällt.
7. **Zweispaltiger Satz.** Die 16 `column-count: 2`-Container sind aufgelöst; der Text
   läuft einspaltig. `orphans`/`widows`/`break-inside`/`hyphens: manual` sind gegenstandslos
   und entfernt.
8. **Druck- und Blattlogik.** Feste Höhen, `position: absolute`, vertikales Ausrichten per
   `margin: auto 0` (füllte die Blatthöhe), `@media print`-Regeln für das 294-mm-Blatt.
9. **Navigationsschiene links** (`.navrail` mit TITEL / INHALT / 01 … ANHANG). Ihre Funktion
   übernimmt das Inhaltsverzeichnis als Sprungliste.
10. **Ein leerer Absatz** (`<p><br></p>`) am Ende der Motiv-Tabelle in Kapitel 1 — reiner
    Abstandshalter zum Blattfuß, ohne Text.

## Wurde Text angepasst?

**Nein.** Kein Wort, keine Zahl, keine Quelle, keine Überschrift, keine Kapitelreihenfolge.
Der sichtbare Text der Web-Fassung ist zeichenweise identisch mit dem der Seitenfassung
(70 857 Zeichen, automatisch gegengeprüft) — einschließlich Bindestrichen statt
Geviertstrichen und deutscher Anführungszeichen. Absätze mussten nicht zusammengeführt
werden: der Spaltensatz der Vorlage war CSS-basiert, kein Absatz war über eine Spalten-
oder Seitengrenze zerschnitten.

Alle elf Abbildungen (ABB. 1, 2, 2.1, 3, 4, 5, 5.1, 6, 6.1, 7, 8) sind vollständig
übernommen, samt Bildunterschriften, Methodenhinweisen und der Kennzeichnung
„SCHEMATISCH" bzw. „ILLUSTRATION". Die neun Diagramme bleiben Inline-SVG (Knoten für
Knoten unverändert, nur `sc-camel-view-box` → `viewBox` zurückgesetzt, `role="img"` und
`aria-label` erhalten). Die dreizehn Tabellen, elf Hinweis-/Quellenboxen, drei Merksätze
und das Schlusszitat bleiben eigene, abgesetzte Blöcke.

## Zwei technische Anpassungen, die keine Textänderung sind

- **Rasterbilder neu kodiert.** Reisepass und Porträt lagen als PNG mit 2,9 MB bzw. 2,7 MB
  (1312 × 1199 und 1672 × 941 px) vor. Für das Web sind sie auf 1100 px Breite skaliert und
  als WebP gespeichert (345 KB / 199 KB). Bildinhalt und Alt-Texte unverändert;
  eingebunden mit `max-width: 100%; height: auto`.
- **Anker umbenannt.** Die Sprungziele heißen jetzt `#kapitel-01` … `#kapitel-14`,
  `#abgrenzung`, `#schluss`, `#anhang`. Die Verweise im Quellenanhang („Zitiert in
  Kapitel 2") zeigen darauf. Die alten Seiten-IDs (`kap-3-ai-ext` usw.) bestehen als
  unsichtbare Anker an ihrer ursprünglichen Stelle weiter, damit ältere Links nicht brechen.

## Layout und Technik

- Einspaltig, Textbreite 41 rem (≈ 70 Zeichen), zentriert, Zeilenhöhe 1.7.
- Fließtext 18 px auf Desktop, 17 px ab 720 px Breite; Lead 20,5 px / 18,5 px.
- Keine festen Breiten oder Höhen, `max-width` statt `width`, keine Viewport-Einheiten
  für Schriftgrößen. Brauchbar von 360 px bis Desktop.
- Abbildungen dürfen die Textspalte überragen (52 rem statt 41 rem) und passen auf
  Mobil vollständig hinein. Tabellen stapeln unter 720 px Spalte für Spalte.
- Farben, Schriften und Abstände aus der Vorlage (`#050506` Grund, `#9184d9` Akzent,
  Satoshi/Inter). Kein Redesign.
- Fonts über `<link>` (Google Fonts für Inter, Fontshare für Satoshi). Fallen die Links
  weg, greift der System-Fallback der Schriftliste.
- Semantisch: `article`, `section`, `header`, `nav`, `h1`–`h3`, `figure`/`figcaption`,
  `table`/`th`/`td`, `blockquote`, `aside`. Alt-Texte an beiden Bildern, `role="img"` und
  `aria-label` an allen neun SVG, sichtbarer Fokus-Stil, Fließtext-Kontrast ≈ 18:1.
- Kein PDF, kein iframe, kein Framework, kein Build-Schritt.
