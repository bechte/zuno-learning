---
name: zuno-photo-to-cards
description: Use when the user provides photos of textbook pages, notes, vocabulary lists, or learning material and wants the content organized into Zuno courses and learning cards.
---

# Fotos in Zuno-Lernkarten umwandeln

Verwende die Bildverarbeitung des aktuellen KI-Clients, wenn sie verfügbar ist. Die Fotos werden dabei an den KI-Anbieter des Clients übermittelt. Wenn der Client keine Bilder analysieren kann, erkläre die Einschränkung und bitte um Text oder einen geeigneten Client. Audioerzeugung ist nicht Teil dieses Ablaufs.

## Ablauf

1. Bestimme mit Zuno den Zielkurs und lies dessen Kurslabels sowie vorhandene Lektionen/Sektionen. Frage nach dem Zielkurs, wenn er unklar ist.
2. Lies alle Bilder in der vom Nutzer vorgegebenen Reihenfolge. Ein Foto ist nicht automatisch eine neue Lektion, Sektion oder Seite.
3. Extrahiere nur sicher zuordenbare Lernkarten. Bewahre sichtbare Schreibweise und Alternativen. Erfinde keine Übersetzungen, Beispiele, Aussprache oder Seitenzahlen. Bei eindeutigen beschrifteten visuellen Lernbegriffen darf die fehlende Gegenseite ergänzt werden; Unsicheres auslassen oder markieren.
4. Weise Karten anhand sichtbarer Überschriften einer Lektion, Sektion und anhand tatsächlicher Buchseitenzahlen einer Seite zu. Referenzseiten in Übungen oder Texten sind keine Seitenzuordnung.
5. Zeige vor Änderungen eine kompakte Vorschau mit extrahierten Karten, unsicheren Stellen und vorgeschlagener Hierarchie. Frage, ob fehlende Struktur neu angelegt oder auf vorhandene Ziele gemappt werden soll.
6. Verwende vorhandene Elemente, wenn der Nutzer sie auswählt. Neue Elemente schrittweise anlegen und jeweils Zunos zurückgegebene IDs für die nächste Ebene verwenden.
7. Lege Karten in Sammelaufrufen an (maximal 2.000 pro Aufruf), standardmäßig mit `allow_partial=false`. Bei Fehlern den Stapel korrigieren und als Ganzes erneut senden; bei erneutem Senden auf mögliche Duplikate hinweisen.
8. Berichte angelegte IDs, Zuordnungen und Fehler knapp. Erst nach ausdrücklicher Zustimmung zusätzlich den Skill `zuno-card-enrichment` ausführen.

## Kursregeln

- Sprache: Front und Back entsprechen den Kurslabels. Übersetze nichts, was nicht eindeutig im Material steht.
- Wissen: Front und Back bleiben im jeweiligen Inhaltssprachkontext; nicht automatisch übersetzen.
- Beispiel- und Aussprachefelder nur übernehmen, wenn sie klar sichtbar und eindeutig zugeordnet sind.
- Kategorie nur wählen, wenn sicher; sonst leer lassen.
- Doppelte Einträge aus unterschiedlichen Bedeutungen behalten. Keine automatische Deduplizierung durch Zuno annehmen.
- Vorschau und finale Bestätigung sind getrennte Schritte. Erst nach Nutzerfreigabe schreiben.

Für detaillierte Erkennungsregeln siehe [Fotoimport-Regeln](references/photo-import-rules.md).
