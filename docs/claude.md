# Claude

Das Repository enthält ein Claude-kompatibles Marketplace-Manifest unter `.claude-plugin/marketplace.json`. Es kann direkt aus GitHub als Marketplace registriert werden; ein ZIP ist dafür nicht nötig.

## Claude App / Claude Desktop

1. **Customize → Plugins → Add → Add marketplace** öffnen.
2. **Add from a repository** wählen und `bechte/zuno-learning` eingeben.
3. Das Marketplace-Verzeichnis synchronisieren und **Zuno Learning** installieren.
4. Beim Verbinden OAuth starten, mit dem Zuno-Konto anmelden und die Zustimmung erteilen.
5. Den Connector/Plugin im Chat aktivieren.

## Claude Code

Im CLI kann die Quelle und das Plugin direkt hinzugefügt werden:

```text
/plugin marketplace add bechte/zuno-learning
/plugin install zuno-learning@zuno
```

Nach der Installation OAuth über den MCP-Login abschließen. Skills und MCP-Konfiguration werden gemeinsam vom Plugin geladen.

Für Team- und Enterprise-Organisationen kann ein Administrator eine Marketplace-Quelle einschränken oder zentral bereitstellen. Der OAuth-Zugriff bleibt benutzerspezifisch.
