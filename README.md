# Basel-entsieglungs-explorer
demo to highlight potential for removing stone and asphalt from public spaces and replace it with green
# Basel Entsiegelungs-Explorer

**Ein interaktiver Prototyp, der zeigt, wo in Basel Asphalt/Beton durch Bäume, Sträucher oder Grünflächen ersetzt werden könnte.**

🔗 **Live-Demo:** https://vava78.github.io/basel-entsiegelung-explorer/

## Worum geht es?

Die Stadt versiegelt viel öffentlichen Raum mit Asphalt und Beton — Plätze, breite Trottoirs, grosszügige Kreuzungsecken, Verkehrsinseln. Ein Teil davon wird funktional kaum genutzt und könnte begrünt werden. Diese App ist ein erster Schritt, um solche Flächen systematisch sichtbar zu machen — unter Berücksichtigung dessen, dass im Untergrund oft Leitungen liegen, die genug Abstand zu Baumwurzeln brauchen.

Der Prototyp zeigt zwei Flächentypen:
- **Plätze** (z.B. Marktplatz, Barfüsserplatz, Messeplatz) — grössere zusammenhängende versiegelte Flächen.
- **Strassenraum** (z.B. Aeschenplatz, Margarethenbrücke) — überbreite Trottoirstreifen, grosszügige Kreuzungsecken und Verkehrsinseln, die oft übersehen werden, obwohl sie in der Summe viel Potenzial bieten.

Ein Schieberegler simuliert den nötigen Mindestabstand zu Leitungen und rechnet live aus, wie viele Bäume bzw. Sträucher an einem Standort theoretisch Platz hätten.

## Was ist echt, was ist simuliert?

| Ebene | Status | Quelle (geplant) |
|---|---|---|
| Standorte der Plätze/Strassenabschnitte | ✅ echte Orte, reale Flächenmasse | Geoportal Basel-Stadt (Vermessungsamt), via WFS |
| Leitungsverlauf (Strom/Wasser/Gas) | ⚠️ **simuliert** | Leitungskataster — beschränkt öffentlich, Zugang über eGovernment-Vertrag nötig |
| Bestehende Bäume | ⚠️ **simuliert** | Stadtbaum-Kataster |
| Trottoir-/Eckengeometrie bei Aeschenplatz & Margarethenbrücke | ⚠️ grob angenähert, nicht vermessen | Curb-/Fassadenlinien aus WFS oder Digitalisierung ab Orthofoto |

**Wichtig:** Dieses Tool trifft aktuell keine verbindlichen Aussagen darüber, wo tatsächlich gepflanzt werden kann. Es zeigt die Methode — sobald echte Leitungsdaten eingespiesen werden, ersetzt eine echte räumliche Pufferberechnung (Polygon minus gepufferte Leitungslinien) die heutige grobe Schätzung.

## Wie geht es weiter?

1. Zugang zum Leitungskataster beantragen (Kanton Basel-Stadt, Grundbuch- und Vermessungsamt) — idealerweise im Rahmen einer Zusammenarbeit mit der Stadt, nicht als Einzelperson.
2. Reale Oberflächenpolygone (Plätze, Trottoirs) aus dem offenen Geoportal einbinden statt der handgezeichneten Demo-Rechtecke.
3. Echte Baumstandorte und Bodenkennwerte (Versickerung, Bodentiefe) ergänzen.
4. Die Scoring-Logik von einer Flächenschätzung zu einer echten Geometrieoperation (`turf.buffer` + `turf.difference`) ausbauen.
5. Priorisierung nach Hitzeinsel-Daten, Fussgängerfrequenz und Quartier-Wünschen ergänzen.

## Technik

Einzelne HTML-Datei, läuft komplett im Browser. Kein Server, keine Datenbank.
- [Leaflet](https://leafletjs.com/) für die Karte
- [Turf.js](https://turfjs.org/) für Flächen- und Geometrieberechnungen
- OpenStreetMap als Kartenhintergrund

Lokal öffnen: einfach `index.html` im Browser starten — keine Installation nötig.

## Lizenz

MIT — siehe [LICENSE](LICENSE). Frei nutzbar, auch für die Stadt oder Dritte, die das weiterbauen möchten.

## Kontakt / Feedback

Dieser Prototyp wurde als Diskussionsgrundlage erstellt, nicht als fertiges Produkt. Rückmeldungen, Korrekturen an den Standortdaten und Hinweise auf bessere Datenquellen sind willkommen.
