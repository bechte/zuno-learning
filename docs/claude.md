# Claude Code

## Marketplace hinzufügen

Im Claude Code CLI oder in einer Claude Code-Sitzung:

```text
/plugin marketplace add bechte/zuno-learning
/plugin install zuno-learning@zuno
```

Nach der Installation ein neues Claude-Code-Fenster oder eine neue Sitzung starten. Beim ersten Verbinden im MCP-Bereich OAuth für das Zuno-Konto abschließen. Claude Code verwaltet den OAuth-Ablauf anhand der Metadaten des Remote-MCP-Servers.

## Verwendete Dateien

- `.claude-plugin/marketplace.json` registriert den GitHub-Marktplatz und verweist auf das Plugin im Repository-Stamm.
- `.claude-plugin/plugin.json` enthält die Claude-Code-Plugin-Metadaten.
- `.mcp.json` liegt im Plugin-Stammverzeichnis und verbindet sich per `streamable-http` mit `https://api.zuno.cards/mcp/zuno`. Claude Code akzeptiert `streamable-http` als Alias für `http`; OpenAI-spezifische OAuth-Erweiterungen gehören nicht in diese Datei.
- Die gemeinsamen Skills liegen in `skills/`.

Claude Code kann die Plugin-Konfiguration mit `claude plugin validate .` prüfen. Danach `/plugin` öffnen und unter MCP kontrollieren, ob `zuno` verbunden ist. Eine erfolgreiche Anmeldung in Claude Code bestätigt nicht automatisch den Import in ChatGPT oder Codex; diese Clients haben eigene Marketplace- und MCP-Dateien.

Für Claude.ai und Cowork können sich Marketplace-Import und unterstützte Plugin-Komponenten vom Claude-Code-Ablauf unterscheiden.
