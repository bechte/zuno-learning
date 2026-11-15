# Fotoimport-Regeln für Zuno

Diese Client-Anleitung folgt dem Fotoimport-Vertrag aus Zunos `AiPromptCatalog::photoImport` und `spec-photo-capture.md`.

## Analyse

- Verarbeite die geordneten Bilder als zusammenhängende Folge. Berücksichtige Orientierung, Perspektive, Spalten, Tabellen, Überschriften, Lernboxen, tatsächliche Seitenränder und abgeschnittene Inhalte.
- Eine neue Datei ist nicht automatisch eine neue Buchseite, Lektion, Sektion oder Unit. Überschriften gelten für nachfolgende Karten, auch über Bildgrenzen hinweg.
- Ordne Begriffe nur zu, wenn dieselbe Zeile, Tabelle, Beschriftung oder Gestaltung die Verbindung klar zeigt.
- Extrahiere vollständige Vokabelpaare, eindeutig beschriftete Lernbegriffe und passende Beispielsätze/Aussprache, wenn diese vorhanden sind. Keine bloßen Kapitelüberschriften, Grammatikhinweise oder redaktionellen Fließtexte.
- Übernimm sichtbare Schreibweisen. Erhalte Artikel, Präpositionen, Satzzeichen, Wortbestandteile, Mehrwortausdrücke und ausdrücklich genannte Alternativen.
- Ergänze keine fehlenden Bedeutungen, Übersetzungen, Beispiele, Aussprache oder redaktionellen Informationen aus allgemeinem Wissen. Ausnahme: Bei einem eindeutig als Lerninhalt gestalteten Bildbegriff darf die fehlende Gegenseite übersetzt werden; bei Mehrdeutigkeit auslassen.
- Exakte Duplikate nur in der Vorschau kenntlich machen; unterschiedliche Bedeutungen nicht zusammenführen.

## Zielstruktur und Seiten

- Unit/Lektion/großes Kapitel → Lektion; Kapitel/Part/Teil/Unterabschnitt → Sektion.
- `page_label` ist ausschließlich die tatsächliche gedruckte Buchseitenzahl, etwa `P34`. Referenzangaben wie `p. 4` sind keine Seitenlabels.
- Eine nicht sicher lesbare Seitenzahl bleibt leer. Niemals aus Uploadreihenfolge oder Kontext ableiten.
- Abschnittswechsel innerhalb eines Fotos müssen erkannt werden. Für jede Karte die passende Hierarchie ausgeben oder Unsicherheit markieren.
- Die KI kann in einer Vorschau neue/ vorhandene Zielstruktur vorschlagen, aber der Nutzer entscheidet das Mapping vor dem Schreiben.

## Kurskontext

- Sprache: Kurslabels steuern Front/Back; links/rechts auf dem Foto bestimmt die Richtung nicht automatisch.
- Wissen: Inhalte bleiben im jeweiligen Sprachkontext und werden nicht automatisch übersetzt.
- Kategorien müssen einem Zuno-Code entsprechen: `noun`, `verb`, `adjective`, `adverb`, `pronoun`, `determiner`, `preposition`, `conjunction`, `interjection`, `numeral`, `particle`, `auxiliary`, `phrase`, `idiom`, `phrasal_verb`, `collocation`, `fixed_expression`, `sentence`. Bei Unsicherheit leer lassen.
