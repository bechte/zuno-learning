# Claude

Claude-Clients können den Zuno-MCP als Remote-Server verbinden. Je nach Claude-Produkt unterscheiden sich Einrichtung, OAuth-Unterstützung und Skills-Import.

1. In Claude die MCP-/Connector-Einstellungen öffnen und einen Remote-MCP-Server hinzufügen.
2. Serveradresse verwenden: `https://api.zuno.cards/mcp/zuno`.
3. OAuth starten, mit dem Zuno-Konto anmelden und die Zustimmung in Zuno erteilen.
4. Die Skills aus `skills/` separat installieren/importieren, sofern der genutzte Claude-Client Skills unterstützt.

Für Claude Code kann der MCP alternativ über dessen MCP-Einrichtung hinzugefügt und die Skill-Verzeichnisse in den verfügbaren Skills-Ordner kopiert werden. Zugangstokens gehören ausschließlich in den OAuth-Flow des Clients, niemals in dieses Repository.

Die Verfügbarkeit der Remote-Connectoren und Skills richtet sich nach Claude-Produkt, Version, Tarif und Workspace. Diese Anleitung muss vor Veröffentlichung mit den aktuellen Claude-Importwegen getestet werden.
