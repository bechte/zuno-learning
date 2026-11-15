# Zuno-MCP-Werkzeuge

Die Verbindung verwendet den bestehenden Remote-MCP. Die aktuelle Werkzeugliste und Eingabeschemas kommen zur Laufzeit von Zuno; diese Datei ist nur eine workflow-orientierte Kurzreferenz.

Kurs- und Kartenverwaltung: `get_learning_profiles`, `get_active_courses`, `get_all_courses`, `get_course_information`, `get_cards`, `create_course`, `update_course`, `delete_course`, Hierarchiewerkzeuge sowie Kartenwerkzeuge.

Lernen: `get_cards_for_learning` gibt einen einzelnen Lernschwung zurück. Nach Abschluss sendet der Client alle beantworteten Karten zusammen mit genau einem Aufruf von `submit_learning_results`; übersprungene Karten werden ausgelassen. Wiederholtes Senden zählt als erneutes Lernen.

Kartenanlage: `create_cards` nimmt maximal 2.000 Karten und verlangt `allow_partial`. Für vollständige Importe verwenden die Skills `allow_partial=false`. Bei Fehlern den ganzen Stapel korrigieren, bevor erneut gesendet wird. Der Server dedupliziert nicht.

Details und Berechtigungen richten sich nach der aktuellen Zuno-MCP-Spezifikation; diese Entwicklungsreferenz wird nicht in die installierte Plugin-Runtime kopiert.
