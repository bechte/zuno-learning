# ChatGPT

## ChatGPT im Workspace

Ein Workspace-Administrator kann das Repository unter **Admin Console → Plugins → Add → Import marketplace** als Marketplace-Quelle hinzufügen. Repository `https://github.com/bechte/zuno-learning`, Branch `main` und den Plugin-Pfad leer lassen, damit die Marketplace-Datei im Repository-Stamm verwendet wird. Danach das Plugin sowie die Installationsrichtlinie prüfen. Der Import ist eine Workspace-Funktion und kann je nach ChatGPT-Plan und Organisationsrichtlinie verfügbar sein.

## Verwendete Dateien

- `.agents/plugins/marketplace.json` listet das Plugin für den Repository-Marketplace.
- `plugin.json` enthält die portable Plugin-Identität und OpenAI-Oberflächenmetadaten.
- `mcp.json` verbindet sich per Streamable HTTP mit `https://api.zuno.cards/mcp/zuno`. Der aktuelle ChatGPT/Codex-Desktop-Loader verwirft den dokumentierten OpenAI-OAuth-Erweiterungsblock in dieser Datei; der Workaround lässt den Host OAuth anhand der Server-Challenge beim ersten Toolaufruf starten. Siehe [Loader-Fehler #53658](https://github.com/openai/codex/issues/53658).
- Die gemeinsamen Skills liegen in `skills/`.

Der GitHub-Import verbindet nicht automatisch ein Zuno-Konto. Jeder Nutzer muss beim ersten Toolaufruf den OAuth-Dialog abschließen. Der Desktop-Workaround wurde nicht live gegen Zuno verifiziert.

## ZIP-Verteilung

Ein GitHub-Release-ZIP ist für Upload oder manuelle Verteilung gedacht. Für einen Workspace Marketplace-Import wird es nicht benötigt.
