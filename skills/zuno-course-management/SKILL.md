---
name: zuno-course-management
description: Use when the user wants to inspect, create, organize, edit, activate, or delete their Zuno courses, lessons, sections, pages, or cards using the Zuno MCP tools.
---

# Zuno-Kurse verwalten

Nutze die Zuno-MCP-Werkzeuge für Daten und Änderungen. Erfinde keine IDs oder Strukturzuordnungen.

## Ablauf

1. Kläre das Ziel, falls Kurs oder Bereich nicht eindeutig ist. Rufe `get_all_courses` oder `get_active_courses` auf; für Details `get_course_information`.
2. Beim Erstellen einer Hierarchie immer schrittweise vorgehen: Kurs anlegen, zurückgegebene Kurs-ID verwenden, Lektion anlegen, zurückgegebene Lektions-ID verwenden, danach Sektion und anschließend Karten.
3. Beim Ändern oder Löschen vorhandene IDs aus Zuno verwenden. Bevor ein ganzer Kurs, eine Lektion, Sektion, Seite oder Kartenmenge gelöscht wird, zeige den betroffenen Umfang und hole die Bestätigung des Nutzers ein.
4. Für Kartenlisten `get_cards` mit Pagination verwenden; maximal 50 Karten pro Seite. Bei vollständiger Liste alle Seiten abrufen.
5. Für das Aktivieren genau die beabsichtigte Hierarchieebene mit dem passenden `set_*_activation` Werkzeug benennen. Der Erfolg der Aktivierung gibt nicht automatisch den neuen Strukturstatus zurück; bei Bedarf Struktur erneut abrufen.

## Berechtigungen und Profil

- Zunos Berechtigungen und die globalen MCP-Schalter gelten immer; bei einem Berechtigungsfehler nicht wiederholt versuchen.
- Ohne `profile_id` ist der Hauptaccount gemeint. Eine `profile_id` nur bei Profilabfragen, Lernen und Aktivierung verwenden, wo das Werkzeug sie unterstützt.
- Profilkontext bedeutet nicht, dass Kursinhalte im Namen des Profils bearbeitet werden dürfen.
- MCP unterstützt keine Freigaben oder Änderungen von Sharing-Einstellungen.

## Sammelanlage

Vor dem Anlegen bestehende Karten im passenden Bereich prüfen, damit der Nutzer mögliche Duplikate sieht. Zuno dedupliziert nicht. Karten stapelweise mit höchstens 2.000 Karten pro Aufruf anlegen. Für einen vollständigen Import `allow_partial=false` verwenden; Fehler korrigieren und den vollständigen Stapel erneut senden. Wiederholungen können Duplikate erzeugen.

Lernkarten aus Fotos und die optionale KI-Vervollständigung folgen den spezialisierten Skills.
