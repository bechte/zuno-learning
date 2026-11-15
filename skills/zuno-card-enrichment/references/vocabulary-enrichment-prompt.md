# Zuno-Vervollständigungsprompt

Quelle: `backend/app/Content/AiPromptCatalog.php::vocabularyEnrichment`. Diese portable Fassung hält die fachlichen Anweisungen der Serverversion fest. Bei Änderungen muss sie synchronisiert werden; siehe [Prompt-Synchronisierung](../../../docs/prompt-sync.md).

Verwende diesen Prompt zusammen mit einem JSON-Array `cards`. Jeder Eingabeeintrag enthält `id`, `front`, `back`, `category_code`, `missing_fields` sowie bereits gespeicherte optionale Werte. Kurskontext enthält Inhaltstyp, Front-Label und Back-Label.

## Prompt

Du ergänzt Lernkarten. Verarbeite jede Karte anhand ihrer stabilen ID. Ergänze ausschließlich Felder aus `missing_fields`. Bereits vorhandene Werte dürfen niemals verändert werden.

{KONTEXT: Bei Inhaltstyp Sprache sind Front ({FRONT_LABEL}) und Back ({BACK_LABEL}) unterschiedliche Sprachen. Beispielsätze müssen bei Ergänzungen sinngemäß zwischen diesen Sprachen übersetzt werden. Bei Inhaltstyp Wissen sind Front und Back keine Übersetzungsseiten. Beispielsätze bleiben in ihrer vorhandenen Sprache und werden nur passend zum jeweiligen Inhalt formuliert.}

`category_code` muss genau einer dieser Werte sein: `noun`, `verb`, `adjective`, `adverb`, `pronoun`, `determiner`, `preposition`, `conjunction`, `interjection`, `numeral`, `particle`, `auxiliary`, `phrase`, `idiom`, `phrasal_verb`, `collocation`, `fixed_expression` oder `sentence`. Wenn die Quelle „Phrase“ sagt, verwende `phrase` oder die passendere Ausdruckskategorie.

Wenn `category_code` bereits `sentence` ist oder du die Karte als `sentence` klassifizierst, liefere weder `front_sample`, `back_sample`, `front_pronunciation`, `back_pronunciation`, `front_reading` noch `back_reading`; lasse diese Felder weg, weil die Lernkarte selbst der Satz ist.

Eine Lesefassung ist der natürlich gesprochene, aber inhaltlich exakt äquivalente Text für Text-to-Speech. Löse nur eindeutige Buchnotationen und verbreitete Abkürzungen der jeweiligen Sprache auf, zum Beispiel `sth.`/`sb.` zu `something`/`somebody` oder `etw.`/`jn.` zu `etwas`/`jemanden`. Erhalte alle ausdrücklich angegebenen Alternativen; erfinde keine Bedeutungen. Wenn keine Auflösung nötig ist, entspricht die Lesefassung exakt dem Karteninhalt.

Beispielsätze müssen den Lernkern betonen und bei getrennten Verwendungen kurze Beispiele für die jeweiligen Alternativen liefern. Wenn nur eine Beispielsatzseite einer anderen Kategorie fehlt, formuliere einen kurzen, natürlichen Satz im passenden Kontext.

Die IPA folgt immer ausschließlich dem sichtbaren Karteninhalt: Sie darf eindeutige Abkürzungen wie `sth.`, `sb.`, `etw.` oder `jn.` ausschreiben, aber niemals eine zur Erklärung ergänzte Verknüpfung wie `or` oder `oder` enthalten. Sie darf keine weiteren Wörter, Bedeutungen oder Beispiele hinzufügen. Wenn das nicht sicher möglich ist, lasse die IPA weg. Verwende für die Lautschrift niemals `front_sample` oder `back_sample`. Liefere Aussprache ausschließlich als IPA zwischen Schrägstrichen.

Antworte ausschließlich als gültiges JSON-Objekt mit einem `cards`-Array und den angegebenen Karten-IDs. Jedes Ergebnis enthält `id` und nur neu erzeugte erlaubte Felder. Füge keine bestehenden, unveränderten Felder oder zusätzliche Erklärungen hinzu.
