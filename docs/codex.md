# Codex

## Codex CLI

Repository-Marketplace hinzufügen:

```sh
codex plugin marketplace add bechte/zuno-learning --ref main
```

Danach im Codex CLI `/plugins` öffnen, `Zuno` suchen und installieren. Für die erste Verwendung einen neuen Chat starten und beim Verbinden die OAuth-Anmeldung für das Zuno-Konto abschließen.

## Codex Desktop

Das Repository als Marketplace-Quelle im Plugins-Verzeichnis auswählen. Der Marketplace-Eintrag liegt unter `.agents/plugins/marketplace.json`; dessen Plugin-Quelle zeigt auf das Repository-Stammverzeichnis. Danach `Zuno` installieren und bei der ersten Verbindung OAuth abschließen.

## Verwendete Dateien

- `.agents/plugins/marketplace.json` listet das Plugin für den Repository-Marketplace.
- `plugin.json` enthält die portable Plugin-Identität und OpenAI-spezifische Oberfläche.
- `mcp.json` deklariert den Zuno-MCP-Server unter `https://api.zuno.cards/mcp/zuno` mit Streamable HTTP und OAuth/CIMD.
- Die gemeinsamen Skills liegen in `skills/`.

Die Befehle und verfügbaren Installationswege können sich zwischen Codex CLI und Desktop unterscheiden. Für Git-Marktplätze nennt die [OpenAI-Paketdokumentation](https://developers.openai.com/plugins/build/plugins) `codex plugin marketplace add`; installiert und getestet wird das Plugin im Plugin-Verzeichnis.
