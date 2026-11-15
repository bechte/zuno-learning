# ChatGPT und Codex

Das Repository enthält `.agents/plugins/marketplace.json`. Ein GitHub-Workspace-Marketplace-Import benötigt kein ZIP; GitHub liefert das Plugin direkt aus dem Repository und kann es regelmäßig synchronisieren.

## ChatGPT-Workspace

Ein Workspace-Administrator kann unter **Admin Console → Plugins → Add → Import marketplace** das Repository `https://github.com/bechte/zuno-learning` importieren. Den Pfad leer lassen und als Branch `main` auswählen. Danach das Plugin und die Workspace-Installationsrichtlinie prüfen. Die Verbindung autorisiert nicht automatisch Zuno-Konten; jeder Nutzer meldet sich per OAuth bei Zuno an.

## ChatGPT Desktop / Codex

In unterstützten Desktop-/Codex-Umgebungen kann das GitHub-Repository als Marketplace-Quelle hinzugefügt werden:

```sh
codex plugin marketplace add bechte/zuno-learning
```

Anschließend das Plugin im Plugin-Verzeichnis installieren. OAuth verbindet den Nutzer mit Zuno.

## ZIP-Veröffentlichung

Ein Release-ZIP ist eine Alternative für Upload oder manuelle Verteilung, aber nicht nötig, wenn der Workspace Marketplace direkt aus GitHub importiert wird. Der Import von GitHub-Marketplaces ist eine Workspace-Admin-Funktion. Die verfügbaren Schreibaktionen hängen außerdem von ChatGPT-Plan und Workspace-Berechtigungen ab.
