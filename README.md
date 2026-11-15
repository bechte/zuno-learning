# Zuno AI Plugin

Dieses Projekt bündelt die Verbindung zum bestehenden Zuno-MCP-Server und portable Skills für wiederkehrende Lernkartenabläufe.

## Enthalten

- `mcp.json`: Verbindung zum Remote-MCP unter `https://api.zuno.cards/mcp/zuno` mit OAuth.
- `skills/zuno-course-management`: Kurse, Lektionen, Sektionen, Seiten und Karten verwalten.
- `skills/zuno-photo-to-cards`: Fotos mit dem Bildmodell des jeweiligen KI-Clients auswerten und Karten über Zuno anlegen.
- `skills/zuno-card-enrichment`: Zunos KI-Vervollständigungsprompt clientseitig anwenden und fehlende Felder über MCP ergänzen.

Der MCP-Server selbst wird von Zuno betrieben und ist nicht Bestandteil dieses Pakets. Die Einrichtung in Zuno erfordert ein Konto, aktivierten MCP-Zugriff und die OAuth-Zustimmung. Das Paket enthält keine API-Schlüssel.

## Clients

- **ChatGPT:** Plugin-Paket mit Skills und MCP-Verbindung verwenden, sofern der Account die Installation benutzerdefinierter MCP-Plugins unterstützt.
- **Claude:** Zuno als Remote-MCP-Connector mit OAuth verbinden. Skills abhängig vom verwendeten Claude-Client separat als Skills installieren/importieren; siehe [Claude](docs/claude.md).
- **Codex / Claude Code:** Die SKILL.md-Dateien folgen dem portablen Agent-Skills-Format. MCP-Verbindung separat konfigurieren, sofern die Plugin-Installation sie nicht übernimmt.

MCP- und Skill-Unterstützung hängt vom jeweiligen Client, Tarif und Workspace ab. Die Client-Anleitungen sind deshalb keine Garantie, dass eine einzige Installationsdatei überall identisch importiert werden kann.

## Prompt-Pflege

Die Prompt-Ressource zur Vervollständigung wurde aus Zunos `AiPromptCatalog::vocabularyEnrichment` abgeleitet. Bei Änderungen am Zuno-Prompt muss die Plugin-Kopie synchronisiert werden. Siehe [Prompt-Synchronisierung](docs/prompt-sync.md).

## Status

Frühe, lokal vorbereitete Projektversion. Die Manifeststruktur und Skills müssen vor Veröffentlichung mit den aktuellen Importwegen und realen Clientkonten geprüft werden. Die öffentliche MCP-Verbindung wurde bei dieser Vorbereitung nicht live getestet.
