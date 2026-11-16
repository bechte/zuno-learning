# Zuno Learning

Zuno Learning verbindet ChatGPT, Codex und Claude Code mit dem bestehenden Zuno-MCP-Server und ergänzt die Verbindung um gemeinsame Skills für Lernkartenabläufe.

## Funktionen

- Kurse, Lektionen, Sektionen, Seiten und Karten mit Zuno verwalten.
- Lernkarten aus Fotos vorbereiten und nach Vorschau sowie Freigabe anlegen.
- Fehlende Kartenfelder nach Zunos Vervollständigungsregeln ergänzen.

Der MCP-Server wird von Zuno betrieben und ist nicht Bestandteil dieses Repositories. Für den Zugriff sind ein Zuno-Konto, aktivierter MCP-Zugriff und die OAuth-Zustimmung erforderlich. Das Repository enthält keine API-Schlüssel.

## Einstieg nach Client

- [ChatGPT](docs/chatgpt.md): Workspace Marketplace und Installation.
- [Codex](docs/codex.md): Repository-Marketplace über Codex CLI und Plugin-Verzeichnis.
- [Claude Code](docs/claude.md): Claude Marketplace und OAuth-Verbindung.

## Aufbau

Die drei Skills unter `skills/` sind gemeinsam und werden von den unterstützten Clients geladen. Die Clients verwenden unterschiedliche Marketplace-, Manifest- und MCP-Dateien:

| Client | Einstieg und Konfiguration |
| --- | --- |
| ChatGPT / Codex | `.agents/plugins/marketplace.json`, `plugin.json`, `mcp.json` |
| Claude Code | `.claude-plugin/marketplace.json`, `.claude-plugin/plugin.json`, `.mcp.json` |

Alle MCP-Dateien liegen am Plugin-Stamm. `mcp.json` enthält den Streamable-HTTP-Endpunkt für OpenAI-Clients. Der OpenAI-Desktop-Loader verwirft derzeit den dokumentierten OAuth-Erweiterungsblock; daher wird OAuth über die Server-Challenge beim ersten Toolaufruf gestartet. `.mcp.json` nutzt Claudes MCP-Format und denselben Endpunkt. Die Dateiformate sind client-spezifisch und nicht austauschbar.

## Releases

Ein Push eines Tags im Format `vMAJOR.MINOR.PATCH` startet `.github/workflows/release.yml`. Der Workflow prüft die Versionsangaben in den vier Plugin- und Marketplace-Manifesten, erstellt ein ZIP mit den Plugin-Manifests, MCP-Konfigurationen und Skills und hängt ZIP sowie SHA-256-Prüfsumme an das GitHub Release an. Vor dem Tag müssen die Versionsangaben in `plugin.json`, `.claude-plugin/plugin.json` und den beiden Marketplace-Manifesten zur Tag-Version passen.

Das ZIP ist für direkten Upload oder manuelle Verteilung gedacht. Die Marketplace-Installation bezieht die Dateien direkt aus dem Repository.

## Pflege der Zuno-Prompts

Die portable Referenz des Vervollständigungsprompts basiert auf Zunos `AiPromptCatalog::vocabularyEnrichment`. Bei Promptänderungen die Kopie synchronisieren; siehe [Prompt-Synchronisierung](docs/prompt-sync.md).
