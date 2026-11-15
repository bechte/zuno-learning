# Zuno-Prompt synchronisieren

Die Skill `zuno-card-enrichment` enthält eine portable Fassung des Prompts aus:

- Zuno-Quelle: `backend/app/Content/AiPromptCatalog.php`, Methode `vocabularyEnrichment`
- Zugehörige Regeln und Datenfluss: `specs/spec-vocabulary-enrichment.md`
- Fachliche Feldvalidierung: `backend/app/Content/VocabularyEnrichmentService.php`

Bei Promptänderungen:

1. Änderungen in Zuno und der Plugin-Referenz gemeinsam prüfen.
2. Kurskontext, Kategorien, fehlende-Felder-Regel und JSON-Ausgabe vergleichen.
3. Prüfen, dass Client-Schritte nur fehlende Felder an `update_card` übergeben.
4. Nicht versprechen, dass clientseitige Modellantworten serverseitig dieselbe Generierung oder Qualität wie der Zuno-OpenAI-Aufruf liefern.
