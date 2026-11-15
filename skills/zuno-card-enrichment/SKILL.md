---
name: zuno-card-enrichment
description: Use when the user wants Zuno's AI completion behavior applied to existing cards, or after importing photo-based cards with the user's approval.
---

# Zuno-Karten vervollständigen

Diese Skill führt Zunos bestehenden Vervollständigungsprompt mit dem Modell des aktuellen KI-Clients aus und speichert die erzeugten fehlenden Felder über Zuno-MCP. Sie ruft Zunos serverseitige KI nicht auf und benötigt keinen Zuno/OpenAI-Schlüssel.

## Einwilligung

Wenn dieser Schritt nach einem Fotoimport vorgeschlagen wird, frage: „Soll ich die neuen Karten mit Zunos KI-Vervollständigungsregeln ergänzen? Ja (empfohlen) / Nein“. Ja ist die vorausgewählte Empfehlung; führe die Generierung und Änderungen erst nach ausdrücklicher Zustimmung aus. Bei bestehenden Karten ebenfalls vor der ersten Änderung fragen.

## Ablauf

1. Hole die Karten aus dem vom Nutzer genannten Kurs und Bereich mit `get_cards`; verwende Pagination und frage nie mehr als 50 Karten pro Seite ab.
2. Wähle nur tatsächlich fehlende, anwendbare Felder. Unterstützt werden `category_code`, `front_reading`, `back_reading`, `front_sample`, `back_sample`, `front_pronunciation` und `back_pronunciation`.
3. Übergib dem Modell Kartendaten mit stabiler `card_id`, Kursinhaltstyp und Front-/Back-Labels. Lade den Prompt aus [Zunos Vervollständigungsprompt](references/vocabulary-enrichment-prompt.md) und beachte ihn genau. Jeder Feldwert soll nur erzeugt werden, wenn er fehlt.
4. Prüfe die Antwort: bekannte Karten-IDs, zulässige Feldnamen, Strings, Zuno-Kategoriecodes, passende Sprache und keine nicht angeforderten Felder. Sätze dürfen keine erfundenen Fakten einführen.
5. Zeige die vorgeschlagenen Ergänzungen vor dem Speichern als Vorschau. Übernimm nur nach Zustimmung.
6. Verwende `update_card` mit der Karten-ID und ausschließlich den weiterhin leeren Feldern. Nie vorhandene Werte überschreiben. Wenn mehrere Karten bearbeitet werden, einzeln oder in überschaubaren Gruppen aktualisieren; bei einem Fehler bestehende Karten nicht unbemerkt als vollständig melden.
7. Berichte, welche Karten ergänzt wurden und welche Felder fehlgeschlagen oder bewusst leer gelassen wurden.

## Grenzen

- Diese Funktion ergänzt fehlende Felder; sie schreibt vorhandene Vorder- und Rückseiten nicht um.
- Text-to-Speech oder Audioerzeugung wird nicht ausgelöst.
- Der Client kann Zunos identische Generierung nicht garantieren. Modell, Bild-/Textverarbeitung und Antwortqualität hängen vom jeweiligen Client ab.
- Kategorien `sentence` erhalten keine Beispiele, Aussprache oder Lesefassungen.
